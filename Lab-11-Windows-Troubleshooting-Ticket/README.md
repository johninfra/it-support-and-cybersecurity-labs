# Lab 11 - Windows Troubleshooting and Printer Support

## Overview  
This lab simulates a real world IT support scenario involving software installation and printer troubleshooting on a Windows system. The objective was to diagnose common user issues, restore functionality, and verify successful operation using standard help desk procedures.

---

## Lab Setup  

- **Host Machine:** Windows Laptop  
- **Virtualization:** VMware Workstation Player  
- **Target Machine:** Windows 10/11 VM  
- **Network Type:** NAT  

---

## Tools Used  

- Windows Settings  
- Control Panel  
- Services (services.msc)  
- Command Prompt  
- Devices and Printers  

---

## Tasks Performed  

1. Installed a basic software application  
2. Verified application functionality  
3. Simulated printer issue (printer offline or not printing)  
4. Restarted Print Spooler service  
5. Removed and re-added printer  
6. Printed a test page to confirm functionality  

---

## Commands Used  

- services.msc

---

## Screenshots  

### Software Installed  
![Software Installed](screenshots/software-installed.png)

### Application Opened Successfully  
![Application Open](screenshots/app-open.png)

### Printer Issue Detected  
![Printer Issue](screenshots/printer-issue.png)

### Print Spooler Restart  
![Spooler Restart](screenshots/spooler-restart.png)

### Test Page Printed  
![Test Print](screenshots/test-print.png)

---

## Results  

- Successfully installed and verified software functionality  
- Identified and diagnosed printer connectivity issue  
- Restarted critical Windows service to resolve printing failure  
- Restored printer functionality and confirmed successful test print  

---

## Key Takeaways  

- Learned how to troubleshoot common Windows printer issues  
- Understood the role of the Print Spooler service in print management  
- Gained experience installing and verifying software in a Windows environment  
- Reinforced structured troubleshooting methodology used in IT support  

---

## Skills Demonstrated  

- Windows troubleshooting and system diagnostics  
- Software installation and validation  
- Printer troubleshooting and configuration  
- Service management using Windows tools  
- Problem solving using structured IT support workflows

- ---

## Conclusion  

This lab demonstrated how to troubleshoot common Windows issues related to software installation and printer functionality. The process involved identifying the problem, using system tools to diagnose the issue, and applying a targeted fix by restarting the Print Spooler service. After resolving the issue, functionality was verified through a successful test print. This exercise reinforced the importance of structured troubleshooting in IT support environments. Overall, the lab provided practical experience handling real world help desk scenarios.


- ---

## Ticket Scenario  

**Scenario:**  
A user reports that they are unable to print documents and their printer appears offline.

**Issue:**  
Printer is not responding and print jobs are stuck in the queue.

**Diagnosis:**  
Checked printer status in Devices and Printers and identified that the Print Spooler service was not functioning properly.

**Resolution:**  
Restarted the Print Spooler service and reinitialized the printer connection.

**Verification:**  
Printed a successful test page and confirmed the user could resume normal printing operations.
