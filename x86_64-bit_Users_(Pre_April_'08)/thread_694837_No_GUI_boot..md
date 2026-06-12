---
title: "No GUI boot."
date: 2008-02-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by whitefang5412 on 2008-02-12
Well, this really isn't a giant problem, but when I turn on my machine. I get no ubuntu loading screen, and after about a 3 minute boot I get loaded into the desktop. It's not really a problem, but I'd like to have a fix for it, because I like seeing the boot up screen for some reason.:)

---

### Post by gsmanners on 2008-02-12
What type of video card are you using?

You may need to add a kernel option for whatever mode you want Linux to use by default (i.e. vga=0x315 or vga=0x318 for example).

---

### Post by Nikos.Alexandris on 2008-02-12
check the [http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Fix_Slow_boot.2Ffaulty_splash_screen](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Fix_Slow_boot.2Ffaulty_splash_screen) 
page!

---

### Post by hajk on 2008-02-12
Not using an 8xxx series GeForce nVidia card, like 8600GT, are you? If so, the boot and shutdown splash screens are not supported in Gutsy usplash.  May be it'll be fixed in Hardy...

---

### Post by whitefang5412 on 2008-02-13
I'm using an ATI graphics card. I experience this problem with even some i386 distro's. It's a heck of a lot more common on my desktop which runs linux mint and windows.

---

