---
title: "Firefox goes black &amp; white after changing video card/settings"
date: 2009-05-30
forum: x86 64-bit Users
---

### Post by esdaniel on 2009-05-30
Hi,

I've upgraded my Kubuntu JJ graphics card, from an 8800GT to a HD4870, so had to swap the drivers out and so on.  

For the most part it was painless, using restricted drivers, with the exception of *aticonfig --initial* command not automatically adding and enabling the AIGLX option for the desktop effects in Xorg.conf.

What I've not been able to 'get right' much to my chagrin is a quirk with firefox. It had been working fine but between trial and error tweaks while learning/experimenting with the xorg/ati driver Firefox has decided to go colorless, or so it seems - pic attached in case words have failed me.  Firefox was running in safe mode when I took the snap so I guess it's out of FireFox's control.  I've also purged nvidia and firefox and reinstalled firefox though thus far no joy. Also xorg.conf (xorg.txt) just in case I've done something fatally stupid there, though hope not.  

Bit of a weird one, been hunting and not found much on net for guidance :-( 

Any ideas, clues, tips on this one?

---

### Post by esdaniel on 2009-05-30
To be fair I did not reset anything when I'd run Firefox in safe mode, idea being to see if the problem persisted when all addons were disabled, anyhow...

Having bitten the bullet of resetting user preferences and toolbars permanently when launching in safe mode again it has resolved the black-white issue.

I hope that helps anyone else who ends up with same problem.

---

