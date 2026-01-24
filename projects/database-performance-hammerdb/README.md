# Database Performance Testing with HammerDB

## Overview
This project is based on Lab 2.1 and uses HammerDB to measure transactions per minute (TPM) for MySQL and MariaDB under different load levels. The objective is to determine which database performs better under stress.

## What I Did
- Installed HammerDB on a Windows 10 VM and configured it with the TPC C benchmark.
- Built a test schema and executed transactions against a MySQL server using a single virtual user.
- Repeated the test for MariaDB and then increased the virtual user count to eight for both databases to compare scalability.
- Monitored TPM results and CPU usage on the database servers during the tests.

## Results
- MySQL scaled to eight users with a total throughput of ~725,340 TPM and ~90,668 TPM per user【597933275880089†L240-L260】.
- MariaDB achieved ~231,204 TPM per user with a single user but dropped to ~69,342 TPM per user at eight users【597933275880089†L246-L253】.
- MySQL therefore delivered higher throughput at high concurrency, whereas MariaDB’s performance declined more sharply.
- Attempts to allocate additional CPU or RAM to MariaDB were constrained, so no further scaling was tested【597933275880089†L264-L280】.

## Lessons Learned
- Database performance does not scale linearly; lock contention and resource limits reduce per-user throughput as concurrency rises.
- MySQL proved more resilient to increased concurrency and is preferable for workloads requiring high TPM【597933275880089†L254-L263】.
- CPU and memory allocation constraints in virtual environments can limit performance improvements; ensure virtualization settings allow scaling.

## Next Steps
- Investigate performance tuning (caching, indexing) for MariaDB to improve scalability.
- Compare additional databases (PostgreSQL, SQLite) under HammerDB.
- Automate benchmarking via scripts for reproducible testing.
