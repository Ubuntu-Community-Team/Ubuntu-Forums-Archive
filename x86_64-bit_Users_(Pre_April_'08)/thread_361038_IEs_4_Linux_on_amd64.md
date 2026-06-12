---
title: "IEs 4 Linux on amd64"
date: 2007-02-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by Pejalo on 2007-02-13
Has anyone here installed wine and ies4linux on amd64? Is it safe to just install 64bit wine and use force-architecture for the i386 version of ies4linux? I can't find any instructions and am not knowledgeable enough to compile my own from source.
Thanks

---

### Post by Kilz on 2007-02-14
> **Pejalo said:**
> Has anyone here installed wine and ies4linux on amd64? Is it safe to just install 64bit wine and use force-architecture for the i386 version of ies4linux? I can't find any instructions and am not knowledgeable enough to compile my own from source.
Thanks

I do know that ies4linux works if you use the 32bit wine. Secondly wine is a 32bit application layer, even the versions compiled to install on amd64, so it should work. Why not try it and post back here either way.

---

### Post by cmost on 2007-02-14
I can verify that It's working fine on Edgy x86-64.  I'm using a version of Wine available from the   amd64 repos.  I also have Codeweavers Crossover Linux installed on my workstation but I haven't used it to install any Windows applications yet (Haven't had a need - yay!!!)  See screenshot attached.

---

### Post by lgrce on 2007-02-14
I have it working fine as well on my Edgy x64 machine. The only issue I have had is some problems with fonts, but that had nothing to do with getting IE4Linux running.

---

### Post by Pejalo on 2007-02-15
It works!
I used your WineForAMD64 wiki article for wine, Kilz, then the standard ies4linux instructions.
Thanks to all for replying!

---

### Post by prince_niceguy on 2007-02-15
I installed wine from this thread

[http://ubuntuforums.org/showthread.php?t=297280](http://ubuntuforums.org/showthread.php?t=297280)

and then installed ie4linux and it works without any issues.

---

