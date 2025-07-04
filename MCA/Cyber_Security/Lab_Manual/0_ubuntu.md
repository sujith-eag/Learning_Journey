
# Linux Networking & Cybersecurity Essentials

## System Identity & Hostname

Viewing and Changing Hostname

```bash
hostname

sudo hostnamectl set-hostname new-hostname
```

- `hostname`: Displays the system's current hostname.
    
- `hostnamectl`: Modern tool for persistent change (affects `/etc/hostname`).

## Network Interfaces (`ip` command)

```bash
ip addr show

ip link show
```

Commands `ip link show` and `ip addr show` are used to inspect network interfaces on a Linux system.

- `ip link show` displays low-level details about each network interface, such as operational status and hardware (MAC) addresses.
    
- `ip addr show` includes all of that and adds IP address assignments (IPv4 and IPv6), making it more comprehensive.

> Use of `ifconfig` command is currently not recommended

### Interfaces Overview

| Interface   | Type           | Likely Purpose                             |
| ----------- | -------------- | ------------------------------------------ |
| `lo`        | Loopback       | Localhost interface (`127.0.0.1`)          |
| `enp0s31f6` | Ethernet NIC   | Wired network card                         |
| `wlp2s0`    | Wireless NIC   | Wi-Fi interface                            |
| `virbr0`    | Virtual Bridge | Virtual bridge (e.g., created by KVM/QEMU) |

### Field Descriptions (`ip link show`)

```bash
2: enp0s31f6: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN mode DEFAULT group default qlen 1000
    link/ether e4:b9:7a:6c:63:f7 brd ff:ff:ff:ff:ff:ff
```

- `2`: Interface index.
    
- `enp0s31f6`: Interface name.
    
- Flags in `<>`:
    
    - `NO-CARRIER`: No physical connection (e.g., cable unplugged).
        
    - `BROADCAST`, `MULTICAST`: Supports broadcast/multicast traffic.
        
    - `UP`: Interface is administratively up (enabled).
        
- `mtu 1500`: Maximum Transmission Unit in bytes.
    
- `qdisc fq_codel`: Queuing discipline (used for traffic shaping).
    
- `state DOWN`: Operational status (DOWN = inactive).
    
- `link/ether e4:b9:7a:6c:63:f7`: MAC address.
    
- `brd ff:ff:ff:ff:ff:ff`: Broadcast address.
    

### IP Address Information (`ip addr show`)

This command provides all the interface-level details shown by `ip link show`, and additionally displays assigned IP addresses, both IPv4 and IPv6, along with information about their validity periods.

#### lo (Loopback)

```bash
inet 127.0.0.1/8 scope host lo
inet6 ::1/128 scope host noprefixroute 
```

- IPv4: `127.0.0.1` — the standard local loopback address.
    
- IPv6: `::1` — loopback address for IPv6.
    
- `valid_lft forever`: These addresses never expire.
    
- Used for internal system communication, always active.
    

#### enp0s31f6 (Ethernet)

```bash
link/ether e4:b9:7a:6c:63:f7
```

- MAC: `e4:b9:7a:6c:63:f7`
    
- No IP address is assigned.
    
- Interface is marked `DOWN` with `NO-CARRIER`, indicating the cable is likely unplugged or the connection is inactive.
    

#### wlp2s0 (Wireless)

```bash
link/ether 98:3b:8f:05:90:60 brd ff:ff:ff:ff:ff:ff

inet 192.168.168.87/24 brd 192.168.168.255 scope global dynamic noprefixroute wlp2s0

inet6 2401:4900:640e:743e:3dbf:d692:999c:3c28/64 scope global temporary dynamic 

inet6 2401:4900:640e:743e:980:4d6e:252b:d7d0/64 scope global dynamic mngtmpaddr noprefixroute 

inet6 fe80::91c3:4fa6:62f2:b273/64 scope link noprefixroute 
```

- MAC: `98:3b:8f:05:90:60`
    
- IPv4: `192.168.168.87` — dynamically assigned (likely via DHCP).
    
- IPv6:
    
    - Global addresses: dynamically assigned and temporary (privacy extensions).
        
    - Link-local address: `fe80::...` used for local network operations.
        
- Interface is `UP` and `LOWER_UP`, indicating a working wireless connection.
    

#### virbr0 (Virtual Bridge)

```bash
inet 192.168.122.1/24 brd 192.168.122.255 scope global virbr0
link/ether 52:54:00:02:0d:74
```

- MAC: `52:54:00:02:0d:74`
    
- IPv4: `192.168.122.1` — typically assigned by virtualization tools (e.g., libvirt).
    
- No IPv6 address.
    
- Interface is up but has `NO-CARRIER`, which is expected unless a VM is currently using the bridge.

	