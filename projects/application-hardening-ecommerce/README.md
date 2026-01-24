# Application Hardening: e\u202fCommerce Site

## Overview
This project documents the security assessment and hardening of a vulnerable e\u2011commerce demo. Using OWASP ZAP and manual exploration, we discovered serious web and configuration weaknesses. The goal of the project is to demonstrate application penetration testing, vulnerability triage and recommended remediations.

## What I Did
- Ran an active OWASP ZAP scan against the demo site to identify injection and configuration flaws. ZAP reported 8 high\u2011severity cross\u2011site scripting (XSS) vulnerabilities along with medium and low issues such as missing CSRF tokens, missing Content\u2011Security\u2011Policy headers, outdated JavaScript libraries, insecure cookie attributes and cross\u2011domain script inclusion【602211062706724\u2020L10-L29】.
- Manually browsed the site to evaluate functionality and security posture. I noted that the storefront offered non\u2011hammer items, login and checkout pages were served over plain HTTP rather than HTTPS, and there was no visible privacy policy or strong password enforcement【602211062706724\u2020L42-L86】.
- Investigated the associated FTP server. Anonymous login was enabled and I could download database backups and configuration files (e.g. `db.zip`, `hammer.sql` and `db-creds.txt`) which contained sensitive customer data and credentials【602211062706724\u2020L42-L86】.
- Performed SSL/TLS analysis using SSL Labs on external domains for comparison. Sites like badssl.com and amazon.com received a grade B because they still support TLS\u00a01.0/1.1 and lacked strict downgrade protections【602211062706724\u2020L87-L109】. These findings underscore the need to disable legacy protocols and adopt modern cipher suites.

## Findings
- Persistent and reflected XSS vulnerabilities in multiple pages.
- Missing anti\u2011CSRF tokens on forms, absent Content\u2011Security\u2011Policy headers and insecure cookies (no HttpOnly or Secure flags)【602211062706724\u2020L10-L29】.
- Sensitive files exposed via anonymous FTP login, including database backups and configuration secrets【602211062706724\u2020L42-L86】.
- No privacy notice or strong password requirements; weak identity and access management.
- Reliance on outdated TLS versions and absence of protections against downgrade attacks【602211062706724\u2020L87-L109】.

## Lessons Learned
- Automated scanners like OWASP ZAP are effective at uncovering cross\u2011site scripting and missing security headers. However, manual exploration is required to identify business logic flaws and misconfigurations in non\u2011HTTP services【602211062706724\u2020L42-L86】.
- Sites must implement anti\u2011CSRF tokens, Content\u2011Security\u2011Policy, and secure cookie attributes to mitigate common web vulnerabilities【602211062706724\u2020L10-L29】.
- Sensitive backups and credentials should never be publicly accessible; restrict FTP access or replace it with secure file transfer methods.
- TLS configurations should disable outdated protocols and enable features like strict transport security and forward secrecy【602211062706724\u2020L87-L109】.

## Next Steps
- Fix all identified vulnerabilities: implement anti\u2011CSRF tokens, define a Content\u2011Security\u2011Policy, update outdated JavaScript libraries, and set Secure/HttpOnly flags on cookies.
- Migrate the site to HTTPS, enforce strong password policies and publish a clear privacy notice.
- Remove anonymous FTP or secure it with authentication and encryption; rotate any leaked credentials.
- Disable TLS\u00a01.0/1.1 and configure modern cipher suites and HSTS.
- Re\u2011run OWASP ZAP and perform a full security review after remediation.
