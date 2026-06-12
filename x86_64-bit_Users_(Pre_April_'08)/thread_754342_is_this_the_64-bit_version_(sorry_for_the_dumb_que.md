---
title: "is this the 64-bit version (sorry for the dumb question)"
date: 2008-04-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by Cr0n_J0b on 2008-04-13
uname -a

Linux 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux

I'm having issues running a particular program, and I think it might be because I've loaded the 64-bit version instead of the 32-bit.

---

### Post by jrharvey on 2008-04-13
what program is it? I think there is a way to force the architecture but it probably depends on the program.

---

### Post by colo on 2008-04-13
The "i686" in the identifying string suggests this is an IA32(therefore non-x86_64)-build.
`uname -m` is suitable for checking arch alone.

---

### Post by Cr0n_J0b on 2008-04-13
uname -m 

i686

So you are saying that the i686 architecture is NOT 64-bit.  ok, well then I'm not sure what's going on.  The program is a little utility for looking up pgp keys.  I picked it up a few years back and have never had any issues with it.  I know that I ran it on fiesty just fine...but now when i run it from the terminal I get nothing.

sudo ./pgpkeyper

just goes back to the prompt without outputting anything.  There is no man or anything for the program, so i usually just type /? or --help and it tells me what to do.  but nothing happens now.  That's why I thought this was 64-bit.

---

### Post by utUtu on 2008-04-13
> **Cr0n_J0b said:**
> uname -m 

i686

So you are saying that the i686 architecture is NOT 64-bit.  ok, well then I'm not sure what's going on.  The program is a little utility for looking up pgp keys.  I picked it up a few years back and have never had any issues with it.  I know that I ran it on fiesty just fine...but now when i run it from the terminal I get nothing.

sudo ./pgpkeyper

just goes back to the prompt without outputting anything.  There is no man or anything for the program, so i usually just type /? or --help and it tells me what to do.  but nothing happens now.  That's why I thought this was 64-bit.

If you have the 64bit Ubuntu installed, you should see something like this

```
ututu5@kubian01:~$ uname -a
Linux kubian01 2.6.24-16-generic #1 SMP Thu Apr 10 12:47:45 UTC 2008 x86_64 GNU/Linux

ututu5@kubian01:~$ uname -m
x86_64
mika5@kubian01:~$        ]
```

---

### Post by scarrabri on 2008-04-14
Hi i dont think this a dumb question,because i too am not sure whch is 64 bit, every thing i see for 64 bit is amd 64,so where is the 64 bit for intel,or dont we get it ,very best wishes ,i am using ubuntu 64 ,but have just instaled ubuntu studio which is brilliant,i hope that is 64 ,scarrabi:lolflag:

---

### Post by jespdj on 2008-04-14
> **scarrabri said:**
> ... every thing i see for 64 bit is amd 64,so where is the 64 bit for intel,or dont we get it ,
The [download page]("http://www.ubuntu.com/getubuntu/download") quite clearly says: "64bit AMD **and Intel** computers". The 64-bit version is for newer AMD and Intel processors, not just for AMD processors.

---

### Post by jamesford on 2008-04-14
i guess its called amd64 cos the architecture was invented by amd (?) and later adopted by intel as well.

---

### Post by scarrabri on 2008-04-15
> **jespdj said:**
> The [download page]("http://www.ubuntu.com/getubuntu/download") quite clearly says: "64bit AMD **and Intel** computers". The 64-bit version is for newer AMD and Intel processors, not just for AMD processors.  Sorry ,but on the  cd i had it never said intel or amd,but the fact it worked was good, thank you for your time scarrrabri:guitar:

---

