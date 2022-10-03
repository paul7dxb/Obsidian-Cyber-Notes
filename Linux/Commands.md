### Escape char in command line
`./` e.g `./-file00`

### Find file
```
find . -name "flag2.txt" 2>/dev/null
find / -name "flag4.txt" 2>/dev/null
```

```
grep . <filename>
```

### System Info
`systeminfo`

### Show file/folder structure:
```
tree
```


### Kill a specific process using a given port
```
sudo fuser -k 445/tcp
```

You can use the following trick to easy navigate and select paths or others args # $_ takes the last argument of the last simplec command executed 
```
cd $_   
```

For example 
```
mkdir my-folder && cd $_
```

You can use xclip to automate clipping # Can be usefull for long outputs (enum4linux, privcheck...) 
```
cat /etc/resolv.conf | xclip -sel clip  
```

You can even create aliases 
```
alias toclip="xclip -sel clip" 
cat /etc/resolv.conf | toclip
````

### Reverse a string
```
cat <file> | rev
```

### Delete Folder and Contents
```
rm -rf <foldername>
```

### wget
Mirror entire site
```
wget -m [url]
```
