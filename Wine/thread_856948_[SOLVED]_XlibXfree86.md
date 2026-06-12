---
title: "[SOLVED] Xlib/Xfree86"
date: 2008-07-12
forum: Wine
---

### Post by mike g on 2008-07-12
I just attempted to install Wine 1.0 and at the end of the ./configure I received a message indicating I am missing Xlib/Xfree86 and suggested that I really did not want to run Wine 1.0 without it.

I attempted to load the missing Xlib and Xfree86 to no avail.

How do I obtain the missing files?  How do I install them once I get them?

---

### Post by happyhamster on 2008-07-12
- Wine 1.0 can be obtained here:
[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

- Or go here to get the latest wine (hardy heron):
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

- But if you really need to compile yourself: try running

sudo apt-get build-dep wine 

- before you run ./configure. See also:
[http://wiki.winehq.org/Recommended_Packages](http://wiki.winehq.org/Recommended_Packages)
[http://wiki.winehq.org/WineOn64bit](http://wiki.winehq.org/WineOn64bit)

Good luck.

---

### Post by mike g on 2008-07-13
Thank You....That seemed to work but when I attempted to load a program I got an error message which I am positive relates to windows....the message said, I attempted to load the C runtime Library incorrectly and to contact support.  Did something not load correctly when I complied and installed Wine?

The program was Quicken 2007 basic which is basically the same as 2006 basic which is supposed to work.

---

### Post by mike g on 2008-07-19
I am closing this as it appears as if this problem has already been reported as a bug.

Thanks you for you assistance.

---

