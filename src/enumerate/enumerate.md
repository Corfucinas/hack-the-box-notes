# Enumerate

## command

```bash
ports=$(nmap -p- --min-rate=1000 -T4 10.10.10.27 | grep ^[0-9] | cut -d '/' -f 1 | tr '\n' ',' | sed s/,$//)
nmap -sC -sV -p$ports 10.10.10.27
```

## See if anonymous access has been permitted

```bash
smbclient -N -L \\\\<IP_ADDRESS>\\
```

## Accessing

```bash
smbclient -N \\\\<IP_ADDRESS>\\<FOLDER>
```
