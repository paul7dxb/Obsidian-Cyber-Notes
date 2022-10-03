[Scripting Cheat Sheet](https://learnxinyminutes.com/docs/powershell/)

## PowerView
[Powerview GitHub](https://github.com/PowerShellMafia/PowerSploit/blob/dev/Recon/PowerView.ps1)

[PowerView Cheat Sheet](https://book.hacktricks.xyz/windows/basic-powershell-for-pentesters/powerview)

```powershell
#Import module
Import-Module .\powerview.ps1

# Get info on DC
Get-NetDomainController 

Get-NetGroupMember "Domain Admins"

# Find Available Shares
Find-DomainShare -CheckShareAccess

#Group Policy Info
Get-NetGPO

Get-NetDomainTrust

Get-NetUsers -Domain infra.munn.local

#List systems you can access as local admin
Find-LocalAdminAccess

#Basic user enabled info
Get-NetUser -UACFilter NOT_ACCOUNTDISABLE | select samaccountname, description, pwdlastset, logoncount, badpwdcount 
```


### Port Scanner

```Powershell
$system_ports = Get-NetTCPConnection -State Listen
$text_port = Get-Content -Path C:\Users\Administrator\Desktop\ports.txt

foreach($port in $text_port){
    if($port -in $system_ports.LocalPort){
        echo $port
     }
}
```

### Find file containing a keyword
```powershell
$path = "C:\Users\Administrator\Desktop\emails"
$keyword = "password"
$result = Get-ChildItem -Path $path -Recurse | Select-String $keyword
$result
```

### Port Scanner
```powershell
for ($i = 130; $i -lt 141; $i++){
    Test-NetConnection localhost -Port $i
}
```

