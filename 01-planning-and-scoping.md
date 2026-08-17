# 01 · Planning and Scoping a Penetration Test

> Module 1 of my Ethical Hacking / Penetration Testing course notes.
> Covers governance, risk, and compliance (GRC) basics, the legal agreements
> that define an engagement, and the rules that keep a test authorized and
> ethical.

## Table of Contents

- [Governance, Risk & Compliance (GRC)](#governance-risk--compliance-grc)
- [Legal Concepts & Agreements](#legal-concepts--agreements)
- [Scoping and Customer Requirements](#scoping-and-customer-requirements)
- [Testing Strategies](#testing-strategies)
- [Ethical & Operational Standards](#ethical--operational-standards)
- [Personal Code of Ethical Conduct](#personal-code-of-ethical-conduct)

## Governance, Risk & Compliance (GRC)

Before any technical work starts, a penetration test has to fit inside the
regulatory and legal environment the client operates in.

### Regulatory Compliance Considerations

| Regulation / Standard | Description |
|---|---|
| **GDPR** (General Data Protection Regulation) | Strengthens and unifies data protection for individuals within the European Union. |
| **NIST SP 800-57** | Guidelines for encryption key management. |
| **PCI DSS** (Payment Card Industry Data Security Standard) | Secures the processing of credit card and other digital payments. |
| **GLBA** (Gramm-Leach-Bliley Act) | Applies to all financial services organizations, regardless of size. |
| **HIPAA** (Health Insurance Portability and Accountability Act) | Safeguards electronic health information. |

## Legal Concepts & Agreements

| Agreement / Term | Description |
|---|---|
| **SLA** (Service-Level Agreement) | Documents the minimum and maximum performance expectations of the penetration test service. |
| **Confidentiality Agreement** | Defines how sensitive data discovered during testing (e.g., credentials) must be communicated and handled. |
| **Disclaimer** | A statement clarifying limits of liability, e.g., *"The penetration test report cannot and does not protect against personal or business loss resulting from the test agreement."* |
| **NDA** (Non-Disclosure Agreement) | Defines confidential material, knowledge, and information that must not be disclosed to outside parties. |

## Scoping and Customer Requirements

### Rules of Engagement (RoE)

The Rules of Engagement document specifies the conditions under which the
penetration test will be conducted, for example:

- Testing timeline
- Physical/network location of testing
- Allowed time windows for testing

### Target List and In-Scope Assets

Before testing begins, identify all systems, networks, and applications
that are:

- **In scope** — explicitly authorized for testing
- **Out of scope** — explicitly excluded from testing

## Testing Strategies

| Strategy | Also Known As | Description |
|---|---|---|
| **Unknown Environment Testing** | Black-box testing | Tester has no prior knowledge of the target environment. |
| **Known Environment Testing** | White-box testing | Tester is given full knowledge of the target environment (source code, network diagrams, credentials, etc.). |

## Ethical & Operational Standards

| Requirement / Action | Description |
|---|---|
| Background checks of penetration testing teams | Vet the credentials and skills of individuals performing the test. |
| Adherence to the specific scope of engagement | Maintain a defined list of applications, systems, or networks to be tested. |
| Limiting invasiveness based on scope | Specify tools and attack techniques that could be disruptive to the client's systems. |
| Limiting the use of tools in a particular test | Explicitly allow or disallow specific testing tools. |
| Identification and immediate reporting of criminal activity | Report any evidence that a system or network was already compromised prior to the engagement. |

## Personal Code of Ethical Conduct

**Objective:** To establish a foundational set of principles that govern
professional behavior, technical practice, and moral obligations as an
ethical hacker and IT professional.

### The Ten Principles of Conduct

1. **Strict Adherence to Authorization** — Never perform testing, scanning, or penetration activity without explicit, written permission from the system or network owner.
2. **Protection of Human Life and Safety** — Prioritize the physical safety and well-being of individuals; ensure technical actions do not disrupt critical infrastructure or life-saving systems.
3. **Preservation of Data Privacy** — Treat all information uncovered during an engagement as strictly confidential; never access or disclose sensitive data beyond the authorized scope.
4. **Commitment to Integrity and Honesty** — Provide truthful, accurate, and complete reports of findings, never exaggerating a threat for personal gain or hiding a vulnerability.
5. **Avoidance of Conflict of Interest** — Remain impartial and objective in assessments; disclose any potential conflicts of interest to clients or employers.
6. **Limitation of Impact** — Use the least invasive techniques possible so testing does not cause system crashes, unintended data loss, or denial of service.
7. **Immediate Reporting of Critical Risks** — Report any zero-day or critical vulnerabilities that pose an immediate and severe risk to the appropriate stakeholders without delay.
8. **Respect for Intellectual Property** — Never steal, copy, or misappropriate the code, scripts, or intellectual output of others; respect all software licensing agreements.
9. **Continuous Competence** — Stay current with evolving threats and technologies to ensure security advice is based on accurate, modern standards.
10. **Social Responsibility** — Use technical skills to contribute to a safer digital society, and consider the social consequences of the scripts written and systems designed.

### Commitment Statement

> By committing to this code, an ethical hacker acknowledges that these
> skills carry significant responsibility, and pledges to uphold these ten
> principles to maintain the trust of peers, clients, and the public.

---

**Previous:** — · **Next:** [02 · Intro to Ethical Hacking and Pentesting](02-intro-to-ethical-hacking.md)
