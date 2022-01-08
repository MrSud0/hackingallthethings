---
  title: "DNS"
---

# Google dorking
-site: www.domain.com site:*.domain.com

# CT logos
Certificate Transparency logs
[crt](crt.sh)
[transparencyreport](https://transparencyreport.google.com/https/certificates)

# NSLookup

`nslookup OPTIONS DOMAIN_NAME SERVER`
- OPTIONS contains the query type as shown in the table below. For instance, you can use A for IPv4 addresses and AAAA for IPv6 addresses.
- DOMAIN_NAME is the domain name you are looking up.
- SERVER is the DNS server that you want to query. You can choose any local or public DNS server to query. Cloudflare offers 1.1.1.1 and 1.0.0.1, Google offers 8.8.8.8 and 8.8.4.4, and Quad9 offers 9.9.9.9 and 149.112.112.112. There are many more public DNS servers that you can choose from if you want alternatives to your ISP’s DNS servers.

Query type Result
- A IPv4 Addresses
- AAAA 	IPv6 Addresses
- CNAME 	Canonical Name
- MX 	Mail Servers
- SOA 	Start of Authority
- TXT 	TXT Records

`nslookup -type=A hackingallthethings.com 1.1.1.1`

# Dig
`dig domain MX`
`dig @1.1.1.1 domain MX`

# DNSDumpster
