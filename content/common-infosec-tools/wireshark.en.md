---
title: "Wireshark"
---

#### Filters

ip.addr == IP_ADDRESS
tcp.port == 3389
not tcp.port == 3398
http.request.method == GET
ftp-data

#### operators
not
and
or
