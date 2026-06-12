---
title: "run 32bit aplications in AMD64"
date: 2007-11-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by elo_sneeky on 2007-11-08
hi, i have ubuntu on my desktop and i'm having troubles running 32bit aplications on it... 
the release i have is ubuntu feisty, the version made especially for AMD64, and now there are some programs i want to run on it, even classes things, and i can't...
when i had installed ubuntu i couldn't install the normal version for all processors, so i had installed the version apropriated for my processor, and now i'm having troubles... 

What can I do???

---

### Post by Sef on 2007-11-08
What programs do you want to run?

---

### Post by Jouke74 on 2007-11-08
Install the IA32 libraries for starters.

---

### Post by elo_sneeky on 2007-11-08
i'm working with file systems on virtual disks...

---

### Post by Kilz on 2007-11-08
> **elo_sneeky said:**
> i'm working with file systems on virtual disks...

What applications are you trying to run on the 64bit install? or are these applications on virtual machines?

---

### Post by elo_sneeky on 2007-11-08
there's no apllications in virtual machine, i'm just compiling programs in C, and then run some programs, in C too, to format and work with a virtual disk... i'm using gcc and FUSE... 
when i try to compile those programs with a makefile, i see a list of warnings about all the .o files, saying that the input is not working with the output...

---

### Post by stmiller on 2007-11-08
Like the above said, install all of the ia32* packages.

Then you might possibly have to put 'linux32' in the command line before the executable.

```
$ linux32 program.sh
```

---

### Post by Jouke74 on 2007-11-09
It's hard to understand what you are trying to do. But for the compiling and probably also running (if your virtual space is not 32 bit) you need the 32 bit IA libraries and maybe the development versions too. Or, given that you are playing with the file systems, download the 64 bit source code for them (which again won't work on a 32 bit virtual machine / disk / whatever).

---

### Post by elo_sneeky on 2007-11-09
i had already installed all the IA32 libraries and i'm still having the same problem...
about the work i'm doing, teachers are only now trying to get me the code to work with 64bit processors...

---

### Post by hellmet on 2007-11-09
sry.. offtopic : The linux community should be prepared to answer more 64bit questions, since the usage of such systems has been on the rise..
I recently got my 64bit comp. and I had similar problems .. but ubuntu 64 works, while XP 64 doesn't.

---

