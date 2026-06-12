---
title: "wine install help"
date: 2007-08-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by lcolson on 2007-08-02
I am following the directions for installing 32 bit wine on a 64 bit system here:

[http://wiki.winehq.org/WineOn64bit#head-08d4087d863019523214064680fcf26721c9a1af](http://wiki.winehq.org/WineOn64bit#head-08d4087d863019523214064680fcf26721c9a1af)

But am not able to get any farther than the fourth greyed box which ends with the command:

sudo ln -s libGLU.so.1 libGLU.so

My problem is that I can't figure out how to configure it.  Any ideas?  Is there an easier way to install wine?

---

### Post by John.Michael.Kane on 2007-08-02
Theres a wine repo [Wine for Ubuntu, Debian, and Debian-based distributions]("http://www.winehq.org/site/download-deb"). I would try this method before compiling from source.

---

### Post by Kilz on 2007-08-02
> **lcolson said:**
> I am following the directions for installing 32 bit wine on a 64 bit system here:

[http://wiki.winehq.org/WineOn64bit#head-08d4087d863019523214064680fcf26721c9a1af](http://wiki.winehq.org/WineOn64bit#head-08d4087d863019523214064680fcf26721c9a1af)

But am not able to get any farther than the fourth greyed box which ends with the command:

sudo ln -s libGLU.so.1 libGLU.so

My problem is that I can't figure out how to configure it.  Any ideas?  Is there an easier way to install wine?
There is a 64bit package of wine for Feisty, [take a look here to get it]("http://wine.budgetdedicated.com/apt/pool/main/w/wine/").  If you are runing an older version of Ubuntu like Dapper or Edgy [here is a better 32bit wine howto.]("http://ubuntuforums.org/showthread.php?t=185557")

---

### Post by lcolson on 2007-08-03
Thanks for the help.  I used the method available here:

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

as recommended.

---

