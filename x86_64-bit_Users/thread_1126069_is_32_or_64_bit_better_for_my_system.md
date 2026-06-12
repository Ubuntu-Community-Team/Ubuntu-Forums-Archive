---
title: "is 32 or 64 bit better for my system?"
date: 2009-04-15
forum: x86 64-bit Users
---

### Post by zero777zero on 2009-04-15
how stable/usable is ubuntu 64bit? i'm considering switching over with 9.04 but i dont want to spend extra time in the command line.

here are my specs

processor
-2 CPUs
-Pentium(R) Dual-Core  CPU      E5200  @ 2.50GHz
-Frequency: 1200.000 MHz
-L2 Cache: 2048 KB

Ram: 3282 MiB

do all 32bit progs run in ubuntu 64?

---

### Post by fahadayaz on 2009-04-15
its perfectly stable. i've been on 64bit for a few releases now.
works a charm in Jaunty.... :)

---

### Post by Svensk023 on 2009-04-15
Yes, you should be able to run a 64-bit version of Ubuntu perfectly fine.

---

### Post by fahadayaz on 2009-04-15
>  do all 32bit progs run in ubuntu 64?

no, the application needs to specifically be compiled for the 64bit architecture. most apps already have a 64bit version, so you shouldn't run into much trouble.

---

### Post by Sef on 2009-04-15
Any particular application that you are worried about not having a 64-bit app?   Also it is possible to get a 32-bit app to run on a 64-bit system.

---

### Post by Yellow Pasque on 2009-04-15
> how stable/usable is ubuntu 64bit?
how stable/usable is ubuntu 32bit? ;)

> do all 32bit progs run in ubuntu 64?
Ideally, you won't need any. Did you specifically have something in mind?

---

### Post by youph on 2009-04-15
Except for the odd plugin, the old stigma of buggy drivers and other issues in amd64 linux is pretty much gone. The last issues I remember being a problem for me were flash for firefox and the nvidia drivers, but that was 6.x. Like the others mentioned, unless there is a specific application you need that isn't ported yet to amd64 (still a realistic possibility) you would be doing yourself a disservice running the 32 bit kernel. Modern motherboards all support 4+ gigs of ram and 64 bit code can be anywhere from 0-20% faster (more registers, faster system call interface etc.) 

If you're just running a standard install of Ubuntu I suggest you start out with 64 bit and revert in the unlikely event something isn't supported.

---

### Post by 3Miro on 2009-04-15
I was booting 64-32 bit for some time because of software and driver issues, but for months now I am running only 64 (on two machines).

As far as stability goes, it is the same as 32-bit.

---

### Post by zero777zero on 2009-04-15
thanks for the answers. i still have trouble compiling some software which is why i was hoping ubuntu64 has a 32bit compatibility layer. there are quite a few progs that i depend on which idk if i can find precompiled packages for. oh well, i'll try it out.

---

### Post by Dougie187 on 2009-04-15
AFAIK if you want to install a 32 bit app in 64 it is totally possible. you just have to install the 32 bit libraries. there are plenty of threads on this topic in here, so a quick search should get you some instructions.

---

### Post by jowilkin on 2009-04-15
If you don't want to mess around too much then just install the 32-bit version.  There are still some minor incompatibilities that may require a little messing around to fix.  You probably also won't notice the difference speedwise between the 32-bit and 64-bit versions.

As others have mentioned, at this point most 64-bit issues have been fixed or are pretty easy to fix.  But if you want the easy route, just install 32-bit.

---

### Post by stchman on 2009-04-15
> **zero777zero said:**
> how stable/usable is ubuntu 64bit? i'm considering switching over with 9.04 but i dont want to spend extra time in the command line.

here are my specs

processor
-2 CPUs
-Pentium(R) Dual-Core  CPU      E5200  @ 2.50GHz
-Frequency: 1200.000 MHz
-L2 Cache: 2048 KB

Ram: 3282 MiB

do all 32bit progs run in ubuntu 64?

I have been using 64 bit since Feisty.  It runs very well.  I am not 100% sure if your Pentium dual core is 64 bit capable.  If it is then use 64 bit.

Not all 32 bit, but most.  You will find that the Ubuntu repos give you pretty much all the software you need.

---

### Post by zero777zero on 2009-04-15
> **jowilkin said:**
> If you don't want to mess around too much then just install the 32-bit version.  There are still some minor incompatibilities that may require a little messing around to fix.  You probably also won't notice the difference speedwise between the 32-bit and 64-bit versions.

As others have mentioned, at this point most 64-bit issues have been fixed or are pretty easy to fix.  But if you want the easy route, just install 32-bit.

thanks for the replies. i'm hoping for ubuntu64 to have as few problems as the 32bit edition. i may try it out any and switch to ubuntu32 if necessary.

---

### Post by jespdj on 2009-04-15
> **zero777zero said:**
> do all 32bit progs run in ubuntu 64?
> **fahadayaz said:**
> no, the application needs to specifically be compiled for the 64bit architecture. most apps already have a 64bit version, so you shouldn't run into much trouble.
No, this is wrong. Applications **do not** need to be compiled specifically for the 64-bit architecture.

32-bit software also runs on 64-bit Ubuntu. In practice, you will most likely not need many 32-bit programs, because for most Ubuntu software there are native 64-bit versions available. Some proprietary programs like Skype and Google Earth are available only as 32-bit programs, and they can be installed on 64-bit Ubuntu without any problems. (For those two programs specifically, the [Medibuntu](http://medibuntu.org/) repository contains packages for 64-bit Ubuntu to install them).

---

### Post by NightwishFan on 2009-04-16
I would advise 64-bit. I have never run into problems, and 64-bit seems to hibernate better for me at least. ;)

As for 32-bit software. I believe you only need 64-bit kernel modules and the rest of your software (well the majority) can be 32-bit if it pleases you. As for needing 32-bit software, install what you need from the repos, and if anything is left over we will be glad to help you find it.

---

### Post by youph on 2009-04-16
> **zero777zero said:**
> thanks for the answers. i still have trouble compiling some software which is why i was hoping ubuntu64 has a 32bit compatibility layer. there are quite a few progs that i depend on which idk if i can find precompiled packages for. oh well, i'll try it out.

If you have a tar ball that won't compile on amd64 you can try passing -m32 as a linker option. A quick[ google search]("http://ubuntuforums.org/showthread.php?t=265585") or 6 and you'll be able to come on into the 64 bit world :)

---

