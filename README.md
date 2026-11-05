# Elevate Labs - Task 1: Local Network Port Scanning

## Objective
To perform basic network reconnaissance and discover open ports on devices within a local authorized network using Nmap.

## Environment
- **Attacker:** Kali Linux (192.168.126.10)
- **Target Range:** 192.168.126.0/24
- **Tool:** Nmap 7.99

## Methodology
1. Identified the local IP range using `ip a`.
2. Executed a TCP SYN scan using the following command:
   `sudo nmap -sS 192.168.126.0/24 -oA network_scan`
3. Analyzed the results to identify open ports and the services running on them.

## Key Findings
The scan discovered several live hosts on the network, including the VMware gateway and the target Metasploitable 2 machine (192.168.126.129). 

**Critical Open Ports Identified:**
- **Port 21 (FTP):** Unencrypted file transfer.
- **Port 23 (Telnet):** Unencrypted remote login.
- **Port 80 (HTTP):** Unencrypted web server.
- **Port 445 (SMB):** File sharing (high risk for ransomware).

## Security Risks
- **FTP (21) & Telnet (23):** Transmit credentials in clear text. An attacker could use Wireshark to sniff passwords.
- **SMB (445):** Exposed SMB shares are the primary attack vector for worms like WannaCry.

