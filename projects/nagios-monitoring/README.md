# Nagios Monitoring & SNMP Setup

This project documents my experience deploying and configuring Nagios XI to monitor a small lab environment. I built a test network, enabled SNMP on multiple hosts, added service checks, and generated load to observe how Nagios collected and alerted on metrics.

## What I Did

- Provisioned a Nagios XI instance with dual network adapters to monitor hosts on both the management and production networks.
- Installed and configured SNMP on six servers (Linux and Windows), using secure SNMP v3 where possible and defining read‑only community strings.
- Added each host to Nagios XI and created service checks for CPU, memory, disk usage and network metrics.
- Used Apache JMeter to generate load on the application servers to see how Nagios captured CPU spikes and resource consumption.
- Tuned notification thresholds and ensured that SNMP traffic remained within the local subnet.

## Key Findings & Lessons

- Continuous monitoring helps build a baseline of system behaviour and makes it easier to detect anomalies.
- SNMP v3 is the only version that encrypts data; always use SNMP v3 and restrict write strings to trusted hosts.
- Monitoring tools themselves consume resources and can cause minor spikes; checks and polling intervals should be tuned to minimise overhead.

## Next Steps

- Migrate all devices to SNMP v3 and remove insecure community strings.
- Add application-specific checks and logs to improve visibility.
- Integrate alerting with email or messaging platforms for faster incident response.
- Combine internal monitoring with external tools (like Site24x7) to gain a full picture of service health.
