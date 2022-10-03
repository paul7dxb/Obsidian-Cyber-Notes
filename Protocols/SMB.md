Supported by Windows not Linux

### SMBClient
List shares:
```
smbclient -L
smbclient -L \\\\<IP> -U guest
```

```
smbclient \\\\<IP>\\<share>
get <filename>
-N no password
```

└─$ smbclient -L \\\\10.129.57.14\\backups -U guest

[[nmap#nmap SMB]]

- To make compatible with NFS linux uses Samba
[[Samba]]