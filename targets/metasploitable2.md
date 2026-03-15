# Target: Metasploitable 2

## Overview

Metasploitable 2 is a deliberately vulnerable Linux VM designed for practicing penetration testing techniques. It is intentionally misconfigured and runs outdated, vulnerable software.

- **IP:** 192.168.238.130
- **OS:** Ubuntu 8.04 (Linux 2.6.x)
- **Source:** https://sourceforge.net/projects/metasploitable/

## Open Ports (from nmap -sV -O scan)

| Port | Service | Version | Notes |
|------|---------|---------|-------|
| 21 | FTP | vsftpd 2.3.4 | Backdoored — exploited ✅ |
| 22 | SSH | OpenSSH 4.7p1 | Old, potentially brute-forceable |
| 23 | Telnet | Linux telnetd | Cleartext credentials |
| 25 | SMTP | Postfix | |
| 53 | DNS | ISC BIND 9.4.2 | |
| 80 | HTTP | Apache 2.2.8 | Web app vulnerabilities |
| 139/445 | SMB | Samba 3.x | |
| 1524 | Shell | Metasploitable root shell | Permanent open root shell |
| 3306 | MySQL | 5.0.51a | Often no root password |
| 5432 | PostgreSQL | 8.3.0 | |
| 5900 | VNC | Protocol 3.3 | Weak/no password |
| 6667 | IRC | UnrealIRCd | Backdoored |
| 8180 | HTTP | Apache Tomcat | |

## Exploits Attempted

### vsftpd 2.3.4 Backdoor ✅
- **Module:** `exploit/unix/ftp/vsftpd_234_backdoor`
- **Result:** Root shell
- **How it works:** Sending a username containing `:)` triggers the backdoor, opening port 6200 with a root shell. Port 6200 is ephemeral — closes when session ends.
- **Date:** 2026-03-15
