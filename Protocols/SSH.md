## Reverse SSH Tunnel
Specifies a given port on remote server is to be forwarded to given host and port on local side

- Use ss to determine potential TCP connection ports
[[ss]]
- Check which ports will be allowed through firewall
- On local machine set up ssh:
```
ssh -L <localport>:<sitetoaccess>:<remoteport> <username>@$TGT
ssh -L 10000:localhost:10000 <username>@$TGT
```
- Once established browse to `localhost:<port>` or `127.0.0.1:LOCALPORT`

## Troubleshoot
Unable to negotiate with 10.10.156.94 port 2222: no matching host key type found. Their offer: ssh-rsa
```
ssh -oHostKeyAlgorithms=+ssh-rsa james@$TGT -p 2222
```