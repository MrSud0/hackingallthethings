---
  title: "Server Side Request Forgery"
---
# Intro
SSRF stands for Server-Side Request Forgery. It's a vulnerability that allows a malicious user to cause the webserver to make an additional or edited HTTP request to the resource of the attacker's choosing.
# Background
Types of SSRF:
- Regular, information is returned to the user from the backend
- Blind, information is **not** returned to the user from the backend

# Discovery
Things that indicate a SSRF vulnerability.
- Full URLs used as part of a request's parameter
- Full Urls used in hidden fields of a form
- Partial Urls used as part of a request's parameter
- Url path used as part of request's parameter
# Exploitation
- Modify request parameters
- Modify request parameters using directory traversal to ignore certain portions of the request
- Modify request parameter to ignore a portion of the request by appending **&x=**, this way we fool the server to think the remaining of the URL is the value of parameter X, for example:
  - Benign request https://website.subdomain/item/2?server=api
  - Attacker request https://website.subdomain/item/2?server=server.website.subdomain/flag?id=9&x=
  - The server will run https://server.website.subdomain/flag?id=9&x=.website.subdomain/api/item?id=2
- Reveal credentials (e.g., keys) by completely changing the domain of the request, to hit an attacker owned domain

# Exploitation (Blind)
When the server does not reflect output back at you, you should use an external HTTP logging tool.
- Requestbin.com
- Burp Suite's Collaborator client
- Ngrok
- Webhook.site

# Evading SSRF Defenses
Usually defenses follow two approaches, **deny list** or **allow list.**
A **deny list** is where all requests are accepted apart from resources specified in a list or matching a particular pattern. For example, to bypass a deny list that includes localhost or 127.0.0.1 you can use alternatives such as
- 0
- 0.0.0.0
- 0000
- 127.1,
- 127.*.*.*
- 2130706433
- 017700000001
- or any domains that have a dns record which resolves to **127.0.0.1** such as **127.0.0.1.nip.io**
In cloud environments, t might be useful for the defendesr to block IP 169.254.169.254 which contains metadata for the dpeloyed cloud server.

An **allow list** is where all requests get denied unless they appear on a list or match a particular pattern, such as a rule that an URL used in a parameter must begin with https://website.domain. This can be easily bypassed by using an attacker onwed domain https://website.domain.attacker-domain.domain.

Another way to bypass both approaches is by utilizing redirect endpoints used by the target webapplication.
# Resources
https://tryhackme.com/room/ssrfqi
https://server.website.thm/flag&x=&id=9.website.thm/api/item?id=2
