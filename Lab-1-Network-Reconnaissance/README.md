#  Lab 01 - Network Reconnaissance and Service Enumeration

## Overview  
This lab demonstrates a basic cybersecurity home lab where network reconnaissance was performed using Kali Linux against a Windows virtual machine. The objective was to simulate real world penetration testing techniques by identifying open ports and exposed services within a controlled environment.

---

## Lab Setup  

- **Host Machine:** Windows Laptop  
- **Virtualization:** VMware Workstation Player  
- **Attacker Machine:** Kali Linux VM  
- **Target Machine:** Windows 10/11 VM  
- **Network Type:** NAT (same subnet)

---

## Tools Used  

- **Nmap** (Network scanning)  
- **Kali Linux Terminal**  
- **Windows Command Prompt**

---

## Network Configuration  

- **Kali Linux IP:** 192.168.110.133  
- **Windows VM IP:** 192.168.110.131  
- Verified connectivity using ping and IP configuration commands  

---

## Tasks Performed  

1. Identified IP addresses on both machines  
2. Verified connectivity using ping  
3. Performed a service and port scan using Nmap  
4. Analyzed open ports and detected services  

---

## Commands Used  

```bash
ip a
ipconfig
ping 192.168.110.131
nmap -Pn -sV 192.168.110.131

## Screenshots

### VM Network Setup  
![VM Setup](screenshots/vm-setup.png)

### Kali Linux IP Address  
![Kali IP](screenshots/kali-ip.png)

### Windows IP Address  
![Windows IP](screenshots/windows-ip.png)

### Ping Connectivity Test  
![Ping Test](screenshots/ping-test.png)

### Nmap Command Execution  
![Nmap Command](screenshots/nmap-command.png)

### Nmap Scan Results  
![Nmap Results](screenshots/nmap-results.png)

## RESULTS
- Successfully identified open ports and services on the target system
- Detected:
  135/tcp (MSRPC)
  139/tcp (NetBIOS)
  445/tcp (SMB)
  5357/tcp (WSDAPI)
- Confirmed network communication between attacker and target machines

## SKILLS DEMONSTRATED
- Network reconnaissance and enumeration
- Use of Nmap for service and port scanning
- IP addressing and subnet verification
- Virtual machine networking configuration (NAT)
- Command line usage in Linux and Windows environments
- Understanding of common network services (SMB, RPC, NetBIOS)

## CONCLUSION
This lab demonstrated how to perform structured network reconnaissance in a controlled virtual environment. Identifying active hosts and exposed services is a foundational skill in both IT support and cybersecurity. The process followed in this lab mirrors real world troubleshooting and penetration testing workflows, reinforcing practical and job relevant technical skills.
