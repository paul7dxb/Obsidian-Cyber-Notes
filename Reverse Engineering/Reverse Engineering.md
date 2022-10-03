## radare2 framework
Cheatsheet:
https://scoding.de/uploads/r2_cs.pdf

Open debuging:
```
r2 -d ./<FILENAME>
```

Help / Help for specific feature:
```
?
?a
```

Analyze the program:
```
aa
```

After analysis:
	List Functions (analyse function list):
		`afl`
		`afl | less`
	Print Disassembly Function:
		`pdf @<FUNCTION>`
	Breakpoint:
		`db <0xPOINT>`
		Running pdf on the function after will show breakpoint
	Run program to next break
		`dc`
		Next instruction:
			`ds`
	View variable:
		`px @<MEMORY-ADDRESS>`
	View register:
		`dr`
	Reload program:
		`ood`

| Initial Data Type | Suffix | Size (bytes) |
| --- | --- | --- |
| Byte | b | 1 |
| Word | w | 2
| Double word | l | 4
| Quad | q | 8
| Single precision | s | 4
| Double precision | l | 8 |

## Assembly
[[Assembly]]



## .NET Framework reverse engineering
https://github.com/icsharpcode/ILSpy
https://www.jetbrains.com/decompiler/

