---
title: "FREEZES LIKE Windows"
date: 2007-12-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by Trymic on 2007-12-27
I am recently experiencing a windows version problem on my Ubuntu 7.10. Suddenly it freezes then the screen is switching off. My machine is still is on power but there is nothing i can to but to force shutdown using the power button. The reason i switched to ubuntu is to avoid the blue screen of death of windows but now i have a black one
Any help?

I have recently installed wallpaper draper and uninstall gnash. No update .
 I don't know what is the cause of the problem.

Any help.????
I have to solve it quickly or else i will switch back to XP :(  and wait for 8.04 hoping it would be better.

Thanks

---

### Post by hoarycripple on 2007-12-27
> **Trymic said:**
> I am recently experiencing a windows version problem on my Ubuntu 7.10. Suddenly it freezes then the screen is switching off. My machine is still is on power but there is nothing i can to but to force shutdown using the power button. The reason i switched to ubuntu is to avoid the blue screen of death of windows but now i have a black one
Any help?

I have recently installed wallpaper draper and uninstall gnash. No update .
 I don't know what is the cause of the problem.

Any help.????
I have to solve it quickly or else i will switch back to XP :(  and wait for 8.04 hoping it would be better.

Thanks

This thread might be what you are experiencing:

[http://ubuntuforums.org/showthread.php?t=587905](http://ubuntuforums.org/showthread.php?t=587905)

No real fixes yet much less a consensus on what is even causing the problem.  I experienced this problem too, and my solution so far has been in three steps:

1.  Install the 169.07 drivers from nvidia if that is your chipset
2.  add acpi=off to the default boot options for grub
3.  while in an X session, in a terminal, do:  "xset s off"

That stopped the lockups for me so far.  Let me know how it goes.

Hoarycripple

---

### Post by yyyc186 on 2007-12-27
> **hoarycripple said:**
> 
2.  add acpi=off to the default boot options for grub
Hoarycripple

Oddly enough, now when I add that in menu.lst, my system does not boot at all.  It will boot if I manually edit the startup parameters and take that off before it tries booting.

---

