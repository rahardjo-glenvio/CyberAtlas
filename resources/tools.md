---
title: "Tools Reference"
section: resources
date_created: 2026-06-01
last_updated: 2026-06-01
status: draft
tags: [tools, reference, resources]
---

# Tools Reference

Security tools organized by category. Each entry notes what the tool does, when to use it, and what makes it worth knowing.

This is not an exhaustive list. It is a reference for tools that are widely used, well-documented, and appropriate for the contexts described in this repository.

---

## Reconnaissance & OSINT

| Tool | Description | Use Case |
|---|---|---|
| Maltego | Graph-based link analysis and OSINT | Visualizing relationships between entities |
| theHarvester | Email, subdomain, and name gathering | External reconnaissance |
| Shodan | Internet-connected device search engine | Identifying exposed services |
| Recon-ng | Web reconnaissance framework | Modular external recon |

---

## Network Scanning & Enumeration

| Tool | Description | Use Case |
|---|---|---|
| Nmap | Network scanner and service/version detector | Port scanning, service enumeration, OS detection |
| Masscan | High-speed port scanner | Rapid large-scale scanning |
| Netcat | Network utility for reading/writing TCP/UDP | Banner grabbing, reverse shells, pivoting |
| Wireshark | Network protocol analyzer | Packet capture and analysis |
| tcpdump | Command-line packet analyzer | Lightweight packet capture |

---

## Web Application Testing

| Tool | Description | Use Case |
|---|---|---|
| Burp Suite | Web proxy and testing platform | Intercepting, analyzing, and modifying HTTP traffic |
| OWASP ZAP | Open-source web scanner | Automated and manual web vulnerability testing |
| Gobuster | Directory/file brute-forcer | Web content discovery |
| ffuf | Fast web fuzzer | Directory, file, and parameter fuzzing |
| SQLMap | SQL injection detection and exploitation | Testing and exploiting SQL injection |

---

## Exploitation

| Tool | Description | Use Case |
|---|---|---|
| Metasploit Framework | Exploit development and execution platform | Exploiting known vulnerabilities in lab environments |
| searchsploit | Offline exploit database search | Finding known exploits for identified services |

---

## Password & Credential

| Tool | Description | Use Case |
|---|---|---|
| Hashcat | GPU-accelerated password cracker | Cracking captured hashes |
| John the Ripper | Password cracker | Hash cracking with rule-based attacks |
| Hydra | Network login brute-forcer | Brute-forcing login services |
| CrackMapExec | Post-exploitation framework for Windows/AD | Credential testing across SMB, LDAP, WMI |

---

## Active Directory

| Tool | Description | Use Case |
|---|---|---|
| BloodHound | AD attack path mapping | Visualizing privilege escalation paths |
| Impacket | Python library for Windows protocols | SMB, Kerberos, and DCOM operations |
| Rubeus | Kerberos toolset | Kerberoasting, ticket manipulation |
| Mimikatz | Credential extraction tool | Dumping Windows credentials (authorized testing only) |

---

## Forensics & Incident Response

| Tool | Description | Use Case |
|---|---|---|
| Autopsy | Digital forensics platform | Disk image analysis |
| Volatility | Memory forensics framework | Analyzing RAM captures |
| FTK Imager | Disk imaging and evidence acquisition | Forensic image creation |
| Velociraptor | Endpoint forensics and monitoring | DFIR data collection at scale |

---

## Blue Team & Detection

| Tool | Description | Use Case |
|---|---|---|
| Wazuh | Open-source SIEM and XDR | Security monitoring, log analysis, detection |
| Elastic Stack (ELK) | Log aggregation and analysis platform | SIEM, threat hunting, visualization |
| Zeek | Network traffic analyzer | Network security monitoring |
| Suricata | Network threat detection engine | IDS/IPS |
| YARA | Pattern matching for malware | Writing and testing malware detection rules |

---

## Malware Analysis

| Tool | Description | Use Case |
|---|---|---|
| Any.run | Interactive online malware sandbox | Dynamic analysis with visual interface |
| VirusTotal | Multi-engine scanner | File and URL scanning, hash lookups |
| Ghidra | NSA reverse engineering tool | Disassembly and decompilation |
| x64dbg | Windows debugger | Dynamic analysis of binaries |
| PE Studio | Static PE file analyzer | Rapid triage of Windows executables |

---

→ [Back to Resources](README.md)
