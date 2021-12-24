---
  title: "FTP"
  weight: 5
  chapter: true
---
# nmap specific scripts for FTP

nmap -n -Pn -p21 -vv -sV --script=tftp-enum.nse,ftp-vuln-cve2010-4221.nse,ftp-vsftpd-backdoor.nse,ftp-syst.nse,ftp-proftpd-backdoor.nse,ftp-libopie.nse,ftp-brute.nse,ftp-bounce.nse,ftp-anon.nse IP

# GET
wget -m ftp://netmon.htb/ProgramData/Paessler

# PUT
put
