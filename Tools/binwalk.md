Used to find embedded files in a file / program
```
binwalk <file>
```

Extract files
```
binwalk <file> -e
```

Not extracting certain files
```
binwalk --dd=".*" file_name
```