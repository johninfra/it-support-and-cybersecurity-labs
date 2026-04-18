# Lab 3 - Network Troubleshooting

## Overview
This lab demonstrates real world network troubleshooting in a VMware virtual environment. The objective was to diagnose and resolve a loss of network connectivity after manually releasing the IP configuration on a Windows virtual machine.

This simulates a common IT support scenario where a system loses connectivity due to DHCP or network misconfiguration.

---

## Lab Setup
- Host Machine: Windows Laptop  
- Virtualization: VMware Workstation Player  
- Client Machine: Windows 10 or 11 VM  
- Network Type: NAT  

---

## Tools Used
- Command Prompt  
- ipconfig  
- ping  
- VMware Network Settings  

---

## Problem Encountered
After running:

ipconfig /release

The system lost network connectivity and produced errors preventing IP renewal. The machine was unable to access the network or internet.

---

## Tasks Performed

### 1. Checked IP Configuration
Ran:

ipconfig /all

Observed incorrect or missing configuration.


---

### 2. Attempted IP Renewal
Ran:

ipconfig /renew

Received adapter state error.


---

### 3. Tested Connectivity
Ping test to expected gateway failed:

ping 192.168.110.1

Result:
- 100 percent packet loss


---

### 4. Identified Correct Gateway
Discovered VMware NAT gateway was:

192.168.110.2

---

### 5. Retested Network Connectivity
Ran:

ping 192.168.110.2  
ping 8.8.8.8  

Results:
- Successful replies
- 0 percent packet loss


---

### 6. Verified Final Configuration
Ran:

ipconfig /all

Confirmed:
- Valid IP address
- DHCP enabled
- Correct gateway


---

## Results
- Successfully restored network connectivity by renewing DHCP configuration and identifying the correct gateway within the NAT network.

---

## Key Takeaways
- Releasing IP configuration can temporarily break connectivity
- DHCP must successfully renew for network access to return
- VMware NAT networks may use .2 as the gateway instead of .1
- Systematic troubleshooting is essential in IT environments

---

## Conclusion
This lab provided hands on experience troubleshooting a real network failure scenario. After releasing the IP configuration, the system lost connectivity due to a temporary DHCP issue. By diagnosing the problem, identifying the correct gateway, and verifying network settings, full connectivity was restored. This reinforced practical troubleshooting skills used in real IT support roles.
