# 10 · Tool and Code Analysis

> Module 10 of my Ethical Hacking / Penetration Testing course notes.
> A reference/cheat-sheet of the reconnaissance, enumeration, and
> vulnerability-scanning tools covered across the course.

## Table of Contents

- [Core Linux Distributions](#core-linux-distributions)
- [Reconnaissance](#reconnaissance)
- [Vulnerability Scanners](#vulnerability-scanners)

## Core Linux Distributions

**Kali Linux** — a Debian-based evolution of WHoppiX, WHAX, and BackTrack.
Offers live boots (CD/DVD/USB/PXE) and bare-metal installs; pre-packaged
with hundreds of tools organized by attack phase.

**Alternatives:** Parrot OS, BlackArch Linux, and BlackArch in a Docker
container.

## Reconnaissance

### Passive Reconnaissance (OSINT)

Relies strictly on publicly available information to profile targets
without directly sending packets or using active scanners.

#### DNS & Domain Infrastructure Analysis

| Tool | Purpose |
|---|---|
| `nslookup`, `host`, `dig` | Uncover DNS records, CNAME aliases, and underlying hosting infrastructure (e.g., mapping subdomains to third-party providers like GitHub Pages or CDNs). |
| `whois` | Queries domain registration records. |

> **Note:** EU GDPR protections significantly limit publicly visible
> registrant details (often obfuscated via privacy protection services).

**Key WHOIS fields:** Registrar, Name Servers, Expiry Dates, Domain
Status codes (e.g., `serverTransferProhibited`).

#### File Metadata Extraction

| Tool | Description |
|---|---|
| **ExifTool** | Command-line tool to extract EXIF metadata from digital media (JPEG, PNG, audio/video). High-value targets: camera make/model, OS/software build numbers, creation timestamps, and precise GPS coordinates. |
| **FOCA** (Fingerprinting Organization with Collected Archives) | Web and document analysis tool (PDF, MS Office, OpenOffice) that extracts EXIF data from site graphics and document properties to reveal internal usernames, network paths, and software versions. |

#### Subdomain & Entity Enumeration

**theHarvester** — automated reconnaissance tool that queries search
engines, PGP key servers, and public databases (Google, Bing, CRT.sh,
ThreatCrowd, VirusTotal, Netcraft, LinkedIn).

**Key command options:**

| Flag | Purpose |
|---|---|
| `-d <domain>` | Target domain/company name. |
| `-b <source>` | Data source (`google`, `pgp`, `linkedin`, `shodan`, or `all`). |
| `-l <limit>` | Limit total results returned. |
| `-c` | Perform DNS brute forcing. |
| `-n` | Run reverse DNS queries on discovered IP ranges. |

#### Internet-Connected Device Mapping

| Tool | Description |
|---|---|
| **Shodan** | Search engine for exposed internet-facing systems and IoT devices. CLI: `shodan stats <query>` (aggregate stats), `shodan host <IP>`, `shodan search <query>`, `shodan honeyscore <IP>` (checks if an IP is a honeypot). |
| **Censys** | University of Michigan tool for profiling public network infrastructure, SSL/TLS certificates, and protocol banners across the IPv4 space. |

#### Frameworks & Graphical Data Mining

| Tool | Description |
|---|---|
| **Maltego** | Node-based graphical link analysis tool. Uses Transforms (queries) executed against Entities (domains, email addresses, IPs, persons) from an Entity Palette to map complex external relationships. |
| **Recon-ng** | Modular, menu-driven CLI reconnaissance framework modeled after Metasploit. |

**Recon-ng key commands:**

```bash
show modules              # display available modules by category
                           # (Discovery, Exploitation, Import, Recon, Reporting)
keys list                 # manage required API tokens (Shodan, GitHub, Censys, etc.)
keys add
use <module_path>         # select a module (e.g. recon/hosts-hosts/resolve)
show info                 # view required parameters
set SOURCE <target>       # configure target parameters
run                       # execute the selected module
```

### Active Reconnaissance & Host Enumeration

Involves direct packet interaction with the target network, and carries a
risk of detection or scope violation.

#### Host & Service Discovery

**Nmap** — used for network sweeping, port discovery, and service
fingerprinting.

**Scope management:** limit internet-facing scans strictly to authorized
scopes to prevent unintended collateral scanning. Internal sweeps
typically target full subnets (e.g., `/24`).

#### SMB & Active Directory Enumeration

**Enum4linux** — a specialized wrapper tool for enumerating
Windows/Samba environments over SMB (ports 139/445).

**Dependencies:** `nmblookup`, `net`, `rpcclient`, `smbclient`, `polenum`, `ldapsearch`.

**High-value findings:**

- Workgroup/domain name details (via `nmblookup`)
- NetBIOS name table status (`<00>` Workstation, `<20>` File Server, `<1d>` Master Browser)
- Null session vulnerabilities (checking whether a connection succeeds with an empty username `''` and password `''`)
- Domain SIDs, password policies, RID range cycling (`500-550`, `1000-1050`), and default user accounts (`administrator`, `guest`, `krbtgt`)

## Vulnerability Scanners

### 1. General & Enterprise Vulnerability Scanners

Scan networks, operating systems, and endpoints to identify unpatched
software, misconfigurations, and known vulnerabilities.

| Scanner | Description |
|---|---|
| **OpenVAS** (Greenbone Networks) | Open-source network vulnerability scanner; includes a REST API for automation and continuous scheduling. Tasks are initiated via Task Wizard or Advanced Task Wizard (Scans → Tasks); schedules set under Configuration → Schedules. |
| **Nessus** (Tenable) | Commercial network vulnerability scanner offering continuous monitoring, compliance analysis, and configuration auditing. Cloud variant: **Tenable.io**. |
| **Nexpose** (Rapid7) | Enterprise scanner widely used in professional penetration testing; integrates with exploitation frameworks (e.g., Metasploit) and SIEM tools. |
| **Qualys** | Cloud-native vulnerability management and compliance suite, using lightweight cloud agents, virtual scanners, and network appliances for continuous monitoring and configuration auditing. |

### 2. Web Application & Targeted Exploitation Tools

#### SQLmap

**Purpose:** automated SQL injection (SQLi) enumeration and database
exploitation.

**Typical workflow:**

1. Capture a valid HTTP GET/POST request using an interception proxy (e.g., OWASP ZAP or Burp Suite).
2. Extract parameters and active session tokens (e.g., `PHPSESSID`, security level).

**Essential commands:**

```bash
# Enumerate databases
sqlmap -u "http://<TARGET_IP>/path/?id=1&Submit=Submit" \
       --cookie="PHPSESSID=<COOKIE_VALUE>" --dbs

# Dump database content
sqlmap -u "http://<TARGET_IP>/path/?id=1&Submit=Submit" \
       --cookie="PHPSESSID=<COOKIE_VALUE>" -D <DB_NAME> --dump-all
```

**Automated capabilities:** identifies injection techniques
(boolean-based blind, error-based, time-based, UNION-based), extracts
database tables, and cracks stored password hashes via dictionary
attacks.

#### Nikto

Open-source command-line web server scanner.

**Capabilities:** detects outdated server software, default
files/scripts, dangerous functions (e.g., exposed `phpinfo()`),
misconfigured headers (`X-Frame-Options`, `X-XSS-Protection`), and HTTP
method exposures (`TRACE`).

```bash
# Single host scan
nikto -host <TARGET_IP>

# Chained network discovery: Nmap → Nikto
nmap -p 80 10.1.1.0/24 -oG - | nikto -h -
```

#### OWASP Zed Attack Proxy (ZAP)

Open-source web application security scanner and active interception
proxy.

**Key features:**

- **Spider (Crawler)** — automatically discovers application endpoints starting from a seed URL.
- **Active Scanner** — tests endpoints for path traversal, XSS, and command injection.
- **Fuzzer & API Integration** — automates payload delivery and CI/CD security checks.

#### w3af

Extensible Python-based web application attack and audit framework, with
modular plugins categorized by function: `crawl` (content discovery),
`audit` (vulnerability identification — SQLi, XSS, LFI/RFI, buffer
overflows), `bruteforce`, `evasion`, `infrastructure`, `auth`.

**Basic console workflow:**

```text
w3af>>> plugins
w3af/plugins>>> audit sqli
w3af/plugins>>> back
w3af>>> target
w3af/config:target>>> set target http://<TARGET_IP>
w3af/config:target>>> back
w3af>>> start
```

#### Directory Brute-Forcing Tools

**DirBuster** — legacy Java GUI tool for brute-forcing hidden directories
and files using wordlists *(now integrated into OWASP ZAP)*.

**Modern alternatives:** `gobuster`, `ffuf` (high-speed command-line
tools).

### 3. Specialized & Domain-Specific Scanners

| Tool | Target Domain / Use Case |
|---|---|
| **Brakeman** | Static code analysis (SAST) specifically for Ruby on Rails applications. |
| **SCAP Scanners** | Compliance and security policy testing using the Security Content Automation Protocol. |
| **Wapiti** | Black-box web application vulnerability scanner (audits GET/POST parameters). |
| **Scout Suite** | Multi-cloud security auditing tool (AWS, Azure, GCP). |
| **WPScan** | Vulnerability scanner focused exclusively on WordPress core, plugins, and themes. |

---

**Previous:** [09 · Reporting and Communication](09-reporting-and-communication.md) · **Back to:** [README](README.md)
