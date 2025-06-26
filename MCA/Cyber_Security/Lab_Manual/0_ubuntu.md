
# Linux Networking & Cybersecurity Essentials

## 1. System Identity & Hostname

### Viewing and Changing Hostname

```bash
hostname
sudo hostnamectl set-hostname new-hostname
```

- `hostname`: Displays the system's current hostname.
    
- `hostnamectl`: Modern tool for persistent change (affects `/etc/hostname`).
    

---

## 2. Network Interfaces Overview

### Legacy: `ifconfig`

```bash
ifconfig -a
```

- Lists all interfaces (even inactive).
    
- Shows IP addresses, MAC address (HWaddr), RX/TX stats.
    
- **Note**: Deprecated in many distros.
    

### Recommended: `ip` command

```bash
ip addr show
ip link show
```

- `ip addr`: Shows IP addresses + interface status.
    
- `ip link`: Shows MAC address, interface flags (`UP`, `BROADCAST`, etc.).
    
- To bring interface up/down:
    

```bash
sudo ip link set eth0 up
sudo ip link set eth0 down
```

---

## 3. Checking MAC Address

```bash
ifconfig eth0
ip link show eth0
```

- MAC (hardware) address identifies the NIC.
    
- Important for ARP and local network identification/classification.
    

---

## 4. IP Address Management

### View IP, Netmask, Broadcast

```bash
ip addr show eth0
```

Output includes:

- `inet`: IPv4 address and subnet (e.g., `192.168.1.5/24`)
    
- `inet6`: IPv6 address
    
- Network mask, dynamic/static configuration.
    

### Set a Static IP

```bash
sudo ip addr add 10.0.0.5/24 dev eth0
sudo ip route add default via 10.0.0.1
```

- Adds a static IP and custom route via gateway.
    

---

## 5. Routing Table Inspection

```bash
route -n
ip route show
```

- `route -n`: Old-style routing table.
    
- `ip route`: Modern equivalent. Shows default gateways and network paths.
    

---

## 6. DNS Configuration & Query

### Check DNS Servers

```bash
cat /etc/resolv.conf
```

- Lists DNS servers used by system resolver.
    

### Query with `dig` and `nslookup`

```bash
dig @8.8.8.8 example.com A
nslookup example.com 1.1.1.1
```

- `dig`: Flexible DNS query utility.
    
- `nslookup`: Basic DNS lookup tool for interactive queries or scripts.
    

---

## 7. Network Services & Connection Inspection

### `netstat` / `ss`

```bash
sudo ss -tulpn
```

- Lists TCP/UDP listening ports with associated programs.
    
- Replaces deprecated `netstat -tulpn` in modern distros.
    

---

## 8. Packet Monitoring and ARP

### Display ARP Cache

```bash
arp -n
ip neigh
```

### Live Packet Capture with tcpdump

```bash
sudo tcpdump -i eth0 -n
```

- Captures and displays traffic headers (packets).
    

---

## 9. Firewall: `iptables` / `ufw`

### List Rules

```bash
sudo iptables -L -nv
sudo ufw status verbose
```

### Basic Rule Creation

```bash
sudo iptables -A INPUT -p tcp --dport 22 -j ACCEPT
sudo ufw allow 443/tcp
```

- Controls network traffic for better security.
    

---

## 10. Useful CLI Tools for Cybersecurity

- `nmap`: Network mapping and vulnerability scanning
    
- `netcat` (`nc`): TCP/UDP connection tool
    
- `tcpdump`: Network traffic capture
    
- `wireshark`: Packet-level GUI analysis
    
- `traceroute`: Trace packet path (`traceroute 8.8.8.8`)
    
- `whois`, `dig`, `nslookup`: DNS and domain information gathering
    

---

## Quick Command Reference

|Command|Purpose|
|---|---|
|`hostnamectl`|View or set system hostname|
|`ip addr`, `ip link`|Show IPs and network interfaces|
|`ifconfig -a`|Legacy interface tool|
|`arp -n`, `ip neigh`|Show ARP cache|
|`ip route`, `route -n`|Display routing table|
|`cat /etc/resolv.conf`|List DNS resolvers|
|`dig`, `nslookup`|DNS querying tools|
|`ss -tulpn`, `netstat`|Check open/listening TCP/UDP ports|
|`tcpdump`|Capture packets in real time|
|`iptable` / `ufw`|Firewall management|

---

Let me know if you'd like detailed usage examples, common security use-cases (e.g., ARP spoofing, DNS poisoning), or a formatted PDF/Markdown version.