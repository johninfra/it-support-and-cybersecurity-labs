# IT Support and Cybersecurity Lab Portfolio

## About This Repository

This repository contains **27 hands-on labs** spanning **IT support, systems administration, identity and access management (IAM), Microsoft Azure, cloud automation, networking, PowerShell, security operations, and cybersecurity**.

The labs are designed around practical enterprise workflows rather than isolated theory. They document how I configure, administer, secure, troubleshoot, automate, and validate Windows, Linux, Active Directory, Microsoft Entra ID, Azure, Splunk, networking, and endpoint-security environments.

The portfolio progresses from core help desk and infrastructure work into more advanced administration and automation, including **Microsoft Graph, Azure RBAC, GitHub Actions, OpenID Connect (OIDC) workload identity federation, Azure VM Run Command, PowerShell reporting, and cloud-based Windows administration**.

Each lab includes implementation details, commands, screenshots, troubleshooting notes, security considerations, and business or operational context where applicable.

---

## Core Competencies

### Identity & Access Management

- Microsoft Entra ID
- Active Directory
- User and group administration
- Identity lifecycle workflows
- Security groups
- Role-Based Access Control (RBAC)
- Microsoft Graph PowerShell
- Delegated OAuth permissions
- Workload identity federation
- OpenID Connect (OIDC)
- MFA and authentication support
- Privileged-role verification
- Least-privilege administration
- Password resets and account unlocks

### Microsoft Azure & Cloud Administration

- Azure Virtual Machines
- Azure resource groups
- Azure RBAC
- Microsoft Entra application registrations
- Enterprise applications
- Federated credentials
- Azure CLI
- Azure VM Run Command
- GitHub-to-Azure OIDC authentication
- VM lifecycle automation
- Cloud troubleshooting
- Cost-conscious VM deallocation
- Persistent diagnostic reporting

### Systems Administration

- Windows 10/11
- Windows Server 2022
- Linux administration
- PowerShell automation
- CIM/WMI
- Remote Desktop Protocol (RDP)
- SSH
- Windows services
- Event Viewer
- Endpoint administration
- File and share permissions
- Software deployment
- System health and diagnostic reporting

### Networking

- TCP/IP
- IPv4 configuration
- DNS
- DHCP
- VPN
- SMB
- Default gateway and routing validation
- Network connectivity troubleshooting
- Nmap
- Wireshark
- Port and service enumeration
- Packet capture and protocol analysis

### Security Operations

- Splunk Enterprise
- SIEM monitoring
- SPL
- Sysmon
- Windows Security Logs
- Windows Event Logs
- Microsoft Defender
- Windows Firewall
- Log analysis
- Incident investigation
- Threat detection
- Vulnerability and posture assessment
- Security monitoring and alerting

### IT Operations & Support

- Tier 1–2 troubleshooting workflows
- Help desk and service desk operations
- ITSM
- Ticket prioritization
- Incident documentation
- Escalation
- Remote support
- Identity and access support
- Printer and application troubleshooting
- Standard operating procedures
- Technical documentation

### Automation & DevOps

- PowerShell
- GitHub Actions
- CI/CD concepts
- Azure CLI
- OIDC-based cloud authentication
- Remote script execution
- Automated HTML reporting
- Repeatable administrative workflows
- Source-controlled infrastructure operations

---

## Labs Included

| Lab | Project | Skills Demonstrated |
|---:|---|---|
| 01 | [Network Reconnaissance and Service Enumeration](./Lab-01-Network-Reconnaissance/) | Nmap, host discovery, port scanning, service enumeration, network validation |
| 02 | [Linux System Operations and File Permission Management](./Lab-02-Linux-System-Operations-and-File-Permission-Management/) | Linux CLI, directory management, `sudo`, `chmod`, file permissions |
| 03 | [Windows Network Troubleshooting](./Lab-03-Network-Troubleshooting/) | TCP/IP, DHCP renewal, gateway identification, `ping`, `ipconfig`, `netsh` |
| 04 | [Active Directory Group-Based Access Control](./Lab-04-Active-Directory-Access-Control/) | Active Directory, security groups, NTFS permissions, share permissions, least privilege |
| 05 | [Network Drive Mapping and File Sharing](./Lab-05-Network-Drive-Mapping-and-File-Sharing/) | SMB, UNC paths, shared folders, network drive mapping, access troubleshooting |
| 06 | [Active Directory User and Group Management](./Lab-06-Active-Directory-User-and-Group-Management/) | User provisioning, security groups, group membership, access validation |
| 07 | [Remote IT Support Simulation](./Lab-07-Remote-IT-Support-Simulation/) | RDP, AnyDesk, remote troubleshooting, network adapter recovery, user support |
| 08 | [DNS and Network Connectivity Troubleshooting](./Lab-08-DNS-and-Network-Connectivity-Troubleshooting/) | DNS resolution, `nslookup`, `ping`, `tracert`, IP configuration analysis |
| 09 | [Password Reset and Account Lockout Support](./Lab-09-Password-Reset-and-Account-Lockout-Support/) | ADUC, password resets, account unlocks, identity verification, login validation |
| 10 | [Software Installation and Printer Troubleshooting](./Lab-10-Software-Installation-and-Printer-Troubleshooting/) | Software deployment, application validation, printer configuration, test printing |
| 11 | [Windows Troubleshooting and Printer Support](./Lab-11-Windows-Troubleshooting-Ticket/) | Windows services, Print Spooler, print queues, structured ticket resolution |
| 12 | [Network Traffic Analysis and Security Monitoring](./Lab-12-Network-Traffic-Analysis-and-Security-Monitoring-with-Nmap-Wireshark-and-Splunk/) | Nmap, Wireshark, Splunk, packet capture, protocol filtering, log analysis |
| 13 | [Help Desk Ticket Workflow Simulation](./Lab-13-Help-Desk-Ticket-Workflow-Simulation/) | Ticket prioritization, troubleshooting, documentation, escalation, resolution verification |
| 14 | [Active Directory Password Reset and Ticket Resolution](./Lab-14-Active-Directory-Password-Reset-and-Ticket-Resolution/) | Active Directory support, password management, ticket documentation, issue closure |
| 15 | [Help Desk Ticketing and Cybersecurity Operations Web Application](./Lab-15-Help-Desk-Ticketing-and-Cybersecurity-Operations-Web-Application/) | ITSM workflows, ticket management, user and asset relationships, security-alert simulation |
| 16 | [Windows Host Port Scanning with Metasploit](./Lab-16-Windows-Host-Port-Scanning-With-Metasploit/) | Metasploit, TCP port scanning, host discovery, service identification, exposure assessment |
| 17 | [SMB Fingerprinting and Security Enumeration](./Lab-17-SMB-Fingerprinting-and-Security-Enumeration/) | SMB enumeration, protocol identification, host fingerprinting, security configuration analysis |
| 18 | [Splunk SIEM Security Monitoring and Alerting Platform](./Lab-18-Splunk-SIEM-Security-Monitoring-and-Alerting-Platform/) | Splunk deployment, log ingestion, SPL, dashboards, real-time alerts, reconnaissance detection |
| 19 | [Splunk SOC Security Monitoring Dashboard](./Lab-19-Splunk-SOC-Security-Monitoring-Dashboard/) | Windows Security Logs, Sysmon, authentication monitoring, process analysis, threat detection |
| 20 | [Configuring and Troubleshooting RDP on Windows Server 2022](./Lab-20-Configuring-and-Troubleshooting-Remote-Desktop-Protocol-on-Windows-Server-2022/) | Windows Server, RDP, TCP/UDP 3389, firewall rules, remote-access troubleshooting |
| 21 | [PowerShell Windows Health Check Automation](./Lab-21-PowerShell-Windows-Health-Check-Automation/) | PowerShell, CIM/WMI, CPU and memory monitoring, disk analysis, system reporting |
| 22 | [PowerShell Vulnerability Management and Security Audit Framework](./Lab-22-PowerShell-Vulnerability-Management-and-Security-Audit-Framework/) | Endpoint inventory, security-control assessment, service analysis, risk reporting |
| 23 | [Microsoft Entra ID Fundamentals](./Lab-23-Microsoft-EntraID-Fundamentals/) | Entra tenant administration, cloud user provisioning, security groups, identity administration |
| 24 | [PowerShell Security Awareness and Endpoint Posture Dashboard](./Lab-24-PowerShell-Security-Awareness-Dashboard/) | PowerShell automation, Defender, Windows Event Logs, WMI/CIM, security auditing, HTML reporting |
| 25 | [Linux Web Infrastructure and Security Configuration](./Lab-25-Linux-Web-Infrastructure-and-Security-Configuration/) | Ubuntu administration, SSH, Nginx deployment, systemd, web infrastructure, SSL/TLS configuration |
| 26 | [Microsoft Entra ID Administration with PowerShell and Microsoft Graph](./Lab-26-Microsoft-EntraID-Administration-with-PowerShell-and-Microsoft-Graph/) | Microsoft Graph PowerShell, delegated OAuth scopes, Entra user/group enumeration, RBAC, privileged-role verification, secure session management |
| 27 | [Azure Windows Diagnostic Automation with GitHub Actions, OIDC, and Azure RBAC](./Lab-27-Azure-Windows-Diagnostic-Automation-with-GitHub-Actions-OIDC/) | GitHub Actions, Entra workload identity federation, OIDC, Azure RBAC, Azure CLI, VM Run Command, Windows Server, PowerShell, persistent HTML reporting, VM lifecycle automation |

---

## Selected High-Signal Labs

### [Lab 27 — Azure Windows Diagnostic Automation](./Lab-27-Azure-Windows-Diagnostic-Automation-with-GitHub-Actions-OIDC/)

Built an end-to-end Azure automation workflow where GitHub Actions authenticates to Microsoft Azure through **Microsoft Entra ID OIDC workload identity federation**, receives scoped authorization through **Azure RBAC**, starts a Windows Server VM, remotely executes a PowerShell diagnostic toolkit with **Azure VM Run Command**, generates a persistent HTML report, and automatically deallocates the VM.

**Standalone project:** [azure-windows-diagnostic-automation-workflow](https://github.com/johninfra/azure-windows-diagnostic-automation-workflow)

### [Lab 26 — Microsoft Entra ID Administration with PowerShell and Microsoft Graph](./Lab-26-Microsoft-EntraID-Administration-with-PowerShell-and-Microsoft-Graph/)

Used Microsoft Graph PowerShell with delegated OAuth permissions to connect to Microsoft Entra ID, enumerate users and groups, inspect directory roles, validate privileged assignments, and securely terminate the administrative session.

### [Lab 22 — PowerShell Vulnerability Management and Security Audit Framework](./Lab-22-PowerShell-Vulnerability-Management-and-Security-Audit-Framework/)

Built a PowerShell-driven endpoint assessment workflow covering inventory, security controls, services, exposure, and structured risk reporting.

### [Lab 18 — Splunk SIEM Security Monitoring and Alerting Platform](./Lab-18-Splunk-SIEM-Security-Monitoring-and-Alerting-Platform/)

Deployed Splunk, ingested security telemetry, built SPL searches and dashboards, and configured alerting for simulated reconnaissance activity.

### [Lab 12 — Network Traffic Analysis and Security Monitoring](./Lab-12-Network-Traffic-Analysis-and-Security-Monitoring-with-Nmap-Wireshark-and-Splunk/)

Combined Nmap, Wireshark, and Splunk to perform host discovery, service enumeration, packet analysis, network validation, and SIEM-based investigation.

---

## Tools and Technologies

| Area | Technologies |
|---|---|
| Cloud | Microsoft Azure, Azure Virtual Machines, Azure resource groups, Azure RBAC, Azure CLI, Azure VM Run Command |
| Identity | Microsoft Entra ID, Active Directory, Microsoft Graph, App Registrations, Enterprise Applications, OAuth, OIDC |
| Automation & DevOps | PowerShell, GitHub Actions, CI/CD concepts, workload identity federation |
| Windows | Windows 10/11, Windows Server 2022, RDP, Event Viewer, Windows Services, Defender, Firewall |
| Linux | Ubuntu Linux, Kali Linux, SSH, Nginx, systemd |
| Security Monitoring | Splunk Enterprise, SPL, Sysmon, Windows Security Logs, Windows Event Logs |
| Networking | TCP/IP, DNS, DHCP, VPN, SMB, Wireshark, Nmap |
| Virtualization | VMware Workstation, Azure Virtual Machines |
| IT Operations | ITSM, help desk workflows, incident management, ticket documentation, remote support |
| Reporting | HTML reporting, PowerShell-generated diagnostics, security and system-health reports |

---

## What This Portfolio Demonstrates

This repository shows progression across multiple layers of enterprise IT:

```text
End-User Support
      |
      v
Windows / Linux Administration
      |
      v
Networking and Active Directory
      |
      v
Security Monitoring and PowerShell Automation
      |
      v
Microsoft Entra ID and Microsoft Graph
      |
      v
Azure Administration, RBAC, OIDC, and Cloud Automation
```

The goal is to demonstrate not only familiarity with tools, but the ability to connect **identity, infrastructure, security, automation, and troubleshooting** into repeatable operational workflows.

---

## Professional Summary

CompTIA **Security+** and **A+** certified IT professional focused on **systems administration, Microsoft Azure, identity and access management, cloud security, cybersecurity operations, and Tier 2 technical support**.

Hands-on work in this portfolio includes Windows and Windows Server administration, Active Directory and Microsoft Entra ID, Microsoft Graph, RBAC, OIDC workload identity federation, PowerShell automation, GitHub Actions, Azure VM administration, networking, Splunk SIEM, endpoint security, and structured troubleshooting.

The portfolio demonstrates practical readiness for roles such as **Tier 2 IT Support, Desktop Support, Junior Systems Administration, IAM/Identity Administration, Microsoft 365/Entra Administration, and entry-level cloud or security operations roles**.

---

## Related Portfolio

- **GitHub Profile:** https://github.com/johninfra
- **Standalone Azure Windows Diagnostic Automation:** https://github.com/johninfra/azure-windows-diagnostic-automation-workflow
- **Windows IT Diagnostic Toolkit:** https://github.com/johninfra/windows-it-diagnostic-toolkit
- **Azure Enterprise Administration Lab:** https://github.com/johninfra/azure-enterprise-administration-lab
- **Azure Identity Governance Console:** https://github.com/johninfra/azure-identity-governance-console
