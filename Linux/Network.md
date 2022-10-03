### Network
`netstat -ano`
-   `-a`: Displays all active connections and listening ports on the target system.
-   `-n`: Prevents name resolution. IP Addresses and ports are displayed with numbers instead of attempting to resolves names using DNS.
-   `-o`: Displays the process ID using each listed connection.

### /etc/hosts
- Used to direct name based virtual hosting
- Add using a text editor or send striaght to file:
```
echo "10.129.136.91 unika.htb" | sudo tee -a /etc/hosts
```
