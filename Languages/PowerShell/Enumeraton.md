## Users and Groups

- Get local users:

	```PowerShell
	Get-LocalUser | select * 
	```


- Find user by SID:
	```PowerShell
	Get-LocalUser | Where-Object -Property SID -eq "<SIDVALUE>" 
	```


- Find users with password required set to false
	```PowerShell
	Get-LocalUser | Where-Object {$_.PasswordRequired -match "False"} 
	```

- Get local users
	```PowerShell
	(Get-Net-User).name
	# Get last logon times
	Get-NetUser | select -ExpandProperty lastlogon
	```

- Get local groups
	```PowerShell
	Get-LocalGroup | select * 
	```
	```PowerShell
	Get-LocalGroup | select -Property name, SID
	```


## Network

- Get IP info
	```Powershell
	Get-NetIPAddress
	```

- Port information (like netstat)
	```Powershell
	Get-NetTCPConnection
	```

- Ping address range
	```powershell
	1..15 | %{echo "10.0.2.$_"; ping -n 1 10.0.2.$_ | Select-String ttl}
	```

- Port scan
	```powershell
	1..1024 | %{echo ((New-Object Net.Sockets.TcpClient).Connect("10.0.2.8", $_)) "Open port on - $_"} 2>$null
	```

## System
- Patch history
	```Powershell
	Get-Hotfix
	```

- View Scheduled Tasks
	```Powershell
	 Get-ScheduledTask
	```

- Get security descriptor like owner
	```Powershell
	get-acl C:\
	```

## Processes

- Start a process or application
	```powershell
	start-process notepad.exe
	```

- Show running processes
	```Powershell
	get-process -name <processname>
	```

## Misc

- Find files containing API_KEY
	```Powershell
	Get-ChildItem -path C:\Users -Recurse | Select-String "API_KEY" -List
	```


- Heading
	```Powershell
	
	```