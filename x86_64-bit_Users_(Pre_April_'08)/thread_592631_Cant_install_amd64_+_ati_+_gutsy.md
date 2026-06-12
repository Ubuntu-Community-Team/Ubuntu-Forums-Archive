---
title: "Cant install amd64 + ati + gutsy"
date: 2007-10-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by grazzt on 2007-10-26
Cant get the install to work with an amd64 and an ati video card.

If I choose just the normal install, I get black screen, and it hangs

If I add "nosplash", I can get a little further, but ubuntu cant detect my video card so its in "low resolution mode", even if I hit continue there or manually force the "radeon" driver, all it does is go back to the console and "Running local boot scripts (/etc/rc.local)" and never progresses any further.

Even tried the noacpi, nolacpi options, no good either.

Have tried 3 cds, last 2 burning at 4x, and they all do the same thing.

I have read that maybe I should install Feisty and do the upgrade, is that really necessary?

---

### Post by RemmyLee on 2007-10-26
I too was unable to install via the normal CD and the problem was the splash screen.

 I used the alternate CD to install and then edited the grub menu to remove the splash option (/boot/grub/menu.lst) once installation was complete.

You will need to edit the grub menu at runtime as well by selecting your method of boot, E, and then remove "-splash" from the entry.

Once inside, sudo gedit /boot/grub/menu.lst

Remove "-splash" and you should be fine.

It's not a pretty solution, but it works.

---

