---
title: "pause when starting up"
date: 2008-11-06
forum: x86 64-bit Users
---

### Post by LashSilence83 on 2008-11-06
Just out of curiosity, has anyone else running Intrepid 64-bit having a pause during startup after the wallpaper has loaded? Whether it's a reboot or cold boot on my system, I'm getting an extended (about 10-15 sec.) pause where the spinning icon freezes right after the wallpaper loads but before the gnome panel shows up. I never had this with any of the 32 bit versions so I'm a bit perplexed. It's not catastrophic or even critical by any means, but still annoying. Any ideas?

---

### Post by loephatt on 2008-11-06
Fascinating.

*I am seeing exactly the same thing.*

I recently built a clean copy of 8.10 x64 on a DELL Precision 490 (dual XEON and 4gb RAM). It was previously running 8.04 x32. It did not show this delay/lag.

Glad I am not losing my mind.

regards,

loephatt

---

### Post by LashSilence83 on 2008-11-10
have you tried anything to fix it? I have no idea where to start. I tried stripping off all the things that might slow the system down at startup but to no avail. Maybe it's a bug?

---

### Post by sco01 on 2008-11-11
Confirmed on a Dell T3400 (Intel Q9559, 4Gb RAM). Where do I start tracking this down?

//S

---

### Post by loephatt on 2008-11-11
Well, I am seeing it on a 32 bit version as well on a DELL latitude D630.

So I think we are seeing a systemic issue, perhaps the base code is not optimized as much as it could be? I don't think it can be viewed as a bug, more as bloat.

regards,

loephatt

---

### Post by fabertawe on 2008-11-11
> **LashSilence83 said:**
> Just out of curiosity, has anyone else running Intrepid 64-bit having a pause during startup after the wallpaper has loaded? Whether it's a reboot or cold boot on my system, I'm getting an extended (about 10-15 sec.) pause where the spinning icon freezes right after the wallpaper loads but before the gnome panel shows up.

Do you have an entry in ~/.xsession-errors containing this?
```
WARNING: Application 'gnome-wm.desktop' failed to register before timeout
```

If you do it seems like a common problem related to Compiz. I get around this by disabling 'Window Manager' (gnome-wm) in 'Sessions' and loading 'fusion-icon' instead and letting it launch Compiz. Admittedly, the desktop doesn't seem to load that much quicker on booting but on a logout/login it loads almost instantly, like with Metacity.

---

### Post by victorb on 2008-11-12
Just a thought.. I just installed 8.10 on a d630. And for the first couple of reboots I had the spinning thingy stop for 5 - 10 seconds just after the wallpaper loaded.

I also had my fan going crazy. Looking to fix the fan problem, I found this thread [http://ubuntuforums.org/showthread.php?p=6143525]("http://ubuntuforums.org/showthread.php?p=6143525") that explains how to perform a BIOS update from within Ubuntu (2nd entry). It solved my fan problem, and it also looks like it solved my pause at startup problem.

So if you guys do not have an up to date bios, maybe you should give this a try.

_Edit:_ Nevermind. The startup pause is back.. I also disabled a few services I do not use in the System menu.. No luck..

---

### Post by loephatt on 2008-11-12
Thanks, I caught that thread earlier as the fan did go berserk after the upgrade. I upgraded the BIOS on the laptop to fix that issue.

Unfortunately, the lag remains on my two units.

regards,

loephatt

---

