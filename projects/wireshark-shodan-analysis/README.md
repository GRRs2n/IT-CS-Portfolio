# Wireshark and Shodan Network Analysis

## Overview
This project explores network security through the analysis of packet captures (pcaps) and external reconnaissance using Shodan. By examining network traffic and publicly exposed services, I learned how attackers may exploit insecure protocols and misconfigured systems and how defenders can proactively identify and mitigate risks.

## What I Did
- Analyzed the `av.pcap` capture using Wireshark to inspect an anti‑virus software update session. I identified the source IP (81.131.131.6), destination (80.239.144.76), FTP protocol in use and noted that the connection used anonymous credentials. The RETR command was used to retrieve nine files (`avp.klb`, `avp.set`, `avp_ext.set`, `avp_x.set`, `black.lst`, `ca.avc`, `daily-ex.avc`, `daily.avc`, `master.xml`)【408223297298984†L9-L60】. Because FTP is unencrypted an attacker could intercept credentials and tamper with the update files【408223297298984†L56-L60】.
- Opened the `NetworkProtocol.pcap` and discovered that it was using SNMP version 1 with the community string `public`【408223297298984†L72-L96】. I parsed several Object IDs: `sysObjectID`, `prtChannelState`, `sysName`, `sysLocation` and `ifPhysAddress` and learned how each reveals device type, status, names and MAC addresses. Attackers can leverage this information to fingerprint devices and target known vulnerabilities.
- Examined a `Malware.pcap` and detected the malware beaconing to domains like `nofbiatdominicana.com` and `kpai7ycr7jxqkilp.torexplorer.com`. The DNS responses resolved to a private IP (192.168.204.2) which indicated domain masquerading【408223297298984†L176-L190】. Packet analysis showed the host was a virtual machine (VMware MAC address), established an encrypted connection (SSL/TLS), and sent victims to a ransom payment URI `http://nofbiatdominicana.com/3ubc5pzotxyp0ui`【408223297298984†L195-L209】. I noted that malware uses encryption to evade inspection【408223297298984†L201-L204】.
- Registered a Shodan account and performed various searches. Queries for “default password” revealed numerous HP printers and nginx servers using default credentials, while “vnc”, “rdp” and “scada” searches returned devices with open remote‑access ports【408223297298984†L230-L274】. I learned that these services often run with default settings, leaving them vulnerable to takeover. Shodan can also find industrial control systems and unpatched SCADA devices, highlighting the danger of exposed critical infrastructure【408223297298984†L266-L283】.
- Reflected on how organizations can use Shodan defensively to inventory their own internet‑facing assets and remediate misconfigurations before adversaries discover them【408223297298984†L323-L330】.

## Findings
- **FTP update sessions are insecure**: Transfers used anonymous credentials over FTP, retrieving multiple files without encryption【408223297298984†L56-L60】.
- **SNMP v1 leaks device metadata**: Using the default `public` community string and outdated protocol allows attackers to enumerate devices via OIDs【408223297298984†L72-L96】.
- **Malware uses DNS and TLS to hide communications**: The C2 infrastructure resolved malicious domains to private IPs and used TLS to encrypt payloads【408223297298984†L176-L204】.
- **Default credentials and open services are widespread**: Shodan searches show many devices with default passwords or open VNC/RDP/SCADA ports【408223297298984†L230-L274】.

## Lessons Learned
- Always replace insecure protocols like FTP with secure alternatives (SFTP/FTPS) and enforce strong authentication【408223297298984†L56-L60】.
- Upgrade SNMP deployments to version 3 and change community strings from the defaults to reduce information leakage【408223297298984†L72-L96】.
- Threat actors hide C2 traffic within encrypted tunnels; monitoring DNS requests and certificate details can reveal malicious patterns【408223297298984†L176-L204】.
- Shodan is a powerful tool for both defenders and attackers; continuously monitor your own exposed services and remediate default credentials or open remote‑access ports【408223297298984†L230-L330】.

## Next Steps
- Configure secure update mechanisms for software (use HTTPS or signed updates).
- Harden network devices: disable SNMP v1, implement SNMPv3 and restrict SNMP access.
- Implement network traffic inspection solutions that can detect encrypted malware C2 communications.
- Regularly audit your organization’s internet exposure with Shodan or similar services and close or secure unnecessary services.
