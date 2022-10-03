-   ? The preceding item is optional and matched at most once.
-   * The preceding item will be matched zero or more times.
-   + The preceding item will be matched one or more times.
-   {n} The preceding item is matched exactly n times.
-   {n,} The preceding item is matched n or more times.
-   {,m} The preceding item is matched at most m times.
-   {n,m} The preceding item is matched at least n times, but not more than m times.

### Regex Examples

- Everything between square brackets:
	- `\[(.*?)\]`
		-   `\[` : `[` is a meta char and needs to be escaped if you want to match it literally.
		-   `(.*?)` : match everything in a non-greedy way and capture it.
- Get all between > and <, starting with a non white space followed by a space, then not a "<" 0 or more times:
	- `grep -oP "(\>)(\S\s)([^<]*)(\<)" drawing | tr -d '>< \n'