# Incident Response Case Study: Luigi's Data Exfiltration

## Overview
This case study analyzes an incident at Luigi's Inc. where an employee's infected personal laptop introduced malware into the corporate network. The compromised machine scanned the network, identified an anonymously accessible FTP server, and exfiltrated sensitive data via an encrypted VPN connection over a long weekend【603881384706818†L0-L24】. The case highlights the dangers of unmanaged devices and outdated security controls.

## Incident Details

- **Unauthorized Device:** A personal laptop infected with PSL malware connected to the corporate Wi‑Fi and obtained a DHCP address【603881384706818†L1-L9】.
- **C2 Connection and Network Scanning:** The malware established communication with a command‑and‑control server and scanned the local network, finding an FTP server that allowed anonymous access【603881384706818†L10-L19】.
- **Data Exfiltration:** The attacker compressed the contents of the FTP site and transferred the data over an encrypted VPN tunnel【603881384706818†L20-L23】.
- **Delayed Response:** The user noticed performance issues but left the device running over a long weekend. The NOC detected unusual encrypted traffic but could not decrypt it because the malicious domain list was four months out of date【603881384706818†L24-L31】.
- **Discovery:** After the weekend, the help desk tied the traffic to the personal laptop, which lacked endpoint protection and corporate security software. Forensics confirmed the PSL infection and discovered a temporary file containing the FTP directory listing with sensitive information【603881384706818†L34-L56】.

## Controls That Could Have Prevented the Attack

The incident underscores the importance of several CIS Controls:

- **Control 1 – Inventory of Enterprise Assets:** Maintain an up‑to‑date inventory and block unauthorized devices from connecting【419913622882797†L29-L44】.
- **Control 2 – Inventory of Software Assets:** Track installed software to detect rogue tools【419913622882797†L29-L44】.
- **Control 4 – Secure Configuration of Enterprise Assets and Software:** Disable anonymous FTP and unnecessary services【419913622882797†L47-L50】.
- **Control 6 – Access Control Management:** Enforce least‑privilege access and multi‑factor authentication for exposed services【419913622882797†L50-L52】【419913622882797†L95-L101】.
- **Control 10 – Malware Defenses:** Deploy behavior‑based anti‑malware and endpoint protection to detect C2 activity【419913622882797†L53-L57】【419913622882797†L103-L109】.
- **Control 13 – Network Monitoring and Defense:** Centralize alerting and deploy IDS to detect scans and anomalous encrypted traffic【419913622882797†L111-L118】.
- **Control 14 – Security Awareness and Skills Training:** Educate employees about the risks of connecting personal devices and encourage prompt reporting【419913622882797†L119-L124】.
- **Control 17 – Incident Response Management:** Designate incident handlers and maintain a response plan to ensure timely containment and remediation【419913622882797†L127-L133】.

## Lessons Learned

- Unauthorized devices are a major risk; asset inventories and NAC should block them.
- Legacy services like anonymous FTP are attractive targets and should be disabled.
- Keeping threat intelligence (malicious domain lists) current is critical for detection.
- Behavioural anti‑malware and IDS can detect unusual scanning and VPN traffic even if encrypted.
- User education and clear incident response processes shorten detection and containment time.

## Next Steps

- Implement the CIS Controls listed above, including asset and software inventories, secure configurations, and endpoint protection.
- Update and automate threat intelligence feeds to detect new malicious domains.
- Conduct regular security awareness training focused on device policies and reporting.
- Develop and practice an incident response plan to ensure rapid investigation and containment.
