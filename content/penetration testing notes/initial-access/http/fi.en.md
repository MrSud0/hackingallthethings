---
  title: "File Inclusion"
---

# Intro
[TODO] In some scenarios, web applications are written to request access to files on a given system, including images, static text, and so on via parameters. Parameters are query parameter strings attached to the URL that could be used to retrieve data or perform actions based on user input. The following graph explains and breaking down the essential parts of the URL.

## Local File Inclusion (LFI)
### Checklist
- Find an entry point that could be via GET, POST, COOKIE, or HTTP header values!
- Enter a valid input to see how the web server behaves.
- Enter invalid inputs, including special characters and common file names.
- Don't always trust what you supply in input forms is what you intended! Use either a -browser address bar or a tool such as Burpsuite.
- Look for errors while entering invalid input to disclose the current path of the web application; if there are no errors, then trial and error might be your best option.
- Understand the input validation and if there are any filters!
- Try the inject a valid entry to read sensitive files
- Check the source code (if available) for potentially vulnerable use of functions
#### PHP
**Interesting functions**
- include
- require
- include_once 
- require_once 

### Techniques
- Bypass file type restriction for example, only .php files are allowed. Use null byte **%00 or 0x00** to disgard everything after it.(This is fixed on PHP 5.3.4 and up)
`../../../../../etc/passwd%00`
- Bypass keyword filtering. Use the null byte trick as above. Or the Directory trick
at the end of the request use **/.**
- Bypass string replacement, when the web app replaces **../** with empty space.
try **....//** instead of **../**.
- Bypass force read from a specific directory. Simply put the directory name before the **DIR/../**

## Path/Directory Traversal
A vulneabiloity that allows an attacker to read OS resources (e.g, Files). The attacker exploits this vulnerability by manipulating and abusing the web application's URL to locate and access files or directories stored outside the application's root directory.
### Checklist
#### PHP
**Interesting functions**
- User's input passed to fnction such as **file_get_contents** or similar.
### Techniques
use '../' to traverse to sensitive folders, to make sure you are in the root directory plenty '../', you can only get as deep as the root directory.

## Remote file inclusion
Inject a malicous URL in the application.
### Checklist
#### PHP
**Interesting functions**
- allow_url_fopen is on
### Techniques
- first test that you can upload a text file
- then upload a php reverse shell and have an netcat listener on [TODO] (redirect to shells page and netcat utils)

## Other resources
### Interesting paths in Linux
- /etc/issue
- /etc/passwd
- /etc/profile
- /etc/shadow
- /etc/group
- /etc/hosts
- /etc/motd
- /etc/mysql/my.cnf
- /proc/[0-9]*/fd/[0-9]*   (first number is the PID, second is the filedescriptor)
- /proc/self/environ
- /proc/version
- /proc/cmdline
- /root/.bash_history
- /var/log/dmessage
- /var/mail/root
- /root/.ssh/id_rsa
- /var/log/apache2/access.log

###  Interesting paths in Windows
- C:\boot.ini (file=../../../../boot.ini )

### Remediation
## Remediation (PHP)
- Keep system and services, including web application frameworks, updated with the latest version.
- Turn off PHP errors to avoid leaking the path of the application and other potentially revealing information.
- A Web Application Firewall (WAF) is a good option to help mitigate web application attacks.
- Disable some PHP features that cause file inclusion vulnerabilities if your web app doesn't need them, such as allow_url_fopen on and allow_url_include.
- Carefully analyze the web application and allow only protocols and PHP wrappers that are in need.
- Never trust user input, and make sure to implement proper input validation against file inclusion.
- Implement whitelisting for file names and locations as well as blacklisting.


## Sources
[tryhackme] https://tryhackme.com/room/fileinc
