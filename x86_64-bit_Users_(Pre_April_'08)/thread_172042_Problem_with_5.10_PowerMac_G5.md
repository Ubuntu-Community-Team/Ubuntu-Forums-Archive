---
title: "Problem with 5.10 PowerMac G5"
date: 2006-05-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by somebloke on 2006-05-07
I tried to use the live cd of ubuntu on my powermac, everything seemed to work ok, but on the splash screen the ubuntu logo is really low quality and looks like 256 colors. and then it just freezes on a brown screen.

Failing that I tried the live cd on my G4 PowerBook, which seemed to work perfectly fine, so I went and tried to do a full install on my PowerMac with the full installer, again everything went fine until I had to login the slash screen looked dodgy again and the computer freezes on the login screen, you cannot use the mouse or keyboard and the fans start and goto full power and that's how the machine stays.

The PowerMac is a G5 1.8 and has a nVidia Geforce 5200 64mb graphics card, it's pretty much standard.

Can anybody help me out?
Cheers

---

### Post by somebloke on 2006-05-07
After following the instructions on this thread

[http://ubuntuforums.org/showthread.php?t=118282](http://ubuntuforums.org/showthread.php?t=118282)

I could get the system to actually login and work, but only on live cd, and without sound, and with the fans going full speed constantly.

---

### Post by Torrance on 2006-05-08
The instructions for getting an installed version of 5.10 are here: [http://ubuntuforums.org/showthread.php?t=89712&page=3](http://ubuntuforums.org/showthread.php?t=89712&page=3) It's a known bug, and is related to the sound server, but I'm not sure if it will be fixed by the time Dapper Drake comes out.

I'm afraid that sound and fan control are a no-go with 5.10. Hopefully termal management will be in 6.06, but the Betas still don't have this (despite the fact that it's easy to add). Sound is not likely to be around for a while yet.

---

