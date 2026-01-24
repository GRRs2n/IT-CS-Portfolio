# Performance and Monitoring Analysis

This project consolidates lessons learned across multiple labs in my CTI3561 course. It synthesises insights from load testing, database benchmarking, SNMP-based monitoring and external monitoring, highlighting how to interpret performance results and why different tools produce different metrics.

## Overview

- **Load Testing (JMeter)** – A JMeter test plan with 64 threads simulated users hitting static pages, dynamic CMS pages and a plain HTTP request. Results showed simple pages scale better; throughput varied widely between scenarios and back‑end databases【285630800421541†L43-L71】.
- **Database Benchmarking (HammerDB)** – HammerDB compared MySQL and MariaDB transaction throughput under varying concurrency. MySQL sustained higher total throughput at high concurrency while MariaDB delivered higher per‑user throughput at low concurrency【285630800421541†L92-L117】.
- **Continuous Monitoring (Nagios)** – Setting up Nagios with SNMP v3 across multiple hosts provided baseline metrics and alerts. Configuring services, tuning thresholds and understanding the monitoring overhead were key tasks【285630800421541†L153-L172】.
- **External Monitoring (Site24x7)** – Site24x7 full‑page load monitoring offered an outside‑in perspective on uptime and performance, complementing internal metrics【285630800421541†L153-L172】.

## Key Insights

- **Context matters more than thread counts.** Throughput and latency depend on server CPU, disk, network and database efficiency. Merely increasing JMeter threads doesn’t ensure higher performance; underlying resources must scale too【285630800421541†L43-L71】.
- **Different tools measure different things.** JMeter exercises full web stacks at HTTP level while HammerDB targets database transactions. Their metrics aren’t directly comparable; each tool must be interpreted within its domain【285630800421541†L92-L117】.
- **Baseline vs continuous monitoring.** JMeter and HammerDB provide point‑in‑time baselines. For ongoing visibility, agent‑based tools like Nagios and external monitors like Site24x7 are needed; these generate less load and offer persistent alerts【285630800421541†L153-L172】.
- **Observability comes with overhead.** Monitoring agents consume CPU, memory and network; SNMP v3 improves security but adds encryption overhead. Balance data granularity with resource impact and consider agentless options where appropriate【285630800421541†L153-L172】.
- **Always validate results.** Repeat tests, correlate metrics from multiple tools and investigate anomalies. Differences between tests often reveal misconfigurations or bottlenecks beyond thread counts【285630800421541†L43-L71】.

## Next Steps

To further develop these insights I plan to:

- Automate baseline tests and integrate their results into Nagios for trend analysis.
- Refine load generation to mimic real user behaviour, including think times and varied workloads.
- Experiment with agentless monitoring protocols and compare overhead against SNMP and cloud agents.
