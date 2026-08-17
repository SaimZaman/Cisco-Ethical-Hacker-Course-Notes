# 02 · Intro to Ethical Hacking and Penetration Testing

> Module 2 of my Ethical Hacking / Penetration Testing course notes.
> Covers pentest types, methodologies, and the core Kali Linux commands
> used throughout the rest of the course.

## Table of Contents

- [Types of Penetration Testing](#types-of-penetration-testing)
- [Penetration Testing Methods](#penetration-testing-methods)
- [Industry Methodologies](#industry-methodologies)
- [Exploring Kali Linux](#exploring-kali-linux)

## Types of Penetration Testing

- **Application-Based Testing** — targets web/mobile/desktop applications.
- **Network Infrastructure Testing** — targets routers, switches, firewalls, and internal/external networks.
- **Cloud Testing** — targets cloud-hosted infrastructure and services.

## Penetration Testing Methods

| Method | Also Known As | Description |
|---|---|---|
| Known Environment | White-box | Full knowledge of the target is provided. |
| Unknown Environment | Black-box | No prior knowledge of the target is provided. |
| Partially Known Environment | Grey-box | Limited knowledge (e.g., only a URL or IP range) is provided. |

## Industry Methodologies

Standard frameworks that guide how a penetration test is planned and
executed:

- **OWASP WSTG** — Web Security Testing Guide
- **MITRE ATT&CK** — adversary tactics and techniques knowledge base
- **NIST SP 800-115** — Technical Guide to Information Security Testing and Assessment
- **OSSTMM** — Open Source Security Testing Methodology Manual
- **PTES** — Penetration Testing Execution Standard
- **ISSAF** — Information Systems Security Assessment Framework

## Exploring Kali Linux

### Root Privileges

`su` and `sudo` both grant root permissions.

### Useful Commands

**`grep`** — search for a specific text pattern.

```bash
┌──(kali㉿kali)-[~]
└─$ grep sudo /etc/group
sudo:x:27:kali
```

**`history`** — show the history of previously used commands.

**`man`** — obtain detailed documentation about a command.

```bash
man ls
```

### Basic Commands Reference

| Command | Description |
|---|---|
| `mv` | Moves or renames files and directories. |
| `chmod` | Modifies file permissions. |
| `chown` | Changes the ownership of a file. |
| `dd` | Copies and converts data. |
| `pwd` | Displays the current working directory. |
| `cd` | Changes the current directory. |
| `ls` | Lists the contents of a directory. |
| `mkdir` | Creates a new directory. |
| `cp` | Copies files and directories. |
| `rm` | Removes (deletes) files or directories. |

> **Note:** `$` indicates a regular (non-root) user prompt, and `#`
> indicates a root user prompt.
>
> `cd ~` is a shortcut to the current user's home directory.
>
> `.` refers to the current directory (`cd .` causes no visible change).
> `..` refers to the parent directory, one level up (`cd ..`).

### Redirecting Output

The `>` operator redirects a command's output to a file instead of the
terminal window.

```bash
┌──(kali㉿kali)-[~]
└─$ echo echo this message
echo this message

┌──(kali㉿kali)-[~]
└─$ echo redirect this to a file > text_file.txt
```

### Appending to a File

The `>>` operator appends output to an existing file instead of
overwriting it.

```bash
┌──(kali㉿kali)-[~]
└─$ echo this text will be appended to the text file >> text_file.txt
```

### Deleting Files and Directories

```bash
# Delete a file
rm text_file.txt

# Delete a directory
rm -r directory_name
```

### Moving Files and Directories

```bash
┌──(kali㉿kali)-[~]
└─$ mv kali_folder2/text_file.txt .
```

---

**Previous:** [01 · Planning and Scoping](01-planning-and-scoping.md) · **Next:** [03 · Information Gathering and Vulnerability Scanning](03-information-gathering-and-vulnerability-scanning.md)
