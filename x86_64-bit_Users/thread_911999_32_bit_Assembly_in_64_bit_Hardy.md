---
title: "32 bit Assembly in 64 bit Hardy"
date: 2008-09-06
forum: x86 64-bit Users
---

### Post by S3TH88 on 2008-09-06
In my CS class this semester we're learning about assembly.  My first lab consisted of an assembly file, a c file and a makefile to link them together.  The lab was online, so I tried it from my own computer (running 64 bit Hardy Heron) and got this error:

```

$ make
gcc -Wall -c asm.s -o asm.o
asm.s: Assembler messages:
asm.s:9: Error: suffix or operands invalid for `push'
asm.s:13: Error: suffix or operands invalid for `pop'
make: *** [asm.o] Error 1

```

When I ran the make file in the computer lab it worked fine.
I have heard this is attributed to running 32 bit assembly on a 64 bit OS.  I'm pretty new to Ubuntu, and Linux in general and am not sure how to get it working.  Do I need to download some library or something?  Any help is appreciated. Thanks.

---

### Post by Yellow Pasque on 2008-09-06
Try installing the gcc-multilib package and using the -m32 gcc flag

---

### Post by S3TH88 on 2008-09-06
First, thanks for the quick reply.

It compiles and works when I type:
```

$ gcc -m32 cfile.c asm.s

```

but is there any way to use the makefile?  If I just type make or make -m32 it still gives an error.

---

### Post by IntuitiveNipple on 2008-09-06
There are several options. Specify an *override* on the command-line:
```

make CFLAGS=-m32

```
Add the option into the Makefile:
```

#!/usr/bin/make
CFLAGS += -m32

```

You might want to get more sophisticated with the Makefile, in which case read the [GNU make manual](http://www.gnu.org/software/make/manual/make.html). For example, some Makefiles will detect the bit-ness of the architecture although this is more often done via a **configure** or **autoconf** or **automake** script.

---

