---
title: "New user with some problems"
date: 2008-10-15
forum: x86 64-bit Users
---

### Post by kromerr on 2008-10-15
Hey i've had ubuntu for about a week now and am having a little trouble adjusting and some problems i can't seem to figure out,  if anyone could help me i would really appreciate it. 
            a couple of the problems I'm having are: 
              
               **-** I've been trying to install flash player 9 with no success, even though I've looked here and everywhere on how to do it and it says its "not compatible with x86-64" when ever i try
               **-** Also just today an error came up about the Package Manager saying this when i tried to open it:  

E: Type '&#8220;deb' is not known on line 58 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

Again, any help would be greatly appreciated. Also, other than these couple of problems, Linux seems much better than windows with all the things that you can do.

---

### Post by Yellow Pasque on 2008-10-15
There is a typo in your sources.list.
```
gksudo gedit /etc/apt/sources.list
```
Scroll down to line 58 and fix the first word so that it just says deb.

See the sticky in this sub-forum for directions to install Flash.

---

