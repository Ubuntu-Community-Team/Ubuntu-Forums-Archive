---
title: "Tsclient seg fault."
date: 2005-10-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by darkone338 on 2005-10-14
HI,

Anyone else having problems with tsclient ?

It runs up, I enter the server details, and then click connect and it crashes with a Segmentation Fault and no other information.
Running vncviewer and rdesktop (which tsclient calls), manually, works fine.

I tried removing the package, I've even compiled from source and get  the same problem.
Any help would be greatly appreciated.

Regards

Stu

---

### Post by David Marrs on 2005-10-14
It sounds like a bug in the program. I'd go to the website and find out the easiest way to file a bug report.

---

### Post by darkone338 on 2005-10-14
quick update, 

the tsclient version 1.40 that ships in 5.10 seems to segfault.

So you can go to :-
[http://archive.ubuntu.com/ubuntu/pool/main/t/tsclient/](http://archive.ubuntu.com/ubuntu/pool/main/t/tsclient/)

and install the 1.320 client and it seems to work fine. (I compiled it from the source rather than installing the package, so i would never accidentally update it with synaptic or apt.. ;)   )

ATB

Stu

---

### Post by ssam on 2005-10-14
head over to [https://launchpad.net/](https://launchpad.net/) and file a bug.

---

