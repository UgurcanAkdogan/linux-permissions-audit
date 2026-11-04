# Linux File Permissions Audit

> Part of my Google Cybersecurity Professional Certificate portfolio (Coursera lab environment).

## Project Description

In this project I audited file and directory permissions on a Linux system. The goal was to apply the **Principle of Least Privilege (PoLP)**: users and groups get only the access their role needs, which reduces the system's attack surface.

## Lab Environment

- **Platform:** Google Cybersecurity Professional Certificate (Coursera)
- **Operating system:** Linux (Bash shell)
- **Key commands:** `ls -la`, `chmod`, `cd`

## Step-by-Step Security Audit

### 1. Inspect the current permissions

I moved into the `projects` directory and listed everything, hidden files included, to read each file's permission string.

```bash
cd projects
ls -la
```

I checked the 10-character permission strings (for example `-rw-rw-rw-`) to find access that should not be there.

### 2. Remove write access for "others"

`project_x.txt` allowed the *other* class to write to it. I removed that permission to prevent unauthorized changes.

```bash
chmod o-w project_x.txt
```

**Result:** write access removed for the "other" class.

### 3. Secure a hidden file

Hidden files often hold sensitive data. I made `.project_x.txt` read-only by removing write permission for both the user and the group.

```bash
chmod ug-w .project_x.txt
```

**Result:** the file is protected against accidental or malicious changes.

### 4. Restrict directory access

I removed execute permission from the group on the `drafts` directory, which stops group members from entering it or running files inside.

```bash
chmod g-x drafts
```

**Result:** only the owner can access the directory contents.

## Quick Reference

| Symbol | Meaning |
| --- | --- |
| `u`, `g`, `o` | user (owner), group, others |
| `+` / `-` | add / remove a permission |
| `r`, `w`, `x` | read, write, execute |

## Key Takeaways

- **System hardening:** reducing permissions is a core step in securing a Linux environment.
- **Granular control:** I practiced `chmod` with symbolic mode (`u`, `g`, `o`) to change specific access levels.
- **Audit method:** `ls -la` reveals hidden files and permission risks.

## Repository Contents

| File | Description |
| --- | --- |
| [`Ugurcan_Akdogan_Linux_Permissions_Audit.pdf`](Ugurcan_Akdogan_Linux_Permissions_Audit.pdf) | Full audit write-up |

## About the Author

I am Uğurcan, an aspiring cybersecurity professional and SOC analyst focusing on Linux security, system hardening, and threat detection.
