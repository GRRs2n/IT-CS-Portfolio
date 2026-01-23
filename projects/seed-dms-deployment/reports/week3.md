# Week 3 – SSL and HAProxy Configuration (ending 25 Jan 2026)

## Accomplishments
- Configured HAProxy as a secure reverse proxy for SeedDMS.
- Generated a self‑signed 2048‑bit RSA certificate, combined it into a PEM file, and configured HAProxy to terminate TLS on port 443.
- Verified the HAProxy service status and confirmed it listens on ports 80 and 443.
- Successfully accessed the application over HTTPS from a client browser.

## Plans for Next Week
- Fine‑tune load balancing logic and routing behaviour across the three SeedDMS web servers.
- Validate performance and failover under load.
- Explore additional tuning for stability and throughput.

## Comments / Lessons Learned
Correct certificate formatting (PEM) is critical for HAProxy. Establishing HTTPS improved security and paves the way for production readiness.
