---
title: "post-upgrade browser/video freeze"
date: 2009-03-02
forum: x86 64-bit Users
---

### Post by infallible on 2009-03-02
After the online upgrade from 8.04 to 8.10, i'm experiencing extended grey-out of firefox and epiphany. it occurs consistently when opening new tabs and most of the time when opening new pages. I'm not jumping to blame the ugrade however, as there are may be other circumsances in play. I had attempted to install a PCI Dlink 530TX+ NIC to allow two IP's on the network; doing so seemed to break NetworkManager, and I thought the upgrade would solve it. I seem to remember it working in the short time I used it after the upgrade, probably working... Then I installed an old Matrox Mystique PCI GPU working towards dual display. As it was an old card, and I'm looking to save memory, I uninstalled compiz via synaptic. I took the card out when I suspected it was causing problems, because i was also experiencing window artifacts and residual menus in addition to the browser hang. Everything seemed to un-freeze after thirty seconds or so. I'm not afraid to break into CLI and make this all work, but it almost seems like a fresh install would save me a lot of effort. I'm hoping someone can tell me if there is aeasy fix here, and although I listed these changes, I'm not concrete on the contributing factors.

---

### Post by brerbridge on 2009-03-02
I am having the same issues. I did compiz --replace, not better. I tried turning compiz off, no help either. I can reciprocate this problem everytime, say, if I attempt to play an embedded youtube video on a blog or something. Either grays out for way too long, or the youtube video will just stop and disappear in the middle of playing.

Help would be great from anyone.

---

### Post by istblacken on 2009-03-03
videos being greyed-out is a known bug with npluginwrapper and 32 bit version of flash. there is an alpha version of the 64 bit flash player which works a lot better than the pluginwrapper+32 bit flash player. you can follow the guide here [http://ubuntuforums.org/showthread.php?t=1081964](http://ubuntuforums.org/showthread.php?t=1081964)
and about Network Manager, i don't like it and i use wicd. maybe you want to try that one too to see if that helps.

---

### Post by infallible on 2009-03-03
That doesn't sound right. I had my problems setting up flash, but the browser freeze happens without any flash applets. I'm starting to think the problems are connected, because when gmail freeezes, it comes back saying something about it's features being limited due to connectivity issues.

---

### Post by infallible on 2009-03-07
fresh install fixed it.

---

