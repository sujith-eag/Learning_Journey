
# Managing Network Interfaces

## 1. Enabling or Disabling Network Interfaces

Bring a network interface up or down using the `ip` command:

```bash
sudo ip link set eth0 up     # Enable interface
sudo ip link set eth0 down   # Disable interface
```

Useful for activating or deactivating a device without rebooting.

## 2. Assigning a Static IP Address

Set a manual IP address and default gateway:

```bash
sudo ip addr add 10.0.0.5/24 dev eth0
sudo ip route add default via 10.0.0.1
```

- `ip addr add`: Assigns the IP address with subnet mask.
    
- `ip route add default`: Sets the default gateway for outbound traffic.

> These settings are temporary and will be lost on reboot unless made persistent via network configuration files or a network manager.

## 3. Viewing the Routing Table

Inspect how packets are routed through the system:

```bash
route -n          # Legacy tool
ip route show     # Preferred modern command
```

- Displays default gateway, connected networks, and routing priorities.
    
## 4. DNS Configuration and Lookup

### View Current DNS Servers

```bash
cat /etc/resolv.conf
```

- Shows the DNS servers used for resolving domain names.
    
- Typically managed by `systemd-resolved`, NetworkManager, or other services.
    
### Querying DNS Records

```bash
dig @8.8.8.8 example.com A
nslookup example.com 1.1.1.1
```

- `dig`: Powerful and script-friendly DNS query tool.
    
- `nslookup`: Simple DNS query tool, still widely used.
    
## 5. Checking Active Network Services

Inspect open ports and services:

```bash
sudo ss -tulpn
```

- Lists all listening TCP/UDP sockets with program names.
    
- Replaces the older `netstat -tulpn`.
    
## 6. Monitoring Network and ARP Activity

### View ARP Cache

```bash
arp -n
ip neigh
```

- Shows resolved MAC addresses for local IPs.
    
- `ip neigh` is the modern replacement for `arp`.
    

### Live Packet Capture

```bash
sudo tcpdump -i eth0 -n
```

- Captures packets on `eth0` and displays header-level data.
    
- Useful for low-level network diagnostics.

## 7. Firewall Configuration

### List Firewall Rules

```bash
sudo iptables -L -nv

sudo ufw status verbose
```

- `iptables`: Low-level firewall tool.
    
- `ufw`: User-friendly frontend for `iptables`.
    

### Add Basic Rules

```bash
sudo iptables -A INPUT -p tcp --dport 22 -j ACCEPT
sudo ufw allow 443/tcp
```

- Allows specific traffic (e.g., SSH on port 22, HTTPS on port 443).
    
## 8. Essential Networking and Security Tools

|Tool|Purpose|
|---|---|
|`nmap`|Network scanning, port detection, vulnerability checks|
|`netcat (nc)`|TCP/UDP connectivity testing, file transfers|
|`tcpdump`|Packet capture and inspection|
|`wireshark`|GUI-based packet analysis|
|`traceroute`|Displays route to a remote host|
|`whois`|Domain and IP ownership information|
|`dig`, `nslookup`|DNS record querying|
