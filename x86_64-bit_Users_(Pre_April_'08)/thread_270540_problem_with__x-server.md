---
title: "problem with  x-server"
date: 2006-10-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by jsvidyad on 2006-10-03
Hi!!


    I am able to log into one user account. But, then when I try to switch user and open a second x-window display, I am not able to. i have to log into the original account and I get a pop up message saying "The X server failed. perhaps it is not configured well". I tried restoring my original xorg.conf file, but the problem is still there. I am running ubuntu amd64-xeon on a core 2 duo (T7400) with Nvidia GeForce Go 7300 .

Any help would be greatly appreciated. ](*,)


And oh, this problem popped up suddenly. it was working fine yesterday. I did not do anything which should cause this.

---

### Post by kuja on 2006-10-03
Have you done any updates or installed anything lately? Those are usual culprits. 

Also, what user did you switch to? Try it with a blank user account, that sometimes works.

As per else, try running sudo dpkg-reconfigure xserver-xorg to rewrite the xorg.conf entirely (and then afterwards, re-running sudo nvidia-xconfig if you're using the proprietary nvidia drivers)

---

