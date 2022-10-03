Load scan
```
sudo nmap -sV -O -T4 -p- $TGT
```

```
sudo nmap -sV -T4 $TGT
sudo nmap -A -T4 $TGT -oA nmapOutput
sudo nmap -Pn -sS -sV -T4 $TGT
```

Web enumeration
```
nmap -sV --script=http-enum -p 80 $TGT
```

| nmap flag | Description |
| --- | ---------- |
| -sV | Attempts to determine the version of the services running |
| -Pn | Disable host discovery and just scan for open ports |
| -A | Enables OS and version detection, executes in-build scripts for further enumeration |
| -sC | Scan with the default nmap scripts | 
| -v | Verbose mode | 
| -sU | UDP port scan | 
| -sS | TCP SYN port scan | 
| -p or -p- | Port scan for port or scan all ports |
| -O | OS detection |
| -Pn | Treat host as online (ignore discovery) |
| -oA | Output all three types |
|-oN|Output normal type|


### Scripts
Web
```
sudo nmap -p 80,443 --script http* $TGT -T4
nmap -sV --script=http-enum $TGT

#Test which methods can be used
nmap --script http-methods <target>
nmap --script http-methods --script-args http-methods.url-path='/website' $TGT
```

Brute force DNS
```
nmap -p 53 --script dns-brute <domain>
```

### nmap SMB
```
nmap -p 445 --script=smb-enum-shares.nse,smb-enum-users.nse 10.10.214.122
```

