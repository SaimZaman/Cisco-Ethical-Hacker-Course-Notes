# 09 · Reporting and Communication

> Module 9 of my Ethical Hacking / Penetration Testing course notes.
> Covers how to write and deliver an effective pentest report, and the
> four control frameworks used for remediation guidance.

## Table of Contents

- [Important Components of a Written Report](#important-components-of-a-written-report)
- [Analyzing Findings, Security Controls, and Remediation](#analyzing-findings-security-controls-and-remediation)
- [The 4 Control Frameworks](#the-4-control-frameworks)

## Important Components of a Written Report

### Audience-Tailored Communication

Adapt tone and technical depth to the reader:

- **Executive Summary** — high-level business risk, written for the C-suite.
- **Technical Findings** — detailed findings for IT/development teams to remediate.

**Tool findings & validation:** automated scanner results (e.g., Nessus)
must be manually verified and correlated with business context to
eliminate false positives and false negatives.

### Key Report Sections

Typically includes: **Executive Summary, Scope Details, Methodology,
Findings, Remediation, Conclusion, and Appendix.**

### Risk Scoring Frameworks

| Framework | Description |
|---|---|
| **CVE** | A list of known, cataloged vulnerabilities with standard IDs. |
| **CVSS** | A standard 0–10 severity score, using Base, Temporal, and Environmental metric groups — the Environmental group tailors the rating to a specific organization's threat surface. |

### Control & Secure Distribution

- Treat reports as highly classified; distribute strictly on a need-to-know basis.
- Keep a physical tracking log (recipient name, copy ID, date), and securely delete electronic copies post-delivery.

### Real-Time Documentation

Take notes, screenshots, and video evidence continuously during testing,
rather than waiting until the end. Centralized management tools (like
Dradis) help ingest and organize multi-tool output.

### Root Cause Analysis

Go beyond surface-level scanner output to identify underlying systemic
issues — for example, conducting staff interviews to find out why
firewalls were altered or old servers were left un-decommissioned.

## Analyzing Findings, Security Controls, and Remediation

Penetration testing goes beyond finding vulnerabilities — it requires
providing actionable, expert guidance to help clients fix issues.

- **Proportionate Risk** — recommendations should include relative risk ratings to help clients prioritize remediation.
- The engagement transitions into a "helping relationship" focused on risk reduction.
- **Control Types** — remediation strategies fall into four categories: Technical, Administrative, Operational, and Physical.

## The 4 Control Frameworks

### 1. Technical Controls

Technology-based measures used to directly reduce vulnerabilities.

**Network Segmentation & Microsegmentation**

- Traditional VLAN/subnet-based segmentation relying on central firewalls is inefficient for high "east-west" (internal server-to-server or VM-to-VM) traffic.
- **Microsegmentation** applies granular control at the individual VM or container level, regardless of physical location or VLAN.
- **Zero-Trust Model** — enforces strict, application-aware policies where no user or application can communicate unless explicitly permitted.

**Key practices:**

- System hardening
- Multi-Factor Authentication (MFA)
- Password encryption
- Process-level remediation
- Patch management
- Key rotation & certificate management
- Secrets management solutions

### 2. Administrative Controls

Policies, rules, framework standards, or organizational structures
designed to guide behavior and enforce security.

- **RBAC** (Role-Based Access Control) — defining access based on job roles rather than individuals.
- **S-SDLC** (Secure Software Development Life Cycle) — embedding security requirements throughout the development process.
- **Minimum Password Requirements** — standardized rules for password complexity and age.
- **Policies & Procedures** — formal documentation establishing operational rules and compliance expectations.

### 3. Operational Controls

Day-to-day security measures executed by people (rather than machines) to
enforce management policies.

**User Training & Awareness**

- Uses education to reduce susceptibility to social engineering attacks.
- Guided by standards such as **NIST SP 800-50** (Building an Information Technology Security Awareness and Training Program).
- **Awareness vs. Education** — awareness reminds users of expected behaviors, while training/education teaches specific technical and decision-making skills.

**Other key operational controls:**

| Control | Purpose |
|---|---|
| **Job Rotation** | Prevents single points of failure and deters insider fraud. |
| **Mandatory Vacations** | Helps expose ongoing unauthorized activities or procedural gaps. |
| **Time-of-Day Restrictions** | Regulates when systems or resources can be accessed. |

### 4. Physical Controls

Tangible measures to prevent, deter, or detect physical access to
sensitive facilities, hardware, or materials.

| Control | Purpose |
|---|---|
| **Access Control Vestibules (Mantraps)** | Interlocking dual-door systems that prevent tailgating and unauthorized access. |
| **Biometric Controls** | Physical verification (fingerprint, retina scanners) for secure entry points. |
| **Video Surveillance (CCTV)** | Continuous monitoring and recording to deter intruders and aid incident investigation. |

---

**Previous:** [08 · Performing Post-Exploitation Techniques](08-post-exploitation-techniques.md) · **Next:** [10 · Tool and Code Analysis](10-tool-and-code-analysis.md)
