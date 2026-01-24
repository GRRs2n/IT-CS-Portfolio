# Site24x7 External Monitoring

This project demonstrates how to use Site24x7 for external monitoring of web applications and servers. Site24x7 provides a user‑perspective view by checking availability, response time, DNS resolution and SSL from multiple global locations.

## What I Did

- Signed up for Site24x7 and created a full page monitor for my lab website, which measures DNS resolution, network latency, SSL status and page load times from various geographic locations.
- Installed the Site24x7 server monitoring agent on multiple Linux and Windows hosts to collect CPU, memory, disk and process metrics.
- Configured alert thresholds for CPU usage, disk utilization and response time, and tested alerting functionality.
- Compared external Site24x7 metrics with internal monitors such as Nagios to understand differences and benefits.

## Key Findings & Lessons

- External monitoring offers insights from outside the network, detecting DNS or internet routing issues that internal monitors cannot see.
- Combining internal tools like Nagios with external monitoring provides a more complete picture of service health and ensures alerts are triggered even if the internal network is down.
- Agents provide detailed host‑level metrics, while website monitors give real end‑user response times; both are valuable.

## Next Steps

- Add monitors for API endpoints and increase the number of test locations to capture global performance variations.
- Create custom dashboards and integrate alerts with collaboration tools such as Slack or Microsoft Teams.
- Evaluate additional external monitoring providers and compare features.
