---
title: "R_X86_64_32 error when building software"
date: 2008-01-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by nr4ps on 2008-01-22
Hello,

I'm trying to build some code (a few modules from the framework available at [http://claraty.jpl.nasa.gov/man/software/download/index.php](http://claraty.jpl.nasa.gov/man/software/download/index.php)) but am running into difficulties that I think are caused by the fact that I'm running a 64-bit operating system (Ubuntu Gutsy).  I'm getting the following error:

/usr/bin/ld: ix86_linux_gcc/fdm.o: relocation R_X86_64_32 against `a local symbol' can not be used when making a shared object; recompile with -fPIC
ix86_linux_gcc/fdm.o: could not read symbols: Bad value

I have very little experience with Linux.  Is there some way to just install a 32-bit version of gcc so it just builds as it would on a 32-bit system?  Or would it be simpler to just give up and install 32-bit Ubuntu?

Thanks.

---

### Post by jeffus_il on 2008-01-22
The performance differences between 64 and 32 bit systems are small, there are a good few threads about it on the forum. So if you have the time, it's probably worth reinstalling.
There is the possibility of cross compiling, I haven't done it ,myself since 16 to 32 bit, You have to look at the gcc stuff.

---

### Post by nr4ps on 2008-01-22
Thanks for the advice.  I decided to go for it and just install the 32-bit version of Ubuntu.  Things are more or less working now.

---

