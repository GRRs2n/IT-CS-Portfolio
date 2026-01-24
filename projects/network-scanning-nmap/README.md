# Network Scanning with Nmap

## Overview
This project summarizes a footprinting and network discovery exercise using Zenmap (the graphical front end for Nmap). The aim was to inventory hosts, identify open services, and evaluate exposure in a lab network.

## What I Did
- Conducted a ping sweep scan across the 172.16.1.0/24 subnet using Zenmap. The scan discovered three live hosts: two running Windows and one running Linux【608240012654197†L15-L20】.
- Performed an “Intense” scan against each host to enumerate services, operating system details and potential vulnerabilities. The scan revealed that host 172.16.1.115 exposed FTP and HTTP services on ports 21 and 80【608240012654197†L25-L33】.
- Connected to the FTP service on 172.16.1.115 with anonymous login and enumerated the file system. Sensitive files such as `LogonHelp.txt`, `GetData`, `GetEnergy`, `GetLotsofInfo` and other documents were publicly accessible【608240012654197†L35-L46】.
- Checked that Telnet was not running on any hosts and confirmed that port 23 was closed【608240012654197†L25-L33】.
- Reflected on scanning ethics and best practices: avoid scanning unauthorized networks, obtain approval, and ensure scans do not disrupt services【608240012654197†L51-L65】.

## Findings
- At least three hosts responded to ICMP probes; network enumeration showed both Windows and Linux systems present【608240012654197†L15-L20】.
- The FTP server allowed anonymous logins and contained numerous sensitive files; there was no encryption or authentication【608240012654197†L35-L46】.
- The HTTP service on port 80 responded, indicating a web application may be present.
- No Telnet service was detected, which is good practice.

## Lessons Learned
- Nmap/Zenmap is a powerful tool for discovering hosts and enumerating services; combining ping sweeps with deeper scans provides a clear picture of network exposure【608240012654197†L15-L20】.
- Anonymous FTP is a significant risk; even internal services should enforce authentication and restrict directory listing【608240012654197†L35-L46】.
- Always obtain authorization before scanning networks; excessive scanning or aggressive options can disrupt services or trigger security alerts【608240012654197†L51-L65】.
- Supplement Nmap results with other tools such as Wireshark for packet capture, Netcat for banner grabbing and Nessus for vulnerability assessment【608240012654197†L51-L65】.

## Next Steps
- Disable anonymous FTP on all systems and require credentials with encrypted transport (e.g. SFTP or FTPS).
- Harden web and FTP services: restrict access to necessary IP ranges and enforce strong authentication.
- Schedule regular vulnerability scans using tools like Nessus to detect outdated software and configuration issues.
- Explore deeper enumeration techniques (e.g. service version detection, vulnerability scanning) while maintaining respect for network policy.
