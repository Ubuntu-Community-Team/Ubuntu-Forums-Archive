---
title: "no aic7xxx support for second stage boot in 5.10?"
date: 2006-04-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by jeglin on 2006-04-24
I have 5.10, installing on an PowerTowerPro (OldWorld of course) with a PL 800/G4 upgrade. YellowDog 3 with kernel 2.4 works/installs fine. My target drives (one is YDL, second is for Ubuntu) are on an Adaptec 2940 card. I can complete the first stage install of 5.10 with no problems; apparently the first stage has aic7xxx support built-in; however, when rebooting to go to the second stage, I get a panic (no mountable file systems).

I've been through this lots of times before - it's because the vmlinux that is supplied with the 5.10 CD (same kernel as that installed in /boot during the first stage) apparently has no aic7xxx support built in. It can't see the drives on the adaptec card.

So, I either need a pre-built kernel, compatible with 5.10, with aix7xxx support built in, or I need some other clever hack. If I absolutely have to, I can put the drive back on mesh I guess, but I'd like to avoid that if possible.

I did try one hack... I booted into the Ubuntu second stage using a gentoo kernel I had left over from an earlier experiment. Tons of module errors of course, but I actually got into the second stage of the Ubuntu install. But somewhere around the 80% mark, the screen went black while doing something, and never came back; I let it run overnight like that, but it was gone. I was surprised my gentoo kernel got me that far...

Surely I'm not the only one that has run across this? I have seen the question posed elsewhere here (x86 forum?) but there were few answers, and none viable.

I'm still learning the Ubuntu style of doing things - there appears to be no part of ubuntu.com where I might download alternative kernels...

---

