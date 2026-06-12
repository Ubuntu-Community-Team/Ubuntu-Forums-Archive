---
title: "Quake4 Amd64 sturggle"
date: 2006-08-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by ravalox on 2006-08-11
Hey, I'm trying to install Quake4 'safely' on my dapper drake installation.  The install goes fine but when I try to run it I get the message:
```
./quake4.x86: error while loading shared libraries: libSDL-1.2.so.0:

```

This sounds like it should be simple to resolve, how can I workaround it?  It needs a 32 bit library, but I don't know where to safely put one in?

---

### Post by Kilz on 2006-08-11
[Download this package]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=amd64&file=pool%2Funiverse%2Fi%2Fia32-libs-sdl%2Fia32-libs-sdl_1.0ubuntu1_amd64.deb&md5sum=276fa2e4e35b992aec324aa51f696b46&arch=amd64&type=main") and double click on it, Gdebi will start to install it. It will provide the 32bit lib in the correct location. :D

---

### Post by ravalox on 2006-08-11
That doesn't work, thanks for the attempt though.

---

### Post by Kilz on 2006-08-11
> **ravalox said:**
> That doesn't work, thanks for the attempt though.

What is the error? Is it the same one?

---

### Post by jamesford on 2006-08-11
mmm, quake4 worked right away here, i suppose i do have some 32 bit libraries installed including  ia32-libs lib32asound2 lib32ncurses5 ia32-libs-sdl ia32-libs-gtk lib32stdc++6

no idea if that is of any help

---

### Post by ravalox on 2006-08-11
Thanks a lot, ia32-libs-sdl did its magic and made it work.

---

### Post by Kilz on 2006-08-11
Thats strange , because thats what I linked to in post #2.

---

