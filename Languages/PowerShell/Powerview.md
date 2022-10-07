Get-NetGroup -GroupName *
Get Operating systems on domain
```
Get-NetComputer -fulldata | select operatingsystem
```

Get all users
```powershell
Get-NetUser | select cn
```

Get-NetUser -SPN | ?{$_.memberof -match 'Domain Admins'}

