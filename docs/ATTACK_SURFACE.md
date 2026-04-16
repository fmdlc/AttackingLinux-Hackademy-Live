# Attack Surface

This lab is designed for the **Attacking Linux** course at **EKoparty Hackademy**. The machine intentionally combines weak service configuration, exposed content, and vulnerable web application components to support guided exploitation and post-exploitation exercises in an isolated environment.

## Core Services

- **HTTP / WordPress**: the primary entry point for web enumeration, content discovery, plugin review, and application-layer testing.
- **MariaDB**: backend database used by WordPress and a likely target once credentials or configuration files are recovered.
- **VSFTPD**: enabled with a weakly protected local user to support authentication and password-auditing exercises.
- **SSH**: password authentication is enabled to support credential reuse and remote access scenarios.

## WordPress Components

The lab includes WordPress plus multiple plugins and supporting content intended to make the target feel closer to a real small-company deployment.

Relevant components discussed during the course include:

- `wp-autosuggest`
- `wp-site-import`
- a vulnerable site editor workflow
- an exposed upload mechanism used in the training narrative

## Intended Findings

Students are expected to discover several classes of weaknesses:

- weak service credentials
- exposed administrative surfaces
- insecure file permissions
- recoverable application secrets
- file-read or local file inclusion style issues in WordPress extensions
- insecure upload behavior leading to code execution risk
- opportunities for privilege escalation after foothold

## Example Scenarios Covered In Class

- reading sensitive local files through vulnerable plugin endpoints
- abusing unsafe import or editor features in WordPress extensions
- password attacks against exposed services in a contained lab
- credential reuse between FTP, SSH, WordPress, and database access
- identifying web application attack paths from plugin inventory and exposed content
- turning a web foothold into shell access and then local escalation

## Supporting Lab Artifacts

The bootstrap intentionally leaves behind artifacts that help tell a story and create a more believable target:

- FTP content owned by `webmaster`
- noisy backup and notes files
- permissive web directory permissions
- `wp-config.php` backup archive
- seeded WordPress pages, posts, and menu content

## Teaching Goal

This environment is not intended to represent a single CVE demo. Instead, it is built to support a realistic attack chain:

1. Reconnaissance and service discovery
2. Web and plugin enumeration
3. Credential attacks or application abuse
4. Initial foothold
5. Local discovery and privilege escalation

Use this lab only in isolated virtual machines or dedicated course infrastructure.
