# Format String Attack — CS442 Software Security

Lab assignment for **CS442: Software Security**, College of Computer and Information Sciences, Imam Mohammad Ibn Saud Islamic University (First Semester 2025-2026).

## Overview

This assignment demonstrates a **format string vulnerability**, where a program that passes user input directly to a `printf`-family function can be exploited to read or write arbitrary memory using specifiers like `%x` and `%hhn`.

## Steps

1. **Identify the target address**
   Located the target memory address and broke it down byte by byte to plan the write.

2. **Determine the write order**
   Since `%hhn` writes a single byte at a time, worked out the ascending byte order needed and arranged the four target addresses accordingly.

3. **Calculate the padding**
   Counted the characters printed before the first `%hhn` (addresses, separators, and format specifiers) to know the starting offset.

4. **Compute the values for each `%.Nx` specifier**
   Converted the target hex bytes to decimal and calculated the padding width needed before each `%hhn` so each byte is written with the correct value.

5. **Build and run the exploit**
   Disabled address space layout randomization (ASLR), compiled the vulnerable program, and ran the crafted input through it.

## Result

The target variable's value was successfully overwritten with the intended byte sequence, confirming the format string write worked as planned.

## Environment

- GDB for debugging and memory inspection
- A vulnerable C program with a format string bug
- Shell commands to build the exploit input

## Note

This exploit was built and run in an isolated lab environment for educational purposes, as part of a university course on software security.
