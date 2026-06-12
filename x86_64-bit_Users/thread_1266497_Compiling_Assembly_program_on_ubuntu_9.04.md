---
title: "Compiling Assembly program on ubuntu 9.04"
date: 2009-09-14
forum: x86 64-bit Users
---

### Post by chandershivdasani on 2009-09-14
Hi,

I am trying to compile a small asm program on ubuntu. 

The source code is as follows:

[SIZE=-1].model small
.stack
.data
message   db "Hello world, I'm learning Assembly !!!", "$"

.code

main   proc
   mov   ax,seg message
   mov   ds,ax

   mov   ah,09
   lea   dx,message
   int   21h

   mov   ax,4c00h
   int   21h
main   endp
end main
[/SIZE]

I have saved the file as myproc.asm

I am compiling it using the following command:

tasm proc.asm

I am getting the following error

**Error** myproc.asm(1) junk at end of line, first unrecognized character is `s'

---

### Post by rCXer on 2009-09-14
How are you running tasm? Since there's no linux version of tasm and your code is for dos, are you using an emulator?

---

