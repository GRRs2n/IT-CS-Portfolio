# Wireshark and Shodan Network Analysis

## Overview
This project explores network security through the analysis of packet captures (pcaps) and external reconnaissance using Shodan. By examining network traffic and publicly exposed services, I learned how attackers may exploit insecure protocols and misconfigured systems and how defenders can proactively identify and mitigate risks.

## What I Did
- **Anti‑virus update session (av.pcap):** Inspected a pcap of an anti‑virus software update using Wireshark. Found the client used anonymous FTP to download nine files: `avp.klb`, `avp.set`, `avp_ext.set`, `avp_x.set`, `black.lst`, `ca.avc`, `daily-ex.avc`, `daily.avc` and `master.xml`. Because FTP transfers data in clear text, any attacker on the path could intercept credentials and tamper with the update files.
- **Network protocol capture (NetworkProtocol.pcap):** Discovered that the capture used SNMP v1 with the community string `public`. Parsed object identifiers such as `sysObjectID`, `prtChannelState`, `sysName`, `sysLocation` and `ifPhysAddress`, which reveal device type, status, names and MAC addresses. Attackers can leverage this information to fingerprint systems and target known vulnerabilities.
- **Malware beacon (Malware.pcap):** Detected malware beaconing to domains like `nofbiatdominicana.com` and `kpai7ycr7jqxqkilp.torexplorer.com`. DNS responses resolved to an internal IP address, indicating the victim was behind a NAT. Packet analysis showed the host was a virtual machine and that the malware communicated over TLS. The beacon directed victims to a ransom payment URL. This demonstrates how modern malware uses encryption and anonymised infrastructure to evade inspection.
- **Shodan reconnaissance:** Created a Shodan account and used it to search for services with default credentials, as well as keywords like `vnc`, `rdp` and `scada`. The searches revealed numerous HP printers, nginx servers and industrial control systems accessible over the internet, many still using default or no credentials. This highlighted the danger of exposed critical infrastructure services and misconfigurations.

## Findings
- **FTP update sessions are insecure:** Transfers used anonymous FTP, retrieving multiple update files without encryption. Adversaries could intercept credentials and tamper with updates.
- **SNMP v1 leaks device metadata:** Using the default `public` community string exposes detailed host information and should be replaced with SNMP v3 and strong community strings.
- **Malware uses encrypted channels:** Modern threats use TLS and Tor domains to hide command‑and‑control traffic, making detection harder; defenders must monitor encrypted traffic patterns and DNS queries.
- **Shodan exposes misconfigured devices:** Default passwords and open remote‑access ports are still common. Regularly auditing internet‑facing services via Shodan helps find and remediate misconfigurations before attackers do.

## Lessons Learned
- Always use secure protocols such as SFTP/FTPS or HTTPS for software updates; disable anonymous FTP.
- Replace SNMP v1 with SNMP v3 and use unique, complex community strings.
- Monitor DNS and TLS traffic for signs of beaconing and maintain endpoint protection capable of inspecting encrypted C2 channels.
- Regularly scan your own network with tools like Shodan to identify exposed services and remediate weak credentials and outdated software.
- Document and remediate misconfigurations promptly and educate users about the risks of default passwords.

## Next Steps
- Convert the FTP update mechanism to a secure alternative and validate the integrity of updates with cryptographic signatures.
- Implement network‑wide policies requiring SNMP v3 and encrypted management protocols.
- Develop detection rules for malware beaconing patterns and integrate them into SIEM and IDS systems.
- Schedule periodic external scans using Shodan or similar services as part of the asset management process.
