# GDB Cheatsheet

## General

- `r`: Run the program.

- `c`: Continue running the program (after stopping at a breakpoint).

- `ni`: Next instruction.

- `si`: Step into.

- `disass main`: Disassemble the function `main`.

## Breakpoints

- `b main`: Set breakpoint at the function `main`.

- `b *main+15`: Set breakpoint at offset 15 of the function `main`. Find the offset by looking at the disassembly.

## Inspect values

- `p/u $rax`: Print register %rax as unsigned int.

- `p/x $rax`: Print register %rax as hex.

- `p (int)$rax`: Print register %rax as `int` (or any data type).

- `p (char*)$rax`: Use register %rax as a string pointer, print both the address and the string.
