
```bash
sudo apt install nmap
```


```bash
nmap --version
Nmap version 7.94SVN ( https://nmap.org )
Platform: x86_64-pc-linux-gnu
Compiled with: liblua-5.4.6 openssl-3.0.13 libssh2-1.11.0 libz-1.3 libpcre2-10.42 libpcap-1.10.4 nmap-libdnet-1.12 ipv6
Compiled without:
Available nsock engines: epoll poll select
```

### 
```bash
$ nmap 172.1.27.106


Starting Nmap 7.94SVN ( https://nmap.org ) at 2025-05-29 11:35 IST
Nmap scan report for 172-1-27-106.lightspeed.toldoh.sbcglobal.net (172.1.27.106)
Host is up (0.00022s latency).
Not shown: 996 closed tcp ports (conn-refused)
PORT     STATE SERVICE
22/tcp   open  ssh
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
8888/tcp open  sun-answerbook

Nmap done: 1 IP address (1 host up) scanned in 0.29 seconds

```

## Port Scanning for Domain name
```bash
$ nmap sujith-eag.in

Starting Nmap 7.94SVN ( https://nmap.org ) at 2025-05-29 11:39 IST
Nmap scan report for sujith-eag.in (52.220.155.145)
Host is up (0.036s latency).
Other addresses for sujith-eag.in (not scanned): 52.76.120.174
rDNS record for 52.220.155.145: ec2-52-220-155-145.ap-southeast-1.compute.amazonaws.com
Not shown: 997 filtered tcp ports (no-response)
PORT     STATE  SERVICE
80/tcp   open   http
443/tcp  open   https
6346/tcp closed gnutella

Nmap done: 1 IP address (1 host up) scanned in 4.88 seconds
```

### Detecting OS

```bash
$ sudo nmap -O 172.1.27.23
[sudo] password for mca1: 
Starting Nmap 7.94SVN ( https://nmap.org ) at 2025-05-29 11:47 IST
Nmap scan report for 172-1-27-23.lightspeed.toldoh.sbcglobal.net (172.1.27.23)
Host is up (0.00088s latency).
Not shown: 997 closed tcp ports (reset)
PORT     STATE SERVICE
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
8888/tcp open  sun-answerbook
MAC Address: 04:7C:16:F4:D5:0B (Micro-Star Intl)
Device type: general purpose
Running: Linux 4.X|5.X
OS CPE: cpe:/o:linux:linux_kernel:4 cpe:/o:linux:linux_kernel:5
OS details: Linux 4.15 - 5.8
Network Distance: 1 hop

OS detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 1.62 seconds
```

### OS and Port Scanning

```bash
$ sudo nmap -O -p 80, 172.1.27.106

Starting Nmap 7.94SVN ( https://nmap.org ) at 2025-05-29 11:49 IST
Nmap scan report for 172-1-27-106.lightspeed.toldoh.sbcglobal.net (172.1.27.106)
Host is up (0.00088s latency).

PORT   STATE  SERVICE
80/tcp closed http
MAC Address: 04:7C:16:F4:D4:B8 (Micro-Star Intl)
Too many fingerprints match this host to give specific OS details
Network Distance: 1 hop

OS detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 1.98 seconds

```

### Scanning with File

```txt
// ip.add.txt

172.1.27.106
172.1.27.108
172.1.27.67
172.1.27.100
```

```bash
$nmap -iL ip_add.txt 

Starting Nmap 7.94SVN ( https://nmap.org ) at 2025-05-29 11:53 IST
Nmap scan report for 172-1-27-106.lightspeed.toldoh.sbcglobal.net (172.1.27.106)
Host is up (0.00035s latency).
Not shown: 996 closed tcp ports (conn-refused)
PORT     STATE SERVICE
22/tcp   open  ssh
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
8888/tcp open  sun-answerbook

Nmap scan report for 172-1-27-108.lightspeed.toldoh.sbcglobal.net (172.1.27.108)
Host is up (0.00021s latency).
Not shown: 996 closed tcp ports (conn-refused)
PORT     STATE SERVICE
22/tcp   open  ssh
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
8888/tcp open  sun-answerbook

Nmap scan report for 172-1-27-67.lightspeed.toldoh.sbcglobal.net (172.1.27.67)
Host is up (0.00034s latency).
Not shown: 996 closed tcp ports (conn-refused)
PORT     STATE SERVICE
22/tcp   open  ssh
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
8888/tcp open  sun-answerbook

Nmap done: 4 IP addresses (3 hosts up) scanned in 1.34 seconds

```

### No Port Scan
```bash
$ nmap -sn 172.1.27.66
Starting Nmap 7.94SVN ( https://nmap.org ) at 2025-05-29 12:11 IST
Nmap scan report for 172-1-27-66.lightspeed.toldoh.sbcglobal.net (172.1.27.66)
Host is up (0.00054s latency).
Nmap done: 1 IP address (1 host up) scanned in 0.00 seconds
```

### Random Scanning

```bash
$nmap -iR 5
Starting Nmap 7.94SVN ( https://nmap.org ) at 2025-05-29 12:00 IST
Nmap scan report for ec2-52-24-90-201.us-west-2.compute.amazonaws.com (52.24.90.201)
Host is up (0.26s latency).
Not shown: 998 filtered tcp ports (no-response)
PORT    STATE SERVICE
80/tcp  open  http
443/tcp open  https

Nmap done: 5 IP addresses (1 host up) scanned in 20.53 seconds

```


## SSH Connecting(if SSH port 22 open)

```bash
mca1@administrator:~$ nmap -p 22, 127.1.27.97
Starting Nmap 7.94SVN ( https://nmap.org ) at 2025-05-29 12:13 IST
Nmap scan report for localhost (127.1.27.97)
Host is up (0.000035s latency).

PORT   STATE SERVICE
22/tcp open  ssh

Nmap done: 1 IP address (1 host up) scanned in 0.01 seconds

mca1@administrator:~$ ssh 127.1.27.97
The authenticity of host '127.1.27.97 (127.1.27.97)' can't be established.
ED25519 key fingerprint is SHA256:h9GJPsFkzmD3rLbpiW2I3paOaWTYaX98jpkv5sxIMK4.
This host key is known by the following other names/addresses:
    ~/.ssh/known_hosts:1: [hashed name]
    ~/.ssh/known_hosts:4: [hashed name]
    ~/.ssh/known_hosts:5: [hashed name]
    ~/.ssh/known_hosts:6: [hashed name]
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '127.1.27.97' (ED25519) to the list of known hosts.
mca1@127.1.27.97's password: 
Welcome to Ubuntu 24.04 LTS (GNU/Linux 6.11.0-26-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/pro

Expanded Security Maintenance for Applications is not enabled.

295 updates can be applied immediately.
To see these additional updates run: apt list --upgradable

10 additional security updates can be applied with ESM Apps.
Learn more about enabling ESM Apps service at https://ubuntu.com/esm

Last login: Thu May 29 12:09:44 2025 from 172.1.27.108
mca1@administrator:~$ Desktop/; ls
-bash: Desktop/: Is a directory
daa        Downloads      lab.pcapng  Public           Templates
Desktop    GNS3           Music       PycharmProjects  Videos
Documents  jcef_5577.log  Pictures    snap

mca1@administrator:~$ sudo shutdown now
```
