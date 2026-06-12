---
title: "[SOLVED] ia32 gtk1.2 &amp;amp; other libs"
date: 2007-10-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by sdhays on 2007-10-25
I have a brand new install of Gutsy Gibbon for x86_64 on my Athlon64 box (new to Ubuntu; just switched from Gentoo) and I've discovered that the ia32 libs don't include gtk1.2 support anymore.  Why is that and what's the best way to add 32-bit libraries like that?  I also need a couple other i386 libs like libxml.  Would forcing apt to install i386 libs be a good idea?  Do I have to roll my own solution?

I'm trying to install Canon's driver for Linux for my MP160 printer.  The utilities are only available for i386, but I've read online that they will work on x86_64 with 32-bit support.  

[http://openprinting.org/show_printer.cgi?recnum=Canon-Pixma_MP160](http://openprinting.org/show_printer.cgi?recnum=Canon-Pixma_MP160)

Any suggests are well appreciated!

Scott

---

### Post by jdfreshwater on 2007-10-25
one way to do it may be to use alien on a 32 bit system to create a deb package and install it using dpkg -i --force architecture <package> command.

---

### Post by Cappy on 2007-10-25
See getlibs here:
[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

Let me know if you need any help if something doesn't go smoothly.

[http://packages.ubuntu.com/](http://packages.ubuntu.com/) may be useful if you need a library that you don't know the exact name of

---

### Post by sdhays on 2007-10-25
Thanks!  getlibs solved all of my library dependencies.  Now if only I could figure out why CUPS isn't detecting the pstocanonij filter....  But that's a different problem.

---

