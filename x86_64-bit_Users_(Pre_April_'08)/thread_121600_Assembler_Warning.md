---
title: "Assembler Warning"
date: 2006-01-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by bkv2k on 2006-01-25
I just put an AMD64-based motherboard in my machine and loaded ubuntu.  It went unbelievably well.  I loaded NASM and tried a HelloWorld program using the following:

nasm -f elf hello.asm 

Assembled just fine.

g++ -Wall -s -nostartfiles hello.o

Linked just fine giving a.out and this warning:

warning: i386 architecture of input file 'hello.o' is incompatible with i386:x86-64

a.out runs as expected.  Is there something I should be doing that I'm not when I assemble/link?  And, is using gcc/g++ the way to link assembler files?

Thank for the help!

---

