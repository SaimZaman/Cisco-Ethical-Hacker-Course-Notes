# 07 · Mobile, IoT, and Cloud Security

> Module 7 of my Ethical Hacking / Penetration Testing course notes.
> Covers cloud attack vectors, mobile device attacks, IoT protocol
> weaknesses, virtualization risks, and container security.

## Table of Contents

- [Attack Vectors on Cloud Technologies](#attack-vectors-and-attacks-on-cloud-technologies)
- [Attacking Mobile Devices](#attacking-mobile-devices)
- [Attacking Internet of Things (IoT) Devices](#attacking-internet-of-things-iot-devices)
- [Management Interfaces (IPMI & BMC)](#management-interfaces-ipmi--bmc)
- [Virtual Machine (VM) Vulnerabilities](#virtual-machine-vm-vulnerabilities)
- [Containers & Security Tools](#containers--security-tools)

## Attack Vectors and Attacks on Cloud Technologies

### Overview

Cloud environments are complex and easy to misconfigure, due to a
shortage of experienced cloud engineers and untracked, out-of-date
software.

**Deployment models:**

| Model | Description |
|---|---|
| **Public** | Open to everyone. |
| **Private** | Dedicated to one organization. |
| **Community** | Shared by several organizations. |
| **Hybrid** | A mix of two or more models (including on-premises). |

**Three basic service models:**

1. **IaaS** (Infrastructure as a Service) — raw computing infrastructure like virtual machines and storage.
2. **PaaS** (Platform as a Service) — a platform/environment for developers to build and test applications.
3. **SaaS** (Software as a Service) — ready-to-use software on a subscription basis (e.g., Office 365, web games).

### Credential Harvesting

Gathering and stealing usernames, passwords, tokens, or PINs.

**Method:** phishing emails linking to fake, look-alike login pages (e.g.,
a fake Google or social media login).

**Mitigation:** Multi-Factor Authentication (MFA) is the best defense.

### Privilege Escalation

Exploiting software bugs or flaws to gain higher access than intended.

- **Vertical Escalation** — a regular user gains administrative/root control.
- **Horizontal Escalation** — a user gains access to another user's resources or data at the same privilege level.

### Account Takeover

A threat actor gains control of a valid account and uses it to access
further internal applications and sensitive information.

**Detection:** odd login locations, multiple failed login attempts,
lateral phishing emails, or abnormal file downloading.

### Metadata Service Attacks

Targeting cloud metadata services, which provide applications with
temporary credentials and run startup scripts.

**The risk:** if an attacker reaches these endpoints, they can steal
valid API secret keys or find plaintext passwords left in startup
scripts.

### Resource Exhaustion & DoS Attacks

Sending crafted packets or high traffic volumes to overwhelm server
memory/CPU and crash applications.

**Direct-to-Origin (D2O):** finding the hidden, real IP address behind a
protective CDN to bypass DDoS protection.

### Cloud Malware Injection

Injecting a malicious application into a cloud environment so it runs
alongside legitimate instances, giving the attacker a permanent foothold
to steal data, eavesdrop, or deploy backdoors.

### Side-Channel Attacks

Stealing sensitive data (like encryption keys) by measuring physical side
effects of hardware — timing information, power consumption, or
electromagnetic leaks.

**The risk:** threatens multi-tenant clouds where an attacker's VM shares
a physical CPU with the target's VM.

### Tools, SDKs, and CDKs

| Term | Description |
|---|---|
| **OAS / Swagger** | Frameworks for documenting and understanding API implementations during security testing. |
| **SDK** (Software Development Kit) | A kit of compilers and debuggers used to create software. |
| **CDK** (Cloud Development Kit) | Frameworks for defining, configuring, and safely deploying cloud infrastructure as code. |

## Attacking Mobile Devices

### Common Vulnerabilities

- **Spamming & Phishing** — smishing (SMS phishing) remains highly prevalent, redirecting users to malicious sites to steal credentials or install malware.
- **Business Logic Flaws** — attackers abuse legitimate transactions and app flows to cause unintended, negative behavior. These flaws are unique because automated scanners typically cannot detect them.
- **Lack of Least Privilege** — apps that over-reach on permissions or run unnecessarily with full root access.
- **Other weaknesses** — insecure data storage, passcode/biometric integration flaws, poor certificate pinning, and use of components with known vulnerabilities.

### Mobile Testing and Security Tools

| Tool | Description |
|---|---|
| **ApkX** | Decompiles Android application package files. |
| **Drozer** | Provides access to numerous exploits used to attack Android platforms. |
| **Ettercap** | Performs on-path (man-in-the-middle) attacks. |
| **Frida** | Dynamic instrumentation toolkit for security researchers and reverse engineers. |
| **MobSF** | Automated mobile application and malware analysis framework. |
| **Postman** | Used to test and develop APIs. |

## Attacking Internet of Things (IoT) Devices

### Why IoT Management & Security Is Challenging

- **System Complexity** — disparate hardware and software from multiple vendors and integrators.
- **Legacy Technologies** — continued use of legacy/outdated tech complicates modern security orchestration.
- **Fragmentation** — no single, unified security solution covers all diverse IoT deployment scenarios.

### Analyzing IoT Protocols

**Common protocols:** Wi-Fi, Bluetooth/BLE, Zigbee, Z-Wave, LoRaWAN,
Insteon, Modbus, Siemens S7comm.

**Bluetooth Low Energy (BLE) risks:**

- Connections rely on a three-phase sequence: pairing feature exchange, short-term key generation, and transport-specific key distribution.
- Many implementations fail to enable BLE-layer encryption, leaving data exposed.
- Attackers can harvest advertisements, deploy clone/fake BLE devices, and conduct on-path attacks.

**Protocol testing tools:**

| Tool | Purpose |
|---|---|
| **Ubertooth One** | Specialized hardware/antenna used to sniff and analyze BLE traffic. |
| **GATTacker & BtleJuice** | Software frameworks to intercept, manipulate, and execute on-path attacks on BLE infrastructure. |

### IoT Security — Special Considerations

- **Fragile Environments** — IoT setups can be brittle; traditional high-intensity network scans might accidentally crash devices.
- **Availability Concerns** — interruptions to network access or device functions can halt critical operations.
- **Data Corruption** — tampering with internal data fields can skew tracking metrics or degrade system operations.
- **Data Exfiltration** — attackers can compromise insecure IoT systems and use them as gateways to exfiltrate sensitive organizational data.

### Common IoT Vulnerabilities

1. Insecure defaults
2. Plaintext data leaks
3. Hard-coded credentials
4. Missing/insecure update mechanisms

**Security checklist:** ensure the device supports encrypted
communications, allows firmware updates, and has default
configurations/credentials changed.

**Architecture & misconfigurations:** IoT data typically flows
**Endpoints (things) → Fog/Edge Gateways → Cloud Services**. Data theft
usually results from public network exposure, lack of input
sanitization, and default credentials.

## Management Interfaces (IPMI & BMC)

**IPMI:** a tool administrators use for out-of-band management (managing
servers/IoT devices even when powered off).

**The risk (BMC):** the Baseboard Management Controller has direct access
to the motherboard. If compromised, an attacker gains the equivalent of
physical access, and can monitor, reboot, and install malicious
software/implants.

## Virtual Machine (VM) Vulnerabilities

### Hypervisors

| Type | Description |
|---|---|
| **Type 1** | Runs directly on bare-metal hardware (e.g., ESXi, Hyper-V). |
| **Type 2** | Runs on top of a host OS (e.g., VirtualBox). |

### VM Vulnerabilities

- **VM Escape** — a threat actor breaks out of an isolated VM to access the hypervisor or neighboring VMs.
- **Hyperjacking** — injecting or taking over a hypervisor to secretly control the entire virtual environment.
- **Repository Vulnerabilities** — attackers uploading fake, backdoored VM images to public marketplaces.

## Containers & Security Tools

**Risk:** running containers with root privileges leaves them highly
vulnerable to full system compromise.

**Supply Chain Attacks:** threat actors frequently upload malicious code
disguised as legitimate Docker images to public registries like Docker
Hub.

### Tools Cheat Sheet

| Tool | Purpose |
|---|---|
| **Grype** | Open-source container vulnerability scanner. |
| **Dagda** | Detects malware, trojans, and exploits in Docker images. |
| **Kube-bench** | Checks Kubernetes clusters against official CIS Benchmarks. |
| **Kube-hunter** | Actively hunts for security weaknesses in Kubernetes clusters. |
| **Falco** | Real-time threat detection engine for Kubernetes. |

---

**Previous:** [06 · Exploiting Application-Based Vulnerabilities](06-exploiting-application-based-vulnerabilities.md) · **Next:** [08 · Performing Post-Exploitation Techniques](08-post-exploitation-techniques.md)
