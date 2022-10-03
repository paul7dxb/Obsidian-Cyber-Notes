### System info
`systeminfo`
`systeminfo | findstr /B /C:"OS Name" /C:"OS Version"`

`findstr /si password *.txt`
-s for subdirectories
-i for case insensitive

Get info on a service:
```
sc qc netlogon
```


### Patch level
`wmic qfe get Caption,Description,HotFixID,InstalledOn`


### Scheduled tasks
`schtasks /query /fo LIST /v`


***

## Services
Running services
```
wmic service get name,displayname,pathname,startmode
```
