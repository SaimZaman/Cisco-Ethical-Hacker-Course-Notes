# 04 · Social Engineering Attacks

> Module 4 of my Ethical Hacking / Penetration Testing course notes.
> Covers pretexting, phishing variants, physical social engineering
> attacks, and the tools used to carry them out.

## Table of Contents

- [Core Concepts](#core-concepts)
- [Types of Social Engineering Attacks](#types-of-social-engineering-attacks)
- [Types of Physical Attacks](#types-of-physical-attacks)
- [Social Engineering Tools](#social-engineering-tools)

## Core Concepts

Social engineering relies on three core components:

- **Influence** — persuading a target to act in the attacker's favor.
- **Interrogation** — extracting information through conversation.
- **Impersonation** — presenting as someone else to gain trust or access.

### Pretexting

With pretexting (impersonation), an attacker presents as someone else in
order to gain access to information.

## Types of Social Engineering Attacks

### 1. Email Phishing

| Variant | Description |
|---|---|
| **Phishing** | Mass emails sent to broad audiences, containing malicious links or attachments disguised as trusted sources, to steal credentials. |
| **Spear Phishing** | A highly customized phishing attack targeted at a specific individual or group, built by researching their habits and relationships. |
| **Whaling** | A specialized form of spear phishing that exclusively targets high-profile executives (e.g., CEOs) using urgent, official-looking corporate documents. |

### 2. Vishing (Voice Phishing)

A social engineering attack conducted over phone calls, where the
attacker impersonates a trusted entity to steal personal or financial
data.

### 3. Smishing (SMS Phishing)

Phishing campaigns executed through text messages containing malicious
links, often disguised as bank alerts, delivery/order issues, or prize
notifications.

### 4. USB Drop Key

Leaving malware-loaded USB drives in public or strategic areas, relying
on human curiosity to get victims to plug them into a corporate computer.

### 5. Watering Hole Attacks

Attackers find and compromise legitimate websites that their target
audience frequently visits, injecting malicious code to infect visitors'
devices.

### 6. Physical Attacks

An attacker physically attempts to steal data, or gain entry to a
building or server room.

## Types of Physical Attacks

| Attack | Description |
|---|---|
| **Piggybacking** | An unauthorized person follows an authorized person into a restricted area *with* their knowledge or consent (e.g., someone holds the door open out of courtesy). |
| **Shoulder Surfing** | An attacker looks over a victim's shoulder to steal sensitive data such as passwords, PINs, or personally identifiable information (PII). |
| **Badge Cloning** | An attacker duplicates or copies a legitimate access card or key fob to bypass building security. |
| **Dumpster Diving** | An attacker searches through trash or recycling bins for discarded paperwork containing private or sensitive information. |
| **Tailgating** | An unauthorized person slips through a secure door behind an authorized person *without* their knowledge or consent. |

> **Piggybacking vs. Tailgating:** the difference is consent — piggybacking
> happens with the authorized person's awareness, tailgating happens
> without it.

## Social Engineering Tools

| Tool | Purpose |
|---|---|
| **SET** (Social-Engineer Toolkit) | Framework for building and launching social engineering campaigns (phishing pages, payloads, etc.). |
| **BeEF** (Browser Exploitation Framework) | Focuses on exploiting vulnerabilities in web browsers. |

### Call Spoofing Tools

- **Spoof App**
- **Spoof Card**
- **Asterisk**

---

**Previous:** [03 · Information Gathering and Vulnerability Scanning](03-information-gathering-and-vulnerability-scanning.md) · **Next:** [05 · Exploiting Wired and Wireless Networks](05-exploiting-wired-and-wireless-networks.md)
