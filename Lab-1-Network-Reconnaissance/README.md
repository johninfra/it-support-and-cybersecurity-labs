# Lab 1 - Network Reconnaissance and Service Enumeration with Nmap

## Overview
This lab demonstrates basic network reconnaissance using Kali Linux to scan a Windows virtual machine. The objective was to simulate real world penetration testing techniques by identifying IP addresses, verifying connectivity, and discovering open ports and services within a controlled environment.

---

## Lab Setup
- Host Machine: Windows Laptop  
- Virtualization: VMware Workstation Player  
- Attacker Machine: Kali Linux VM  
- Target Machine: Windows 10 or 11 VM  
- Network Type: NAT (same subnet)  

### Virtual Machine Setup
![VM Setup](screenshots/vm-setup.png)

---

## Tools Used
- Kali Linux Terminal  
- Nmap  
- ip a  
- ipconfig  
- ping  

---

## Tasks Performed

### 1. Identified IP Addresses
Retrieved the IP address of the Kali Linux machine using:

ip a  

Retrieved the IP address of the Windows machine using:

ipconfig  

This step ensures both machines are on the same network.

![IP Configuration](screenshots/ip-config.png)

---

### 2. Verified Network Connectivity
Tested connectivity between machines using:

ping [target IP]

Confirmed successful communication between Kali Linux and the Windows VM.

![Ping Test](screenshots/ping-test.png)

---

### 3. Performed Network Scan
Executed an Nmap scan to identify open ports and services:

nmap -Pn -sV [target IP]

This scan detects running services and versions on the target system.

![Nmap Command](screenshots/nmap-scan.png)

---

### 4. Analyzed Scan Results
Reviewed the scan output and identified open ports and services such as:

- Port 139 (NetBIOS)  
- Port 445 (SMB)  
- Port 443 (HTTPS)  

These services indicate typical Windows network functionality and potential attack surfaces.

![Nmap Results](screenshots/nmap-results.png)

---

## Results
- Successfully identified IP addresses of both machines  
- Verified connectivity between attacker and target systems  
- Detected open ports and active services on the target machine  
- Simulated a basic network reconnaissance scenario  

---

## Key Takeaways
- Network reconnaissance is the first step in penetration testing  
- Ping verifies connectivity between systems  
- Nmap is used for port scanning and service enumeration  
- Open ports can indicate potential vulnerabilities  
- Understanding network structure is critical for cybersecurity  

---

## Conclusion
This lab demonstrated the fundamentals of network reconnaissance using Kali Linux and Nmap in a controlled environment. I successfully identified IP addresses, verified connectivity, and scanned a target machine for open ports and services. This process helped me understand how systems communicate and how attackers gather information during the early stages of penetration testing. I also gained hands on experience using command line tools and interpreting scan results. Overall, this lab built a strong foundation for more advanced cybersecurity tasks such as vulnerability scanning and exploitation.
