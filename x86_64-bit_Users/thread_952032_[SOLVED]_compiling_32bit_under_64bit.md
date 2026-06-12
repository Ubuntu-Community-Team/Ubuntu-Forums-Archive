---
title: "[SOLVED] compiling 32bit under 64bit"
date: 2008-10-18
forum: x86 64-bit Users
---

### Post by sfrank on 2008-10-18
Hi,

I'm trying to build a program that currently runs only under 32bit Linux (since not all 32bit assumptions have been ironed out) under my amd64 home machine in intrepid amd64.

Having installed all necessary libs32 and fiddled with several gcc and ld flags I thought that a should have a clean and continuous 32bit build all the way. However, one of the first steps in the bootstrap process of this build  is linking a couple of obj-files. The linking operations failes with the following error:

ld: Relocatable linking with relocations from format elf32-i386 (OCS/BUILTIN-raw.o) to format elf32-i386 (OCS/BUILTIN.o) is not supported

which baffles me quite a bit since both source and target obj-file are of the same format elf32-i386. I also poked at the source objs to make sure they are indeed elf32-i386 but everything was fine on this side.

Anybody an idea what's going on? 

Thanks a lot,
Stephan

---

### Post by sethvath on 2008-10-19
Did you try getlibs to resolve the 32 bit dependencies?

sudo apt-get install getlibs
getlibs /path/to/binary

---

### Post by Yellow Pasque on 2008-10-19
Using an -fPIC flag when compiling those libraries will probably take care of the error.

---

### Post by sfrank on 2008-10-20
> **sethvath said:**
> Did you try getlibs to resolve the 32 bit dependencies?

sudo apt-get install getlibs
getlibs /path/to/binary

Hi,

at this point of the bootstrap process there are no external dependencies (well apart from the standard C library) so this is really a linker issue where ld is not being able to deal with the provided formats (though it really should be)

But thanks for the suggestion.

Regs,
Stephan

---

### Post by sfrank on 2008-10-20
Hi,

unfortunately -FPIC didn't make any difference. I think I'm giving up now...

Regards,
Stephan

---

### Post by jespdj on 2008-10-20
Note: It is not -FPIC, but -fPIC

-F is not the same as -f

---

### Post by sfrank on 2008-10-20
> **jespdj said:**
> Note: It is not -FPIC, but -fPIC

-F is not the same as -f

Yes, sorry, that was just a typo in my reply. My make-script uses the correct option -fPIC though that does not change anything in the ld behaviour (though the obj have different sizes now).

For the moment I have worked around the issue by not using ld but by employing gcc with the -combine option (and without -fPIC) to compile all the files together, which appears to work.

Thank you all for time and suggestions and I hope my work-around will be helpful to others.

Best regards,
Stephan

---

