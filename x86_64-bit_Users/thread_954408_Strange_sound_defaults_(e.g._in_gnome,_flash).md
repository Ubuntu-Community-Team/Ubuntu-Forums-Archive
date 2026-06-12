---
title: "Strange sound defaults (e.g. in gnome, flash)"
date: 2008-10-21
forum: x86 64-bit Users
---

### Post by xasx on 2008-10-21
Hi,

I ran into strange problems with my Ubuntu sound configuration.

I use Ubuntu 8.04.1 x64.
(If you need any further information, please ask for it)

First of all, I got my X-Fi to work with the help of Amtam's How-to which can be found here [http://ubuntuforums.org/showpost.php?p=4823915&postcount=675](http://ubuntuforums.org/showpost.php?p=4823915&postcount=675). Thanks for that.

Afterwards (i.e. kernel compiling, installing nvidia-driver and the x-fi driver, several reboots) I had to switch my audio cards' order to use the X-Fi as default since I also want to use hda_intel for VoIP issues as secondary sound card. To do so I just added the following lines to alsa-base:
```
options ctalsa index=0
options snd_hda_intel index=1
```

So far, I can hear the pre-login sound, but the sound that is configured to play after login is played through intel_hda. So I thought this could be a user-settings related issue. I ran asoundconf to configure the default sound setting:
```
asoundconf set-default-card 0
```

I don't know whether this is correct; asoundconf list output is:
```
Names of available sound cards:
0 [X-Fi           ]: X-Fi - Creative X-Fi [8c00]
Intel
```

Another strange thing is that the System->Settings->Audio applet plays the test tone through hda_intel if I select auto-detect and through X-Fi if I select ALSA.

Flash is also played via hda_intel.

Is there anything I can do? Anything I left out or forgot? Perhaps a special setting elsewhere...
Perhaps it is also related to having a user-compiled kernel (have I killed support for something)?

Any help is much appreciated.

Thanks in advance. Regards, xasx.

Edit:
1) Totem as well as Nautilus thumbnails (instant preview of music files) use the intended card (i.e. X-Fi)
2) Blacklisting the module results in the after-logon-sound not being played at all.
3) Creating a new user account did not solve the problem, so I suspect it to be a global settings issue.

---

