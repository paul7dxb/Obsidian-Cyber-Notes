Used to walk through assembly of a file

```
gdb <filename>
```

[[Assembly]]

Show code
```
list
```

Show CPU instructions
```
disas
```

Set command
Sets gdb to use the environment to use the absolute path of any executables we run: AKA it means any exploit you make inside gdb will work outside of gdb after doing that.

set exec-wrapper env -u LINES -u COLUMNS

## Finding an entry point
Using gdb
```
info files
```


-   Using `readelf`
    
    ```
    $> readelf -h /bin/ls
    ELF Header:
    Magic:   7f 45 4c 46 02 01 01 00 00 00 00 00 00 00 00 00 
    Class:                             ELF64
    Data:                              2's complement, little endian
    Version:                           1 (current)
    OS/ABI:                            UNIX - System V
    ABI Version:                       0
    Type:                              EXEC (Executable file)
    Machine:                           Advanced Micro Devices X86-64
    Version:                           0x1
    Entry point address:               0x40489c
    Start of program headers:          64 (bytes into file)
    Start of section headers:          108264 (bytes into file)
    Flags:                             0x0
    Size of this header:               64 (bytes)
    Size of program headers:           56 (bytes)
    Number of program headers:         9
    Size of section headers:           64 (bytes)
    Number of section headers:         27
    Section header string table index: 26
    ```
    
    So, the entrypoint address is `0x40489c`.
    
-   Using `objdump`
    
    ```
    $> objdump -f /bin/ls
    
    /bin/ls:     file format elf64-x86-64
    architecture: i386:x86-64, flags 0x00000112:
    EXEC_P, HAS_SYMS, D_PAGED
    start address 0x000000000040489c
    ```
    
    Again, the entrypoint is `0x000000000040489c`.

## Start at start and see what is happening
Show first 50 steps:
```
disas 0x40489c,+50
```