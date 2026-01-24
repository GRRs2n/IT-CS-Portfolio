# Security Policies and Plan

This folder consolidates formal security policies and an overarching security plan for Snowbe Online. The policies include Patch Management (SP ‑26), Secure Development Life Cycle (SP ‑25), Security Maturity (SP ‑27), and a comprehensive Security Plan. Each document defines roles, responsibilities, and practices to establish a consistent and compliant security program.

## Patch Management Policy (SP ‑26)

- **Purpose:** Provide a structured process for identifying, evaluating, approving, and applying software updates to reduce vulnerabilities【669906185097596†L39-L44】.
- **Scope:** Applies to all hardware, software, operating systems, and network devices managed by Snowbe Online【669906185097596†L45-L53】.
- **Roles & Responsibilities:** CISO oversees the program; system owners prioritize critical systems; network admin applies patches; end users report issues【669906185097596†L64-L73】.
- **Policy:** Regularly monitor vendor advisories; evaluate patches for impact; apply critical patches within 30 days; test updates in a staging environment; maintain an inventory and schedule of updates【669906185097596†L75-L96】.
- **Exceptions & Enforcement:** Documented exceptions require CISO approval. Failure to comply may lead to disciplinary action【669906185097596†L97-L103】.

## SDLC Policy (SP ‑25)

- **Purpose:** Establish a structured framework for designing, developing, testing, deploying and maintaining software to ensure security is integrated into each SDLC phase【750876574851806†L39-L46】.
- **Scope:** Applies to in‑house and third‑party software across AWS cloud, on‑premises servers and integrations【750876574851806†L49-L56】.
- **Roles:** Development team implements controls; IT security conducts risk assessments; compliance officer ensures regulatory requirements【750876574851806†L68-L74】.
- **Policy:** Security integrated into each phase: planning (document risks), design (threat modelling), development (secure coding), testing (SAST/DAST), deployment (configuration hardening), maintenance (vulnerability management)【750876574851806†L82-L100】.
- **Exceptions:** Deviations require written justification approved by the CISO【750876574851806†L102-L105】.

## Security Maturity Policy (SP ‑27)

- **Purpose:** Provide a structured approach to assessing and improving cybersecurity capabilities【146850233060913†L40-L43】.
- **Scope:** Applies to Snowbe Online’s IT operations, employee training and incident response planning【146850233060913†L44-L51】.
- **Roles:** CISO oversees assessments; IT security team tracks progress and implements controls【146850233060913†L68-L73】.
- **Maturity Levels:** Defines levels from Initial (informal processes) to Optimized (security embedded into culture). Annual assessments identify gaps and drive continuous improvement【146850233060913†L75-L97】.
- **Ongoing Improvement:** Requires annual assessments and continuous training to build a security‑focused culture【146850233060913†L98-L101】.

## Security Plan (Version 1.0 – March 2025)

- **Introduction:** Outlines security controls, processes, and responsibilities to protect Snowbe Online’s assets and comply with PCI DSS and NIST SP 800‑53【60749163247912†L33-L47】.
- **Scope:** Applies to all employees, contractors and vendors interacting with AWS, on‑premises servers, desktops/laptops, and customer/financial data【60749163247912†L49-L65】.
- **Roles & Responsibilities:** Specifies duties of the CISO, IT security manager, network administrators, developers and end users【60749163247912†L78-L104】.
- **Policies:** Integrates sub‑policies such as SDLC (SP‑25), patch management (SP‑26) and security maturity (SP‑27) into a cohesive program【60749163247912†L109-L184】.

## Lessons Learned

- Well‑documented policies increase clarity in roles, responsibilities and procedures.
- Aligning policies with industry standards (NIST, PCI DSS) provides a strong compliance foundation.
- Regular reviews and updates are necessary to accommodate new threats and technologies.
- Integrating patch management, SDLC and maturity models creates a cohesive security program.

## Next Steps

- Continue refining these policies based on organisational changes and emerging regulations.
- Implement automated compliance monitoring and reporting tools.
- Conduct regular training and security assessments to ensure adherence.
