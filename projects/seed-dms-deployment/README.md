# SeedDMS Multi‑Tier Cloud Deployment

This project documents the design, implementation, and improvement of a multi‑tier SeedDMS deployment in the cloud. SeedDMS is an open‑source document management system. The goal was to build a robust, scalable environment that separates application and database tiers and introduces load balancing and HTTPS.

## Architecture

The deployment uses a three‑tier architecture:

- **Web tier:** Multiple EC2 instances running Apache, PHP, and SeedDMS.
- **Database tier:** A dedicated MariaDB instance to store SeedDMS data.
- **Load balancer:** An HAProxy instance acting as a reverse proxy to distribute traffic across web nodes and terminate TLS.

## Key Features

- Automated environment setup with separate web and database nodes.
- Horizontal scaling of the web tier from one to three nodes.
- Load balancing with health checks and SSL termination via HAProxy.
- Self‑signed certificate generation and configuration for HTTPS.
- Ongoing performance tuning and routing validation.

## Project Reports

Progress was tracked via weekly status reports:

- [Week 1 – Initial Environment Setup](reports/week1.md)
- [Week 2 – Scaling and Load Balancer Preparation](reports/week2.md)
- [Week 3 – SSL and HAProxy Configuration](reports/week3.md)

## Lessons Learned

Separating tiers improves scalability and security. Document root configuration and HAProxy settings are critical for proper application delivery. TLS setup requires correct certificate formatting. Iterative testing and validation are essential when scaling and introducing load balancing.
