---
title: "64bit Assembly"
date: 2008-08-01
forum: x86 64-bit Users
---

### Post by DarkW0lf on 2008-08-01
I have tried this two ways:

Adapting 32 bit code for 64 bit compilation.
Compiling on 64 bit arch for 32 bit target.

Can't get either to work.
First is probably my fault and I am forgetting something that needs changed. So I am trying the second option but anything I compile segfaults. as doesn't display an error during compiling and ld warns that I am compiling for 32 bit on arch that is 64 bit, app will segfault if I attempt to run it.

HLA (32 bit) will run on AMD64 (xubuntu) but how do you compile a 32 bit source on a 64 bit machine ?

---

### Post by John.Michael.Kane on 2008-08-01
I might be mistaken but you may need to pass -m32 flag, and you might need to install the gcc-multilib or gcc-4.2-multilib packages, as well.

---

### Post by Yellow Pasque on 2008-08-02
I was a little confused by the title. You're just trying to compile C code, correct? As J.M.K said, sudo apt-get install gcc-multilib (gets the multilib package for whatever version of gcc you have set as the default) and use the -m32 flag.

---

### Post by BGFG on 2008-08-02
My experience with 32 on 64 was this: 
```

This is my first "howto", and it's very easy:

1. $apt-get install linux32 libc6
2. Download the .deb package from http://www.avast.com/eng/download-av...x-edition.html
3. Register you license from http://www.avast.com/i_kat_207.php?lang=ENG
4. Install it: sudo dpkg --force-architecture -i avast4workstation_VERSION_i386.deb

Everytime you wanna scan: $linux32 avastgui

```

Easy to follow and it worked...

---

### Post by elmoosecapitan on 2008-08-02
-m32 (Works for my makefile)

---

### Post by DarkW0lf on 2008-08-16
I thought I had tried -m32 before, it compiled but did not link properly.
Machine is out being repaired so I'll have to try again later.

No, I am not trying to compile C or install avast (not sure who BGFG is replying to).

---

### Post by Yellow Pasque on 2008-08-16
> No, I am not trying to compile C
:confused: Then what are you trying to compile? You don't compile assembly code; you **assemble** it into object file(s) and link it. That's why we thought you were talking about C.

Are you using nasm?

---

### Post by DarkW0lf on 2008-08-22
compile/assemble/build/whatever

I am using as (Gas) on AMD64, -m32 is not being recognized by as as a parameter.

For example, I am trying to build the code from the Programming from the Ground Up book. Somehow I got the first two (no parameters needed) but not the third (the power example).

---

### Post by DarkW0lf on 2008-12-26
--32 works as a parameter for as and it will compile for 32bit target but ld still will not link. (not sure what -m32 is supposed to be)

I tried three targets for ld: elf32_i386, a.out-i386-linux, and i386linux and none will link to a 32bit target on a 64bit machine. I either get a target not found or an error that I am on a 64bit platform.

---

### Post by Yellow Pasque on 2008-12-26
I would look into setting up a 32-bit chroot environment to do your assembly.

---

### Post by tomdkat on 2008-12-28
> **Temüjin said:**
> I would look into setting up a 32-bit chroot environment to do your assembly.
Or make a 32-bit Linux targeted cross compiler and use that to generate 32-bit executables or object modules.

Peace...

---

### Post by DarkW0lf on 2009-01-09
passing --32 to as will compile code and passing -m elf_i386 to ld will link but when attempting to execute the app bash tells me permission is denied. (I do own and have permissions set on app but bash says permission is denied)

---

