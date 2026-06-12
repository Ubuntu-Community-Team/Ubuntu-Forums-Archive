---
title: "Ubuntu 9.04 will not boot into the GUI after Nvidia Driver install"
date: 2009-06-27
forum: x86 64-bit Users
---

### Post by Hawkwind1349 on 2009-06-27
Ok so I am very new to unbuntu like 3 days new, I know maybe a handful of linux commands so I will provide the information I know if more is needed please let me know how to get it ;)

So I just installed ubuntu 9.04 (dual boot with Vista) and was able to get into it fine, did th standard updates and downloaded some basic programs, however when the hardware driver window came up and told me to activate the graphics driver after doing so it will not boot into the gui anymore. after installing and activating the driver it asks me to reboot after rebooting it hangs at the checking battery state or loading postfix configuration either one of those and even when I log into recovery mode it does nothing, I would like to have this as my new main OS however I do need a lot of help with getting it to work with my graphics driver.

Thank you in advance!

---

### Post by philcamlin on 2009-06-27
click ctrl alt f2 does that o anything? :popcorn:

---

### Post by Hawkwind1349 on 2009-06-27
I logged into the CLI and pressed them and not a thing happened

---

### Post by philcamlin on 2009-06-27
ok so your dropping to shell...

ill get back to you ina bit i have too figure out whats happening:popcorn:

---

### Post by Hawkwind1349 on 2009-06-27
Great thank you, if it helps at all the specs are intel quad 2.8 4 gigs ram and 2 nvidia 8800 gtx

---

### Post by dagrump on 2009-06-28
I'm guessing the 8800's are in SLI? 
If so it requires a little work to reap the benifits, look for "GUI doesn't load after installing nvidia drivers." It's about 3 pages deep, I explained the way to do it there.
Sorry I'm to lazy to type it again.
It's not a point & click solution, but that is the only why I've been told to do it.

---

### Post by slamhound on 2009-06-28
If it's not SLI and you are using two cards for more than two monitors (or perhaps even if you are using SLI) you might need to use the steps described in my reply to a previous post:

[http://ubuntuforums.org/showpost.php?p=7452633&postcount=2](http://ubuntuforums.org/showpost.php?p=7452633&postcount=2)

Basically, you need to use nvidia-xconfig with the -a flag to enable all gpus.  This should get two cards working; but I think if you want to use SLI, some additional steps might be necessary.

---

### Post by Hawkwind1349 on 2009-06-28
> **dagrump said:**
> I'm guessing the 8800's are in SLI? 
If so it requires a little work to reap the benifits, look for "GUI doesn't load after installing nvidia drivers." It's about 3 pages deep, I explained the way to do it there.
Sorry I'm to lazy to type it again.
It's not a point & click solution, but that is the only why I've been told to do it.


I found your page yesterday when I was skimming around the internet and it worked, I installed the newest drivers for the 64 bit version through nvidia and modified my /etc/X11/xorg.conf to the way you suggest and its running like a dream now! I have my dual boot set up in case I need my game fix and I am enjoying the hell out of linux teaching myself all the commands now :) great fix thank you very much!

(i even got a bit nerdy on it and did the 3d desktop cube, it rules!)

again thank you guys a ton for taking your time to help n00bs like myself =)

---

### Post by dagrump on 2009-06-28
Well, I'm glad you got it working. I think thats been needed to be tweaked since 8.10, SLI isn't that widespread it seems. Seems a lot of people won't spring for that second video card. Anyway enjoy your new install & if you break it you get to keep the pieces.

---

