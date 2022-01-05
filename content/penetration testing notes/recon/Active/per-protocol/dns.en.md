---
  title: "DNS"
---
DNS Records; NS-Nameserver records contain the name of the authoritative servers hosting the DNS records for a domain
A-Also known as a host record, the “a record” contains the IP address of a hostname (such as www.google.com)
MX-Mail Exchange records contain the names of the servers responsible for handling email for the domain. A domain can contain multiple MX records
PTR-PointerRecords are used in reverse lookup zones and are used to find the records associated with an IP address.
CNAME-Canonical Name Records are used to create aliases for other host records.
TXT-Text records can contain any arbitrary data and can be used for various purposes, such as domain ownership verification.

# Lookup
 By default host command searchs for the A record

`host DOMAINNAME`

Other records can be specified

`host -t mx DOMAINNAME`

#### Forward lookup brute force
Example for checking if a hostname exists under a domain and returning its IP

`for ip in $(cat list.txt); do host $ip.domain; done`

#### Reverse lookup brute force
Example looking in a set of IPs and filtering out the invalid responses

`for ip in $(seq  50 100); do host 10.10.10.$ip; done | grep -v "not found"`

# Subdomain enumeration
DNSRecon is  an  advanced,  modern  DNS  enumeration  script  written  in  Python.  Running dnsreconagainst megacorpone.com using the -doption to specify a domain name, and -tto specify the type of enumeration to perform (in this case a zone transfer), produces the following output:

`dnsrecon -d megacorpone.com -t axfr`

To begin the brute force attempt, we will use the -doption to specify a domain name, -Dto specify a file name containing potential subdomain strings, and -tto specify the type of enumeration to perform (in this case brtfor brute force)

`dnsrecon -d megacorpone.com -D ~/list.txt -t brt`

#### Sublist3r.py
Another brute forcing tool written in Python

`sublist3r.py -d megacorpone.com`

#### ffuf
Domain discovery with ffuf

`ffuf -w /usr/share/wordlists/SecLists/Discovery/DNS/namelist.txt -H "Host:FUZZ.acmeitsupport.thm" -u http://10.10.160.190 -fs 2395`


# Zone transfer
A zone transfer is basically a database replication between related DNS servers in which the zone fileis copied from a master DNS server to a slave server.

`host -l <domain name> <dns server address>`