---
title: "installing 32bit applications without chroot?"
date: 2008-10-28
forum: x86 64-bit Users
---

### Post by mustard675 on 2008-10-28
Ive searched this topic extensively and have been on the fence between double booting 32bit and 64bit on my AMD machine or installing a chroot in my 64bit environment. 

Kilz, i came across a reply you made almost two (2) years ago in this thread ([http://ubuntuforums.org/showthread.php?t=303472&highlight=chroot]("http://ubuntuforums.org/showthread.php?t=303472&highlight=chroot"))
> The Dapper chroot script that ravenon suggested is the easiest way to install a chroot. But be aware that a chroot is not necessary. It is a good idea if you plan on doing development or plan on installing hundreds of 32bit applications. Which most people will never need to do. But if you are not, it is realitivly easy to install 32bit applications without it.

I am looking to install ONE (1) 32bit application, not hundreds so it seems that you know something (a lot) I do not. I'm still fresh at ubuntu but hopefully "relatively easy" really means what it says. 

In particular i'm looking to install Boxee ([http://www.boxee.tv/]("http://www.boxee.tv/")). Any help or advice is appreciated.

Ubuntu 8.04 Hardy
AMD 64

Thanks!

---

### Post by Kilz on 2008-10-29
Yes, what I wrote about installing 32bit applications is still true. You should be able to install 32bit applications. Its actually easier now than when I wrote that.
[Getlibs]("http://ubuntuforums.org/showthread.php?t=474790&highlight=getlibs") is the reason. Cappy should get it into the main repositories, its that good. It helps 64bit users install the 32bit libraries that are sometimes needed.

1. First you force install the application. (never ever force libraries only applications)
2. Make sure ia32-libs is installed
3. Install getlibs
4. Then open a terminal and try and start it. If it says it cant find a library, use getlibs.

The application will start up and your done

---

### Post by Archmage on 2008-10-29
What is wrong with simply installing it from the repros? Or is this too easy?

---

