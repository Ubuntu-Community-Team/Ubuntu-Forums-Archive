---
title: "[SOLVED] Authorize Reboot For Automation"
date: 2008-12-06
forum: x86 64-bit Users
---

### Post by Rodney9 on 2008-12-06
I am trying to get my computer to start automatically when I need it. I am the only user. So far I have found code to wake the pc ([http://ubuntuforums.org/showthread.p...rtcwake&page=2](http://ubuntuforums.org/showthread.p...rtcwake&page=2)), Thank You Frigaut and Altay_H

code
> 
sudo rtcwake -u -s 1800 -m on

Seeing the suspend/hibernate will not wake up my usb keyboard, I was going to put 'reboot' into Alarm Clock a few minutes after the pc wakes and then after the reboot everything would be working.

My problem is that 'reboot' says "need to be root" even though I have granted my self in Authorizations.

So I need to know how to authorize myself for 'reboot' and 'rtcwake'

Rodney.

---

### Post by Rodney9 on 2008-12-06
I solved this with help from Slim Odds - [http://ubuntuforums.org/showthread.php?t=1004102](http://ubuntuforums.org/showthread.php?t=1004102)

and another forum - [http://forums.whirlpool.net.au/](http://forums.whirlpool.net.au/)  linux/bsd

Between the two I learnt how to change the permission for rtcwake and plugging my keyboard into a hub, lets it still work after suspend.

Thank You 
Rodney

---

