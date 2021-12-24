---
  title: "SMB"
  weight: 5
  chapter: true
---
SMB TEST
https://www.hackingarticles.in/a-little-guide-to-smb-enumeration/nmb

#enumerate hostnames
nmblookup -A 192.168.1.17
nbtscan 192.168.1.17
nmap --script nbstat.nse 192.168.1.17
smbclient -L 10.10.138.4 -N

enum4linux -a 10.10.127.245 /tmp/enum4linux.txt

# enumerate shares
smbmap -H


#connect to share share
smbclient //10.10.138.4/nt4wrksv


# After connection
