---
title: "Can you run 32bit software in a 64bit environment? serious confusion"
date: 2006-02-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by ironfistchamp on 2006-02-14
Right I will start off by saying "yes I am new to linux". Next I will say I am running Ubuntu 5.10 64bit edition. 

The software that I want/need is 32bit and won't compile/install. Is there a way I can run them anyway. at one point I had SuSE 10 and that did 64 and 32 but I don't know why or how. Any help?

Thanks

Ironfistchamp

---

### Post by uniko on 2006-02-14
Yes, you can. I do it with chroot. Change all hoary references to breezy in this [how-to]("http://www.ubuntuforums.org/showthread.php?t=24575&highlight=chroot") if you want to install chroot-environment.

---

### Post by RAOF on 2006-02-14
You can.  You don't **need** to chroot, but it can make installing stuff less fiddley.  If you want help compiling stuff, we can give it.  Any reason why it won't compile to 64bit code?

But the very first thing you need to do before trying to compile anything is make sure you've got the "build-essential" package installed (sudo apt-get install build-essential) - that pulls in a basic build environment.  Without it, you don't have make, gcc, etc.

---

### Post by soccerboi on 2006-02-14
So will everything work almost like 32bit Ubuntu except faster then?  Is the wireless support any worse for 64bit ubuntu?  And will 32bit windows drivers work on 64bit ubuntu with ndis wrapper?

Thanks, Cory Roberts.

---

### Post by RAOF on 2006-02-14
[QUOTE=soccerboi]So will everything work almost like 32bit Ubuntu except faster then?  Is the wireless support any worse for 64bit ubuntu?  And will 32bit windows drivers work on 64bit ubuntu with ndis wrapper?

Thanks, Cory Roberts.[/QUOTE]
Almost everything will work like 32bit Ubuntu, except faster :)  There's still some stuff that takes more effort, because there isn't a 64bit version - wine, flash, and win32codecs mainly.

I've not tried wireless support.  I think it's more difficult under Ubuntu64, and I doubt if you can load 32bit windows drivers with the 64bit ndis wrapper.

---

### Post by soccerboi on 2006-02-14
Okay, thanks for the reply.  I'll just stick with the 32bit version for now.

---

### Post by ironfistchamp on 2006-02-16
Thanks for the help. The two things I want are two of the difficult ones u mentioned. I have the codecs but I need flash support and wine. Also CVS Cedega never works with 64bit distros. Any help?

Thanks

---

### Post by skylornova on 2006-02-16
[QUOTE=soccerboi]Okay, thanks for the reply.  I'll just stick with the 32bit version for now.[/QUOTE]

I don't blame you.  I had an awful time getting wireless to work with 64-bit, so I finally just went back to 32-bit.  Maybe I'll get brave and try it with a future version.

As far as speed differences, on my AMD64 laptop, I hardly notice a difference between the AMD64 and K7 kernels.

---

