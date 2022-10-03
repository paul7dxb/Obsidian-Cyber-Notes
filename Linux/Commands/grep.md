grep a string
```
grep "literal_string" filename
```
Can also use [[Regex]] for string 
- For advanced regex use `-oP`

grep string in multiple files:
```
grep "literal_string" filePattern
```

- Case insensitive: -i
- Recursive search: -r
- Full word not substrings: -w
- Show line number: -n
- Count number of matches: -c
- Show only match (not whole line): -o
- Show file names of matches (used when searching multiple files):
	- -l
- Invert search (grep lines that do not contain): -v
	- e.g display the lines which does not matches all the given pattern:
		- `grep -v -e "pattern" -e "pattern"`
- Display lines before/after grep:
	- N lines after: -A
		- `grep -A <N> "string" FILENAME`
	- N lines before: -B
	- N lines around: -C

Activate grep highlighting:
```
export GREP_OPTIONS='--color=auto' GREP_COLOR='100;8'
```

### Recursive grep
```
grep -r "texthere" .
```
