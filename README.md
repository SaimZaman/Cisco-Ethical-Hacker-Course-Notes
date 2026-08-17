# Ethical Hacking & Penetration Testing — Course Notes

Personal study notes from a Cisco NetAcad Ethical Hacker / Penetration
Testing course, cleaned up and organized into readable Markdown for
reference and revision.

> ⚠️ **Educational use only.** These notes describe tools and techniques
> for security research and penetration testing. Only use them against
> systems you own or are explicitly authorized to test. See
> [Module 1](01-planning-and-scoping.md) for the ethics and legal
> framework behind authorized testing.

## 📚 Modules

| # | Module | Summary |
|---|---|---|
| 01 | [Planning and Scoping a Penetration Test](01-planning-and-scoping.md) | GRC, legal agreements, rules of engagement, code of ethics. |
| 02 | [Intro to Ethical Hacking and Pentesting](02-intro-to-ethical-hacking.md) | Testing types/methods, industry methodologies, core Kali Linux commands. |
| 03 | [Information Gathering and Vulnerability Scanning](03-information-gathering-and-vulnerability-scanning.md) | Passive/active recon, OSINT, Nmap, enumeration, Scapy, vulnerability scanning. |
| 04 | [Social Engineering Attacks](04-social-engineering-attacks.md) | Phishing variants, physical attacks, social engineering tools. |
| 05 | [Exploiting Wired and Wireless Networks](05-exploiting-wired-and-wireless-networks.md) | SMB/SNMP/SMTP/FTP exploits, Kerberos attacks, DoS/DDoS, VLAN hopping, wireless attacks. |
| 06 | [Exploiting Application-Based Vulnerabilities](06-exploiting-application-based-vulnerabilities.md) | HTTP/session fundamentals, SQLi, XSS, CSRF, clickjacking, file inclusion. |
| 07 | [Mobile, IoT, and Cloud Security](07-mobile-iot-and-cloud-security.md) | Cloud attack vectors, mobile device attacks, IoT protocols, VM/container security. |
| 08 | [Performing Post-Exploitation Techniques](08-post-exploitation-techniques.md) | Persistence, C2 frameworks, lateral movement, living off the land, covering tracks. |
| 09 | [Reporting and Communication](09-reporting-and-communication.md) | Report structure, risk scoring, remediation control frameworks. |
| 10 | [Tool and Code Analysis](10-tool-and-code-analysis.md) | Cheat sheet of recon tools and vulnerability scanners covered in the course. |

## 🗂️ Structure

```text
.
├── README.md
├── 01-planning-and-scoping.md
├── 02-intro-to-ethical-hacking.md
├── 03-information-gathering-and-vulnerability-scanning.md
├── 04-social-engineering-attacks.md
├── 05-exploiting-wired-and-wireless-networks.md
├── 06-exploiting-application-based-vulnerabilities.md
├── 07-mobile-iot-and-cloud-security.md
├── 08-post-exploitation-techniques.md
├── 09-reporting-and-communication.md
├── 10-tool-and-code-analysis.md
└── assets/
    └── scapy-terminal-demo.png
```

## 🧭 How These Notes Are Organized

Each module file follows the same layout:

- A short intro describing what the module covers.
- A table of contents linking to each section.
- Concept explanations in prose, with tables for comparisons and
  reference data.
- Fenced code blocks for commands, syntax, and terminal examples.
- A footer linking to the previous/next module for easy sequential
  reading.

## 📝 Notes on Content

- These notes were originally taken while working through the course and
  have since been corrected, restructured, and reformatted for clarity
  and easier GitHub reading.
- Any personal identifiers from the original notes have been removed or
  replaced with generic placeholders.
- Commands and tool syntax reflect what was taught in the course; always
  check a tool's own documentation (`--help` / `man`) for the current,
  authoritative syntax before running it.

---

*Feel free to fork this repo for your own study notes.*
