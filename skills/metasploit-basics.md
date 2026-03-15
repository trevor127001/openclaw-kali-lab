# Skill: Metasploit

Metasploit is a penetration testing framework — a toolkit for finding and exploiting vulnerabilities.

## Starting Metasploit
```
msfconsole
```
Takes ~30-60 seconds to load. You land at the `msf >` prompt.

## Basic Workflow

```
use <module>        # load an exploit or auxiliary module
show options        # see required/optional settings
set RHOSTS <ip>     # set target IP
run                 # execute
```

## Key Concepts

- **Modules** are pre-built exploits. Each targets a specific vulnerability in a specific service/version.
- **RHOSTS** = target (Remote HOSTS). Required for most exploits.
- **RPORT** = target port. Usually pre-set to the default for that service.
- **Payload** = what runs on the target after exploitation. A shell is the most common.

## Privilege Levels

Whatever user runs the vulnerable service is what you get:
- Service running as `root` → you get root
- Service running as `www-data` → you get www-data
- This is why "least privilege" matters — limits blast radius of a compromise

## Lessons Learned

- The vsftpd backdoor was a **supply chain attack** — malicious code injected into the source before distribution (2011)
- Persistence matters: a shell session isn't permanent. Real attackers install backdoors, add SSH keys, or create users to maintain access after the session ends.
- Metasploit knows about thousands of vulnerabilities — the hard part isn't running the exploit, it's knowing which one to use and why it works
