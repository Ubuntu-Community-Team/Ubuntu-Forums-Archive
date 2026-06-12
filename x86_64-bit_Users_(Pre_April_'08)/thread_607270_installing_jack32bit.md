---
title: "installing jack32bit"
date: 2007-11-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by Stochastic on 2007-11-08
Hi, I'm wanting to get ChucK [http://chuck.cs.princeton.edu/](http://chuck.cs.princeton.edu/) up and running on my UbuntuStudio64 install.  I was told by the chuck devs that there are significant issues with getting it to work on a 64bit system and that the only way to do it right now is to install 32bit libraries and a 32bit version of Jack before then installing the 32bit ChucK.  I'm brand new to the 64bit world (I took the plunge thinking that it had gotten better over the last couple years) and have no idea how to "make" a 32bit program.  Please can someone help.  Thanks.

---

### Post by stmiller on 2007-11-08
Some bad news: unfortunately this might not be possible right now. The package maintainer who makes the ia32* packages of 32bit libraries told me in an email that he has a list of 32bit libraries on the wish list to add, including jack and ssh 32bit libraries. 

There might be a way to force a 32bit jack install, but I'm not sure if it would work with the 64bit audio system, etc. :(

---

### Post by Stochastic on 2007-11-09
Nnnnooooooooooo!!!!!   I guess it's back to 32bit I go, this app/language is one I use regularly.

---

### Post by Kilz on 2007-11-09
You might want to force install it [and use getlibs ]("http://ubuntuforums.org/showthread.php?t=474790&highlight=getlibs")to at least see if it will work.

---

### Post by Stochastic on 2007-11-09
I don't quite follow.  would I use getlibs for jack or for chuck's install?

---

