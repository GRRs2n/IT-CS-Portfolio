# Web Server Load Testing with Apache JMeter

## Overview
This project replicates Lab 1.2 from CTI3561. It uses Apache JMeter to perform load testing across multiple web server stacks, including static pages, dynamic CMS pages, and plain HTTP requests. The goal is to measure performance metrics and identify bottlenecks.

## What I Did
- Set up multiple virtual machines with Apache, Lighttpd, Nginx, and database backends; verified network connectivity across HTTP and DB subnets.
- Installed Apache JMeter on a Windows 10 VM. Built a test plan with 64 threads, retrieving embedded resources and adding response time and summary listeners.
- Ran the test plan against 18 scenarios: a PHP Info Page, a plain HTTP request, and Wolf CMS on SQLite, MariaDB, PostgreSQL, and MySQL.
- Collected metrics such as average response time, max response time, throughput, and data rate; aggregated the results into a CSV file.

## Results
- The PHP Info Page had the lowest average response time (~4ms)【54850827996714†L254-L259】.
- The plain HTTP request achieved the best throughput (~62 requests/sec) and highest data rate (~61,836 KB/s)【54850827996714†L260-L278】.
- Wolf CMS on PostgreSQL showed the highest latency and lowest throughput (~4.83 requests/sec)【54850827996714†L271-L283】.
- These results demonstrate that simpler pages and optimized stacks handle concurrent load better, whereas complex CMS apps require tuning and scaling.

## Lessons Learned
- Establishing a baseline through controlled load testing allows objective comparisons across stacks.
- System bottlenecks vary by stack: database choice, CMS overhead, and web server efficiency all impact performance.
- JMeter is effective for synthetic load testing but should be complemented with real-world monitoring to capture geographic latency, caching, and user behaviour【54850827996714†L312-L323】.

## Next Steps
- Implement caching and tuning for CMS-based sites to improve performance.
- Explore distributed JMeter testing to emulate larger user loads and geographic distribution.
- Integrate JMeter results into CI/CD pipelines for regression performance testing.
