# Skill: nmap

Network mapper — discovers hosts and services on a network.

## Commands Used

### Ping sweep (host discovery)
```
sudo nmap -sn 192.168.238.0/24
```
Finds all live hosts on a subnet. No port scanning — just "who's there?"

### Service + OS detection
```
sudo nmap -sV -O <target>
```
- `-sV` — detect service versions (e.g. "vsftpd 2.3.4" not just "FTP")
- `-O` — fingerprint the operating system

## Key Concepts

- **Ports** are numbered doors into a machine. Each service listens on a specific port.
- Services advertise their **version in banners** — nmap reads these. Old versions = known vulnerabilities.
- **NAT networks** are isolated — hosts inside can't be reached from the internet directly.
- A scan shows ports open *at that moment* — dynamically opened ports (like backdoors) won't appear until triggered.

## Lessons Learned

- vsftpd 2.3.4 announced itself in the FTP banner — nmap read it and confirmed the vulnerable version
- Port 6200 (vsftpd backdoor) wasn't visible in the initial scan because it only opens when triggered
- MAC address prefix `00:0C:29` and `00:50:56` = VMware hardware
