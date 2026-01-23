# Week 1 – Initial Environment Setup (ending 11 Jan 2026)

## Accomplishments
- Established initial cloud environment for a multi-tier SeedDMS deployment by provisioning two EC2 instances to separate the web and database layers.
- Configured the web tier with Apache, PHP and installed SeedDMS.
- Installed MariaDB on a dedicated database server and tested connectivity between the tiers.
- Secured the SeedDMS installation by removing installation tools.

## Plans for Next Week
- Add additional web nodes for scaling.
- Deploy a load balancer (HAProxy) instance.
- Prepare for load balancing and high availability.

## Comments / Lessons Learned
Separating the web and database tiers improved scalability and security. Testing connectivity early ensured smooth deployment and removing the installation tools reduced attack surface.
