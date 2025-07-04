
# Nmap – Network and Port Scanning

## 1. Installation and Setup

To install Nmap on a Debian/Ubuntu-based system:

```bash
sudo apt update
sudo apt install nmap
```

Check the installed version:

```bash
nmap --version
```

Expected output:

```
Nmap version 7.94SVN ( https://nmap.org )
Platform: x86_64-pc-linux-gnu
...
```

To list all available options and flags:

```bash
nmap --help
```

## 2. Basic Scanning Techniques

### Scanning a Single IP

```bash
nmap 172.1.27.106
```

This performs a default scan of the top 1000 TCP ports. By default:

- `-sS` (SYN scan) is used if run as root
    
- `-sT` (TCP connect scan) is used if not run as root
```
PORT     STATE SERVICE
22/tcp   open  ssh
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
8888/tcp open  sun-answerbook
```

### Scanning a Domain Name

```bash
nmap google.com
nmap msrit.com
```

Nmap resolves the domain to its IP address before scanning. Output shows the open and filtered ports, as well as DNS resolution.

### Ping Scan (Host Discovery Only)

The `-sn` option disables port scanning and performs only host discovery (ping sweep). This mode is used only to check which hosts are up.

```bash
nmap -sn 172.1.27.66
```

```
Host is up (0.00054s latency).
```

### Scanning Top Common Ports

```bash
nmap --top-ports 100 172.1.27.10
```

Scans the 100 most common TCP ports based on real-world scan data.

### Scanning Specific Ports

```bash
nmap -p 21,25,80 172.1.27.10
```

Scans ports 21 (FTP), 25 (SMTP), and 80 (HTTP).

## 3. Intermediate Scanning Techniques

### Service Version Detection

```bash
nmap -sV 172.1.27.10
```

- `-sV` probes open ports to determine running service versions.
    

### Operating System Detection

OS detection uses TCP/IP stack fingerprinting. It requires root privileges:
```bash
sudo nmap -O 172.1.27.23
```

The `-O` flag enables operating system detection. Nmap compares the target’s response patterns to known OS fingerprints.


### Combined OS and Port Scan

```bash
sudo nmap -O -p 80 172.1.27.106
```

Restricts the Scan to port 80 and attempts to detect the operating system.

### Scanning All Ports (Full Scan)

```bash
sudo nmap -p- 172.1.27.10
```

- `-p-` scans all 65535 TCP ports instead of the default top 1000.
    

## 4. Advanced Scanning Techniques

### Aggressive Scan

```bash
sudo nmap -A 172.1.27.10
```

Combines multiple options:

- OS detection (`-O`)
    
- Version detection (`-sV`)
    
- Script scanning (`-sC`)
    
- Traceroute (`--traceroute`)
    

### UDP Scan

```bash
sudo nmap -sU 172.1.27.10
```

- Scans for open UDP ports. Useful for services like DNS, SNMP, NTP.

- Slower and less reliable due to the nature of UDP.
    
## Version Detection

```bash
nmap -sV 172.1.27.10
```

- `-sV`: Probes open ports to determine service and version information (e.g., Apache 2.4.54).

### Stealth (SYN) Scan with Version Detection

```bash
sudo nmap -sS -sV -p T:21,25,80 172.1.27.10
```

- `-sS`: SYN scan. Stealth scan using SYN packets (SYN scan).
	 
- `-p T:...`: TCP port list
  
- `-p T:21,25,80`: Scan specific TCP ports 21 (FTP), 25 (SMTP), and 80 (HTTP).
  
### Input List of IPs from a FIle

Create a file `ip_add.txt`:

```
172.1.27.106
172.1.27.108
172.1.27.67
172.1.27.100
```

Then scan:

```bash
nmap -iL ip_add.txt
```
The `-iL` option tells Nmap to read input targets from a file.

### Random IP Scanning

```bash
nmap -iR 5
```

Scans 5 randomly chosen IP addresses from the Internet. Useful for testing firewalls and studying large-scale scanning behavior.    

### Traceroute

```bash
nmap --traceroute 172.1.27.10
```

Displays the route packets take (hops) to the target host.

### Timing Options

```bash
nmap -T4 172.1.27.10
```

- `-T0` to `-T5`: Set scan timing.
    
- `-T4` is suitable for fast scans on LANs.
	
- Higher timing values reduce scan time but may increase detection risk.
  

### Output Formats

```bash
nmap -oN result.txt 172.1.27.10    
# Normal text output

nmap -oG result.gnmap 172.1.27.10  
# Grepable format

nmap -oX result.xml 172.1.27.10    
# XML format

nmap -oA fullscan 172.1.27.10      
# All formats with base name 'fullscan'
```


## 5. External Reconnaissance and DNS Tools

### Whois Lookup

```bash
whois google.com
```

- Provides domain registration, owner contact details, registrar, and creation/expiry dates.
    
- Useful for reconnaissance and attribution.
    
### DNS Lookup Using dig

```bash
dig google.com ANY
dig google.com A
dig google.com AAAA
dig google.com MX
```

- `ANY`: All available DNS records
    
- `A`: IPv4 address
    
- `AAAA`: IPv6 address
    
- `MX`: Mail server information
    
Reverse DNS:

```bash
dig -x 8.8.8.8
```

Query for a Domain name of IP using a specific DNS server:

```bash
dig @1.1.1.1 example.com +short
```

### IP Geolocation Lookup

```bash
curl ipinfo.io/8.8.8.8
```

- Fetches geographic and provider information of an IP address.
    

## 6. GUI-Based Tools

### Angry IP Scanner

- Simple and fast IP/port scanner with GUI
    
- Suitable for scanning LANs and small networks    

### Zenmap (Nmap GUI)

- Official GUI front-end for Nmap
    
- Allows you to configure scans, save profiles, and visualize results.

Install on Debian-based systems:

```bash
sudo apt install zenmap
```


## Common Nmap Options

| Option              | Description                                                          |
| -------------------|----------------------------------------------------------------------|
| `-sS`               | SYN scan (stealth scan; default when run as root)                    |
| `-sT`               | TCP connect scan (default when not root)                             |
| `-sU`               | UDP scan                                                             |
| `-sV`               | Service version detection                                            |
| `-O`                | OS detection                                                         |
| `-A`                | Aggressive scan (includes `-O`, `-sV`, default scripts, traceroute)  |
| `-p-`               | Scan all 65535 ports                                                 |
| `-p <range>`        | Scan specific ports (e.g., `-p 22,80,443` or `-p 1-1000`)            |
| `-T<0-5>`           | Set timing template (0 = paranoid, 5 = insane)                       |
| `-iL <file>`        | Input list of targets from file                                      |
| `-iR <num>`         | Scan a given number of random IPs                                    |
| `-sn`               | Ping scan only (host discovery, no ports scanned)                    |
| `--top-ports <n>`   | Scan top `n` most common ports                                       |
| `--traceroute`      | Perform traceroute to target                                         |
| `-n`                | Never resolve DNS (faster scans)                                     |
| `-R`                | Always resolve DNS                                                   |
| `-6`                | Enable IPv6 scanning                                                 |

## Output, Debugging, and Script Options

| Option              | Description                                                      |
| ------------------- | ---------------------------------------------------------------- |
| `-oN <file>`        | Output in normal format                                          |
| `-oG <file>`        | Output in grepable format                                        |
| `-oX <file>`        | Output in XML format                                             |
| `-oA <basename>`    | Output in all major formats at once (`.nmap`, `.xml`, `.gnmap`)  |
| `-v`, `-vv`, `-vvv` | Increase verbosity levels                                        |
| `-d`, `-d2`, ...    | Increase debugging levels (troubleshooting scans)                |
| `--script <name>`   | Run specific Nmap Scripting Engine (NSE) scripts                 |
| `--script-args`     | Pass arguments to scripts                                        |
| `--open`            | Show only open ports                                             |
| `--exclude`         | Exclude specific targets from the scan                           |
| `--exclude-file`    | Exclude hosts listed in a file                                   |
| `--reason`          | Display the reason for each port state                           |
| `--privileged`      | Assumes privileged user mode (useful for scripting environments) |
| `--version-trace`   | Display detailed version detection trace output                  |


### Notable NSE Script Categories (used with `--script`)

Nmap has a powerful scripting engine (NSE) to run individual or categorized scripts:

- `--script default` – runs default scripts (safe and general)
    
- `--script vuln` – runs vulnerability detection scripts
    
- `--script safe` – run safe scripts only
    
- `--script discovery` – for network discovery (e.g., DNS, SNMP, etc.)
    
- `--script malware` – check for known malware backdoors
    
- `--script auth` – attempt authentication bypass
    
- `--script exploit` – run known exploits (use with caution)
    

