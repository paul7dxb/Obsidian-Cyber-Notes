Memory manipulation:
-   (Rb, Ri) = MemoryLocation[Rb + Ri]
-   D(Rb, Ri) = MemoryLocation[Rb + Ri + D]
-   (Rb, Ri, S) = MemoryLocation(Rb + S * Ri]
-   D(Rb, Ri, S) = MemoryLocation[Rb + S * Ri + D]

Move value x to registry %abc:
	`movl x, %abc`

Some other important instructions are:

-   _leaq source, destination: this instruction sets destination to the address denoted by the expression in source
-   _addq source, destination_: destination = destination **+** source
-   _subq source, destination_: destination = destination **-** source
-   _imulq source, destination_: destination = destination ***** source
-   _salq source, destination_: destination = destination **<<** source where **<<** is the left bit shifting operator
-   _sarq source, destination_: destination = destination **>>** source where **>>** is the right bit shifting operator
-   _xorq source, destination_: destination = destination **XOR** source
-   andq source, destination: destination = destination **&** source
-   _orq source, destination_: destination = destination **|** source