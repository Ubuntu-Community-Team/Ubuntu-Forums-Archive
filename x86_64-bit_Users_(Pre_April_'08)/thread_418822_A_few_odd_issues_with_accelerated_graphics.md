---
title: "A few odd issues with accelerated graphics"
date: 2007-04-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by cmost on 2007-04-22
Ok, I took the plunge!  Ordinarily, I wait at least a few weeks before diving into a new Ubuntu release but troubles with Feisty seemed far fewer than those encountered when Edgy was released so I thought "why not."  Another deviation for me was that I chose the upgrade option rather than a clean install.  I must say that I was very pleasantly surprised at how clean and simple the upgrade process was and how all of my programs and settings remained in tact.  Saved me hours of time.  I am having a few issues, however, but, they started before I upgraded to Feisty; with the last xserver updates for Edgy.  I think the problem simply carried over to Feisty.

Whenever I run a openGL screensaver, it will go for a while and then the computer will simply freeze.  It locks up entirely and I have to press the reset button on the tower to restart it.  If I choose a blank screen for a screensaver, my computer will run for days on end without issue.  This only began to occur within the past two weeks.  I tried recompiling my nvidia driver but that didn't solve the problem.  I can post my xorg.conf if anyone feels the problem may lie there.  I'm running Beryl with nvidia's ARGBvisuals (not AIGLX.)  I've been doing this for months without any issues and Beryl seems to be working fine as usual, it's just those pesky openGL screensavers (at least to my knowledge - I'm not a gamer so I can't say if the problem  would occur with other applications that rely on accelerated video.)

Another issue is that the upgrade seemed to kill gDesklets.  It crashes upon start.  Someone said to compile the latest version from the website, but I think i'll wait until it's updated in the repos.

Finally, Cairo-clock seems to crash periodically.  I don't know why yet.

If anyone can offer some insight, i'd be much appreciative.  Thanks!

Besides these very minor issues, Feisty seems noticeably faster than Edgy and starts up quicker too.  I'm loving it!!!  It seems like Ubuntu gets better and better with every release.  Keep up the great work guys!

---

### Post by Sadistic on 2007-04-23
> **cmost said:**
>  
Whenever I run a openGL screensaver, it will go for a while and then the computer will simply freeze.  It locks up entirely and I have to press the reset button on the tower to restart it.  If I choose a blank screen for a screensaver, my computer will run for days on end without issue.  This only began to occur within the past two weeks.  I tried recompiling my nvidia driver but that didn't solve the problem.  I can post my xorg.conf if anyone feels the problem may lie there.  I'm running Beryl with nvidia's ARGBvisuals (not AIGLX.)  I've been doing this for months without any issues and Beryl seems to be working fine as usual, it's just those pesky openGL screensavers (at least to my knowledge - I'm not a gamer so I can't say if the problem  would occur with other applications that rely on accelerated video.)

Hey mate , i had same problem with xubuntu 6.10 , well i coudn't find any solution about it . Seems  its rare issue and nobody know exactly the answer ...:(

---

### Post by ronocdh on 2007-04-23
> **Sadistic said:**
> Hey mate , i had same problem with xubuntu 6.10 , well i coudn't find any solution about it . Seems  its rare issue and nobody know exactly the answer ...:(
I saw this issue in Ubuntu 6.10, was not running Beryl. It was only those dang OpenGL screensavers that did it, made the computer impossible to access, had to do a hard shutdown. Never did see a fix. The hardware was old, an AMD Sempron with integrated graphics in the mobo. Lost to the sands of time now the issue is. =)

---

