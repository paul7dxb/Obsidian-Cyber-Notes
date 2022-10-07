### RDP with xfreerdp
```bash
xfreerdp -v:10.10.4.182 /cert:ignore /u:jack
```

Login with password to THM domain
```bash
xfreerdp -v:10.10.150.211 /cert:ignore /u:THM\\Administrator /p:Password321
```

### NetCat
Netcat:
target:
(May need to be in /tmp for write permissions)
`nc -l -p 1337 > LinEnum.sh`
host:
`nc -w -3 10.10.30.87 1337 < LinEnum.sh`

Find what is using port
```
lsof -ti:PORT
lsof -ti:5901 | xargs kill -9
```

### Delete Tunnel
```
ifconfig $tunnel_id down
iptunnel del $tunnel_id
```