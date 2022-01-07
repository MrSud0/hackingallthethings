---
  title: "Network Enumeration"
---
This section focuses on Host Discovery and Port Scanning.

# Intro
# Techniques


# Host Discovery
Tools for host discovery, and a few examples of usage.

### Ping
Linux
`ping -c 10 IP`
Windows
`ping -n 10 IP`

### Traceroute
traceroute
`telnet IP`
tracert
`tracert IP`

### NMap
ARP Scan
`nmap -PR -sn IP`

#### ICMP scans
ICMP Scan focuses on different types of ICMP packets.

Echo
`nmap -PE -sn MACHINE_IP/24`
ICMP Timestamp
`nmap -PP -sn 10.10.68.220/24`
ICMP Address Mask
`nmap -PM -sn MACHINE_IP/24`
TCP SYN
`nmap -PS -sn MACHINE_IP/24`
TCP ACK
`sudo nmap -PA -sn MACHINE_IP/24`
UDP Ping
`sudo nmap -PU -sn 10.10.68.220/24`

### ARP-Scan
`arp-scan -I eth0 -l`
### Mass scan
`masscan MACHINE_IP/24 -p80,443`


# Port Scanning

### Netcat
Connect mode
`nc IP PORT`
Listen mode
`nc -nvlp`

### NMap
### Telnet

# Resources
