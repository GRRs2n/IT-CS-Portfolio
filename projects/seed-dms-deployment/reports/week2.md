# Week 2 – Scaling and Load Balancer Preparation (ending 18 Jan 2026)

## Accomplishments
- Scaled the web tier from one to three nodes by provisioning two more EC2 servers.
- Deployed and validated SeedDMS on each web node, ensuring independent operation.
- Adjusted the DocumentRoot to allow access at the root URL without the `/seeddms` path and verified functionality via a browser.
- Set up a dedicated Ubuntu instance for the load balancer and installed HAProxy.

## Plans for Next Week
- Configure HAProxy backends, load balancing algorithm, and health checks.
- Implement failover logic and begin SSL/TLS configuration.

## Comments / Lessons Learned
Updating the DocumentRoot resolved redirection issues. Preparing the load balancer sets the foundation for high availability.
