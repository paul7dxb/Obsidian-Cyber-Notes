Extract zlib
```bash
for z in *.zlib; do; zlib-flate -uncompress < "$z" > "${z%.zlib}" ; done
```