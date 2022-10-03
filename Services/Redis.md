An in-memory database

Connect to database:
```
redis-cli -h $TGT
```

Once connected:

Show info:
```
INFO
```

See all keys:
```
keys *
keys <pattern>
```

Display key from above:
```
MGET <key>
```