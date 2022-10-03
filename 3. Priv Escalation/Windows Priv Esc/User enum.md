### User enum
Current user’s privileges: `whoami /priv`
List users: `net users`
List details of a user: `net user username` (e.g. `net user Administrator`)
Other users logged in simultaneously: `qwinsta` (the `query session` command can be used the same way) 
User groups defined on the system: `net localgroup`
List members of a specific group: `net localgroup groupname` (e.g. `net localgroup Administrators`)

