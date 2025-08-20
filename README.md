# Project: Network Penetration Testing & Password Cracking

## Overview
This project demonstrates a comprehensive network penetration testing methodology involving host discovery, service enumeration, and password cracking attacks. The assessment targeted a Metasploitable vulnerable machine using tools like fping, nbtscan, nmap, and Medusa to identify security weaknesses and gain unauthorized access.

---

## Configuration & Screenshots

### 1. Network Configuration Verification
- Verified Kali Linux network configuration using ifconfig
- Identified IP address and network interface details
- Established baseline network connectivity

![Ifconfig Command on Kali](screenshots/kali-ifconfig.png)
*Kali Linux network configuration showing IP address and interface details*

### 2. Host Discovery with Fping
- Scanned entire subnet (192.168.56.0/24) for alive hosts
- Used fping with -a flag to show only responsive hosts
- Generated summary statistics including response times

![Fping Host Discovery](screenshots/fping-scan.png)
*Active host discovery using fping showing responsive systems*

![Fping Statistics](screenshots/fping-statistics.png)
*Fping summary statistics showing 3 alive hosts out of 254*

### 3. NetBIOS Identification with Nbtscan
- Scanned identified hosts for NetBIOS information
- Identified Metasploitable machine through service enumeration
- Gathered hostname and service information

![Nbtscan Results](screenshots/nbtscan-results.png)
*NetBIOS scanning identifying Metasploitable target system*

### 4. Service Enumeration with Nmap
- Conducted TCP SYN stealth scan (-sS) on target
- Performed service version detection (-sV)
- Enabled verbose output for detailed results

![Nmap Initial Scan](screenshots/nmap-initial-scan.png)
*Nmap service enumeration showing open ports and versions*

![Nmap Detailed Results](screenshots/nmap-detailed-results.png)
*Comprehensive nmap results revealing vulnerable services*

### 5. Target Service Selection
- Selected four services for password cracking attempts
- Chose SSH, RSH, RLOGIN, and VNC based on vulnerability assessment
- Prioritized services with known weak authentication mechanisms

![Selected Services](screenshots/selected-services.png)
*Target services selected for password cracking attempts*

### 6. RSH Cracking Attempt
- Attempted brute-force attack against RSH service
- Used Medusa with username and password wordlists
- Service resisted cracking attempts with provided credentials

![RSH Cracking Attempt](screenshots/rsh-cracking-failed.png)
*Unsuccessful RSH password cracking attempt*

![RSH Cracking Continuation](screenshots/rsh-cracking-failed2.png)
*Continued RSH cracking attempts showing no successful logins*

### 7. SSH Cracking Attempt
- Targeted SSH service with common credential combinations
- Utilized Medusa's SSH module for authentication attacks
- Service demonstrated stronger password security

![SSH Cracking Attempt](screenshots/ssh-cracking-failed.png)
*SSH password cracking attempts showing no successful breaches*

![SSH Cracking Continuation](screenshots/ssh-cracking-failed2.png)
*Continued SSH attacks demonstrating service resilience*

### 8. Successful RLOGIN Compromise
- Successfully cracked RLOGIN service credentials
- Discovered weak passwords for root and www-data accounts
- Gained unauthorized access to target system

![RLOGIN Successful Crack](screenshots/rlogin-cracking-success.png)
*Successful RLOGIN password compromise showing weak credentials*

![RLOGIN Additional Credentials](screenshots/rlogin-cracking-success2.png)
*Additional compromised credentials through RLOGIN service*

### 9. Successful VNC Compromise
- Cracked VNC authentication using common passwords
- Discovered multiple accounts using "password" as credential
- Gained graphical access to target system

![VNC Successful Crack](screenshots/vnc-cracking-success.png)
*VNC password compromise revealing multiple weak credentials*

### 10. RLOGIN Shell Access
- Established remote shell access using compromised credentials
- Gained root-level privileges on target system
- Verified access through system commands

![RLOGIN Shell Access](screenshots/rlogin-shell-access.png)
*Remote shell access gained through compromised RLOGIN credentials*

![RLOGIN Access Verification](screenshots/rlogin-access-verification.png)
*Privilege verification and shadow file access demonstration*

### 11. VNC Graphical Access
- Established VNC remote desktop connection
- Gained graphical root access to target system
- Demonstrated complete system compromise

![VNC Graphical Access](screenshots/vnc-graphical-access.png)
*VNC remote desktop connection showing graphical access*

![VNC Access Verification](screenshots/vnc-access-verification.png)
*Root privilege verification through VNC connection*

---

## Observations and Challenges

### Technical Challenges
- **Service Resilience**: SSH and RSH resisted brute-force attacks due to stronger authentication
- **Network Limitations**: Scan times affected by network latency and host responsiveness
- **Tool Configuration**: Medusa required precise module selection and thread management

### Security Findings
- **Weak Credentials**: RLOGIN and VNC services used extremely weak passwords
- **Lack of Lockout**: No account lockout mechanisms enabled on vulnerable services
- **Default Configurations**: Multiple services retained factory default credentials

### Performance Considerations
- **Scan Efficiency**: Fping provided faster host discovery than traditional ping sweeping
- **Resource Usage**: Medusa cracking attempts consumed significant network bandwidth
- **Time Investment**: Comprehensive testing required substantial time investment

---

## Reflections

### Technical Insights
- **Protocol Vulnerabilities**: Clear security hierarchy between encrypted (SSH) and unencrypted (RLOGIN/RSH) services
- **Password Complexity**: Critical importance of strong password policies across all services
- **Attack Surface Reduction**: Value of disabling unnecessary network services

### Security Implications
- **Legacy Service Risks**: RLOGIN and RSH represent significant security liabilities
- **Default Configuration Dangers**: Factory settings often create immediate vulnerabilities
- **Monitoring Gaps**: Lack of detection mechanisms for brute-force attacks

### Operational Lessons
- **Progressive Testing**: Importance of methodical, layered assessment approach
- **Tool Proficiency**: Need for deep understanding of multiple security assessment tools
- **Documentation Value**: Comprehensive logging essential for analysis and reporting

---

## How to Reproduce

### Prerequisites
- Kali Linux penetration testing distribution
- Metasploitable or similar vulnerable target machine
- Network connectivity between testing and target systems
- Administrative privileges on testing machine

### Implementation Steps

1. **Network Configuration Verification**
```bash
ifconfig
ip addr show