---
title: "Urgent, system complains about .Xauthority file, will not start xsession"
date: 2006-08-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by ravalox on 2006-08-08
Hi, I built an athlon64 system and installed mythtv on it, things were going fine until this morning I installed Quake4.  Now it tells me when I try to access anything administrative that the .Xauthority file can't be copied.  I tried a restart and now I can't start an X session at all.  Help, this is my media box and it's totally hosed over one file.  I may have to reformat, if so I don't think Ubuntu will be residing on that drive.

---

### Post by bscbrit on 2006-08-09
[http://www.die.net/doc/linux/man/man1/mkxauth.1.html](http://www.die.net/doc/linux/man/man1/mkxauth.1.html)

might help.

---

### Post by ravalox on 2006-08-09
It would be helpful if Ubuntu had it packaged in there in case it was needed, but as it's not I don't know where to get it.

---

### Post by bscbrit on 2006-08-10
> **ravalox said:**
> It would be helpful if Ubuntu had it packaged in there in case it was needed, but as it's not I don't know where to get it.

Sorry, I don't understand.  What is it that you are looking for that is not in the Ubunut repositories?

---

### Post by ravalox on 2006-08-10
I followed these directions:
[http://www.lucentplum.com/?p=16](http://www.lucentplum.com/?p=16)

It makes Quake4 work just fine, but it also hoses the .Xauthority file so that the next time you reboot you have no X-windows to come back to.  It centers around the ldconfig of the libSDL library, doing that for some reason breaks X-windows.  It's silly that that can have that effect, but never the less that is the problem

---

