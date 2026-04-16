# Methodology

This document summarizes the techniques and tool categories used around this lab during the **Attacking Linux** course. It is intentionally written as course-support documentation rather than as a step-by-step exploitation guide.

## Reconnaissance

Students typically begin with standard host and service discovery:

- fast TCP discovery
- full port scans
- service version detection
- OS fingerprinting
- host discovery on the local subnet

This stage helps identify the expected exposed services:

- HTTP
- SSH
- FTP

## Web Enumeration

The WordPress instance supports several useful enumeration tracks:

- identifying active plugins
- mapping administrative and content endpoints
- discovering import, editor, and upload-related functionality
- testing for file inclusion or unsafe file access behavior
- reviewing content, media, and seeded posts for clues

Directory and content discovery tools can be used to broaden the visible attack surface.

## WordPress Plugin Testing

The course material references multiple vulnerable or high-risk plugin behaviors. In practice, students should learn to:

- inspect plugin names and versions
- map plugin-specific endpoints
- test file-read behavior safely in the lab
- identify upload surfaces and code execution risk
- understand how plugin abuse can expose configuration files or credentials

## Credential Attacks

Because the VM is intentionally weak, password auditing is part of the exercise:

- FTP password guessing against the `webmaster` account
- SSH password attacks using short user lists and weak password sets
- credential reuse validation across WordPress, FTP, SSH, and database services

The goal is to teach how weak credentials compound across services, not just how to break a single login.

## Database and Injection Testing

The WordPress plugins bundled in the lab also support discussion around:

- unsafe parameter handling
- input-based SQL injection testing
- database enumeration after a suspected injection finding

This is useful both for exploitation and for teaching what evidence of poor input handling looks like.

## Post-Exploitation Topics

Once students obtain code execution or a foothold, the lab supports follow-on exercises such as:

- stabilizing shell access
- finding reused credentials
- reading backups and config files
- locating writable paths
- pivoting from application access to local user access
- escalating privileges through local misconfiguration

## Password Recovery and Cracking

Course exercises may also include offline password recovery topics such as:

- ZIP password cracking
- wordlist-based cracking with rules
- brute-force or incremental strategies
- validating recovered credentials against the exposed services

## Suggested Student Workflow

1. Discover exposed services.
2. Enumerate HTTP, WordPress content, and plugins.
3. Test likely weak credentials on the exposed services.
4. Abuse application weaknesses to recover files or gain access.
5. Use recovered data to move deeper into the target.
6. Escalate locally and document the full attack path.

## Scope Reminder

This repository and VM are intended for isolated class use. The techniques discussed here should remain limited to owned infrastructure, course VMs, and explicit lab environments.
