# Lab 1 - Network Reconnaissance

## Overview
This lab demonstrates basic network reconnaissance using Kali Linux to scan a Windows machine. The goal was to simulate real world penetration testing techniques by identifying open ports and services in a controlled environment.

## Lab Setup
- Host Machine: Windows Laptop
- Virtualization: VMware Workstation Player
- Attacker Machine: Kali Linux
- Target Machine: Windows VM
- Network Type: NAT (same subnet)

## Tools Used
- Nmap
- Kali Linux Terminal
- Command Prompt

## Tasks Performed
- Identified IP addresses of both machines
- Verified connectivity using ping
- Performed port scan using Nmap
- Analyzed open ports and services

## Commands Used
- ip a
- ipconfig
- ping [target IP]
- nmap -Pn -sV [target IP]

## Results
- Successfully identified open ports
- Verified communication between machines
- Simulated basic network scanning scenario

## Key Takeaways
- Learned how to perform network reconnaissance
- Understood how port scanning works
- Gained experience using Nmap

## Future Improvements
- Perform deeper scans using additional Nmap flags
- Identify vulnerabilities on open ports

## Conclusion
- This lab demonstrated the fundamentals of network reconnaissance using Kali Linux and Nmap in a controlled environment. I successfully identified IP addresses, verified connectivity, and scanned a target machine for open ports and services. This process helped me understand how systems communicate and how attackers gather information during the early stages of penetration testing. I also gained hands on experience using command line tools and interpreting scan results. Overall, this lab built a strong foundation for more advanced cybersecurity tasks like vulnerability scanning and exploitation.
