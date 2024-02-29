---
layout: post
title: Getting Started with Assembler for Reverse Engineering
date: 2024-02-28
categories: [reverse-engineering, assembler]
tags: [reference]
---

Mostly notes for my self, but this is one thing I am interested in learning about. Thanks to my friend M who gave me alot of these links!


[0xinfectionl - Reverse Engineering for Everyone](https://0xinfection.github.io/reversing/) - x86, ARM-32, x64, ARM-64, Pico Hacking

[Cool tool](https://defuse.ca/online-x86-assembler.htm#disassembly) to paste in some assembler and convert from mnomics to binary and vice versa

[Microcorruption Game](https://microcorruption.com/) - haven't played alot, but could be fun.

[Intel® 64 and IA-32 Architectures Software Developer’s Manual Combined Volumes: 1, 2A, 2B, 2C, 2D, 3A, 3B, 3C, 3D, and 4](https://www.intel.com/content/www/us/en/content-details/782158/intel-64-and-ia-32-architectures-software-developer-s-manual-combined-volumes-1-2a-2b-2c-2d-3a-3b-3c-3d-and-4.html?wapkw=intel%2064%20and%20ia-32%20architectures%20software%20developer%27s%20manual&docid=782158)

[Exercises in Reverse Engineering](https://challenges.re/) - something to get started on

Tools to get familiar with:
* [Ghidra](https://ghidra-sre.org/)
* [Ida FREE](https://hex-rays.com/ida-free/)
* [Radare2](https://github.com/radareorg/radare2)
* [GDB: The GNU Project Debugger](https://www.sourceware.org/gdb/)


## Syntax Styles

### Intel Syntax

* first operand is the `destination`, and the second operand is the `source`
* No prefix on registers or immediates
* Immedates are suffixed with `h` and `b`
* If the first hexadecimal digit is a letter then the value is prefixed by a `0`.
* Base registers use `[ ]`

```
addl eax, [ebx]
mov eax,1

```

### AT&T Syntax

* Registers prefixed with `%`
* Immediates prefixed with `$`, hex is prefixed with 0x
* First operand is the `source`, and the second operand is the `destination`
* Base registers use `( )`

```
addl (%ebx), %eax
movl $1,%eax
```

More [details here](https://imada.sdu.dk/u/kslarsen/dm546/Material/IntelnATT.htm)

