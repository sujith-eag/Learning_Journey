
```bash
systemctl stop sshd
# or
service ssh stop
```

To close SSH Port

```bash
sudo iptables -A INPUT -p tcp --dport 22 -j DROP
```

Using UFW (Ubuntu Firewall)

```bash
sudo ufw deny 22
```

```bash
sudo systemctl status ssh
```

# IP Tables

```
sudo apt install iptables

iptables --version 
```
Used to configure IP Packet filtering and NAT rules of the linux kernel kirewall.
Used for monitering, filtering, and redirecting traffic

```
iptables [options] [chain] [command] [match] [target]
```

It contains Tables
Chains
Rules and 
Targets (IP)

### Rules
A

### Targets

Target is what happens after a packkt matche the rule criteria. 
Common targets include 

ACCEPT : Allows 
DROP : Discard packet without informming the sender 
REJECT : Discard and return an error response 
LOG :
SNAT :
DNAT :
MASQURADE :

To show all the activites
```
sudo iptables -L
```

To find the who is pinging
```
sudo tcptump -i eno1 icmp
```

To drop ping packets
```
sudo iptables -I INPUT -s 172.1.27.103 -j DROP
```

To ACCEPT
```
sudo iptables -I INPUT -s 172.1.27.103 -j ACCEPT
```

To Accept or drop All icmP PACKETS all PCs

```
sudo iptables -A INPUT -p ICMP -j DROP

sudo iptables -A INPUT -p ICMP -j ACCEPT
```




