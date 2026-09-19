# Azure Windows Diagnostic Automation with GitHub Actions, Microsoft Entra OIDC, and Azure RBAC

## Overview

This lab demonstrates a passwordless cloud-automation workflow that uses GitHub Actions to authenticate to Microsoft Azure through Microsoft Entra ID using OpenID Connect (OIDC), start an Azure Windows Server virtual machine, execute a PowerShell-based diagnostic toolkit remotely with Azure VM Run Command, persist the generated HTML report on the VM, and then deallocate the VM to reduce unnecessary compute cost.

The completed workflow validates practical experience across cloud administration, identity, automation, Windows Server, PowerShell, CI/CD, RBAC, and secure workload authentication.

**Dedicated project repository:**  
https://github.com/johninfra/azure-windows-diagnostic-automation-workflow

---

## Architecture

~~~text
GitHub Repository
        |
        v
GitHub Actions
        |
        | OIDC token
        v
Microsoft Entra ID
        |
        | Federated workload identity
        v
GitHub-Windows-Diagnostic-Toolkit
        |
        | Azure RBAC
        v
rg-azure-enterprise-lab
        |
        v
Azure Windows VM: vm-win01
        |
        | Azure VM Run Command
        v
PowerShell Diagnostic Toolkit
        |
        v
C:\DiagnosticReports\IT-Diagnostic-<timestamp>.html
        |
        v
VM deallocated after execution
~~~

No Azure client secret is stored in GitHub. Authentication is performed with GitHub-issued OIDC tokens that Microsoft Entra ID validates against the configured federated credential.

---

## Lab Environment

| Component | Technology |
|---|---|
| Cloud Platform | Microsoft Azure |
| Identity Platform | Microsoft Entra ID |
| CI/CD / Automation | GitHub Actions |
| Workload Authentication | OpenID Connect (OIDC) federation |
| Authorization | Azure Role-Based Access Control (RBAC) |
| Azure Compute | Windows Server 2022 Azure VM |
| VM | vm-win01 |
| Resource Group | rg-azure-enterprise-lab |
| Remote Execution | Azure VM Run Command |
| Command-Line Interface | Azure CLI |
| Automation Language | PowerShell |
| Reporting | HTML diagnostic report |
| Source Control | GitHub |

---

## Objectives

1. Register a Microsoft Entra application for GitHub workload authentication.
2. Create a federated credential tied to the GitHub repository and main branch.
3. Avoid long-lived Azure client secrets by using OIDC.
4. Assign Azure RBAC at the resource-group scope instead of the subscription scope.
5. Configure GitHub Actions with the Azure client, tenant, and subscription identifiers.
6. Authenticate GitHub Actions to Azure using azure/login.
7. Start an Azure Windows VM automatically.
8. Execute a PowerShell diagnostic toolkit remotely with Azure VM Run Command.
9. Generate a persistent HTML system-health report.
10. Deallocate the VM after diagnostics to limit unnecessary compute usage.
11. Validate the report through an RDP session.

---

# 1. Microsoft Entra Application Registration

A dedicated Microsoft Entra application was created for the automation workflow:

~~~text
GitHub-Windows-Diagnostic-Toolkit
~~~

The application represents the GitHub workload inside Microsoft Entra ID.

Instead of creating a client secret, the application uses a federated identity credential.

This reduces the risk associated with storing and rotating long-lived application credentials.

---

# 2. GitHub OIDC Federated Credential

A federated credential was created for the GitHub repository and the main branch.

The trust relationship allows Microsoft Entra ID to validate OIDC tokens issued by GitHub Actions only when the token matches the expected repository identity and branch.

Conceptually:

~~~text
GitHub Actions
     |
     | short-lived OIDC token
     v
Microsoft Entra ID
     |
     | validate repository + branch claims
     v
Azure access token
~~~

This is a workload-identity pattern rather than a user-password authentication flow.

---

# 3. Azure RBAC and Least Privilege

The Microsoft Entra service principal was assigned the Azure role required to manage the lab VM.

The role assignment was scoped to:

~~~text
rg-azure-enterprise-lab
~~~

rather than the entire Azure subscription.

This demonstrates the principle of least privilege by limiting the workload identity to the resource group used by the lab.

The workflow requires VM-management permissions because it must:

- start the Windows VM
- invoke Azure VM Run Command
- deallocate the VM after the diagnostic run

---

# 4. GitHub Actions Repository Secrets

The workflow references three GitHub Actions repository secrets:

~~~text
AZURE_CLIENT_ID
AZURE_TENANT_ID
AZURE_SUBSCRIPTION_ID
~~~

These values identify the Microsoft Entra application, tenant, and Azure subscription.

No Azure client secret is required because authentication is handled through OIDC federation.

The workflow grants the GitHub job permission to request an OIDC token:

~~~yaml
permissions:
  id-token: write
  contents: read
~~~

The id-token permission allows the workflow to request a GitHub OIDC token. Azure authorization is still enforced independently through Microsoft Entra ID and Azure RBAC.

---

# 5. GitHub Actions Workflow

The automation workflow performs five primary stages:

~~~yaml
name: Azure Windows Diagnostic Toolkit

on:
  workflow_dispatch:

permissions:
  id-token: write
  contents: read

jobs:
  diagnostics:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout repository
        uses: actions/checkout@v4

      - name: Login to Azure with OIDC
        id: azure-login
        uses: azure/login@v2
        with:
          client-id: ${{ secrets.AZURE_CLIENT_ID }}
          tenant-id: ${{ secrets.AZURE_TENANT_ID }}
          subscription-id: ${{ secrets.AZURE_SUBSCRIPTION_ID }}

      - name: Start Windows VM
        run: |
          az vm start \
            --resource-group rg-azure-enterprise-lab \
            --name vm-win01

      - name: Run full Windows diagnostic toolkit
        run: |
          az vm run-command invoke \
            --resource-group rg-azure-enterprise-lab \
            --name vm-win01 \
            --command-id RunPowerShellScript \
            --scripts @it-diagnostics.ps1

      - name: Deallocate VM
        if: ${{ always() && steps.azure-login.outcome == 'success' }}
        run: |
          az vm deallocate \
            --resource-group rg-azure-enterprise-lab \
            --name vm-win01
~~~

This provides a manually triggered operational workflow from GitHub without requiring an administrator to start the VM or manually execute the PowerShell script.

---

# 6. Windows Diagnostic Toolkit

The PowerShell toolkit collects operational and security information from the Windows Server VM.

Diagnostic categories include:

- operating system information
- computer manufacturer and model
- processor information
- memory utilization
- disk capacity and free space
- IPv4 configuration
- default gateway and DNS configuration
- gateway connectivity
- internet connectivity
- DNS resolution
- Microsoft Defender status
- Windows Firewall status
- automatic services that are not running
- recent critical and error events
- administrator-session status

The toolkit generates an HTML report for review.

---

# 7. Persistent Report Location

During initial testing, the report was written relative to PowerShell's script directory:

~~~powershell
$reportFolder = Join-Path $PSScriptRoot "Reports"
~~~

When the script was executed through Azure VM Run Command, PSScriptRoot pointed to Azure's temporary Run Command plugin directory.

That made the report difficult to locate after the automation completed.

The report destination was changed to a predictable persistent directory:

~~~powershell
$reportFolder = "C:\DiagnosticReports"
~~~

The script creates the directory automatically when necessary and saves reports using a timestamped filename:

~~~text
C:\DiagnosticReports\IT-Diagnostic-YYYY-MM-DD_HH-MM-SS.html
~~~

This troubleshooting step demonstrates the difference between local script execution context and remote automation execution context.

---

# 8. Validation

The complete workflow was successfully executed through GitHub Actions.

The run validated that:

- GitHub successfully issued an OIDC token.
- Microsoft Entra ID accepted the federated workload identity.
- Azure login succeeded without a client secret.
- Azure RBAC permitted the workload identity to manage the lab VM.
- vm-win01 started automatically.
- Azure VM Run Command executed the PowerShell toolkit inside Windows Server.
- The diagnostic report was generated successfully.
- The VM was deallocated automatically after execution.
- The HTML report was opened and reviewed through an RDP session.

The report confirmed collection of Windows Server, CPU, memory, storage, network, connectivity, and endpoint-security information.

---

## Evidence Captured

Two screenshots were captured during validation:

1. **Windows IT Diagnostic Report** — verifies that the PowerShell toolkit executed on vm-win01 and generated the expected HTML report.
2. **Azure VM RDP connection configuration** — verifies the Azure-hosted Windows Server environment used for validation.

Sensitive or unnecessary identifiers such as public/source IP addresses, personal account identifiers, and login usernames should be redacted before public publication.

---

# 9. Security Considerations

This lab intentionally uses several security controls that mirror enterprise practices.

### Passwordless workload authentication

GitHub Actions authenticates to Microsoft Entra ID through OIDC rather than a stored Azure client secret.

### Least-privilege scope

The workload identity is authorized at the lab resource-group scope instead of receiving subscription-wide access.

### Secret handling

The GitHub workflow references repository secrets and does not hard-code environment identifiers directly into the public workflow where avoidable.

No passwords, access tokens, refresh tokens, MFA codes, private keys, or client secrets are included in the public documentation.

### Controlled remote administration

The automated workflow uses Azure VM Run Command rather than exposing a custom remote PowerShell endpoint.

### Cost control

The VM is deallocated automatically at the end of the workflow, including after most failures once Azure authentication has succeeded.

---

# 10. Troubleshooting Lessons

This lab required troubleshooting across multiple layers:

### OIDC trust

The GitHub repository and branch had to match the federated credential configured in Microsoft Entra ID.

### Azure RBAC

Authentication alone was not sufficient. The workload identity also required Azure authorization to start, manage, and execute commands against the VM.

### Remote execution context

Azure VM Run Command executes PowerShell from a plugin-managed working directory. This affected the original report path and required changing the report destination to a persistent location.

### VM lifecycle

The workflow had to handle a deallocated VM by starting it before diagnostics and returning it to a deallocated state afterward.

These are separate layers of the automation path:

~~~text
Authentication != Authorization != Execution
~~~

A successful implementation required all three layers to function correctly.

---

# Skills Demonstrated

- Microsoft Azure administration
- Azure Virtual Machines
- Microsoft Entra ID
- Workload identity federation
- OpenID Connect (OIDC)
- GitHub Actions
- CI/CD automation
- Azure Role-Based Access Control
- Least-privilege access design
- Azure CLI
- PowerShell automation
- Windows Server 2022 administration
- Azure VM Run Command
- Remote systems administration
- Windows endpoint diagnostics
- HTML reporting
- Cloud troubleshooting
- VM lifecycle automation
- Security-conscious credential management
- Cost-aware cloud operations

---

# Lab Outcome

The final solution provides an automated cloud-management workflow:

~~~text
Administrator
     |
     v
GitHub Actions - Run workflow
     |
     v
GitHub OIDC
     |
     v
Microsoft Entra ID
     |
     v
Azure RBAC
     |
     v
Start vm-win01
     |
     v
Run PowerShell diagnostics remotely
     |
     v
Generate C:\DiagnosticReports\IT-Diagnostic-*.html
     |
     v
Deallocate vm-win01
~~~

The lab demonstrates the ability to integrate source control, CI/CD automation, cloud identity, authorization, Azure infrastructure, Windows administration, and PowerShell into one secure operational workflow.

---

## Project Repository

**Azure Windows Diagnostic Automation Workflow**  
https://github.com/johninfra/azure-windows-diagnostic-automation-workflow
