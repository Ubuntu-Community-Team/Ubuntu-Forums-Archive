---
title: "How do I prevent apper/packagekit from installing Microsoft Fonts"
date: 2013-03-03
forum: Wine
---

### Post by HighPerformer on 2013-03-03
Hi

I don't want these ugly fonts on my system. How can I disable them from being installed?

Apper/Packagekit just seems to ignore this setting:

testi@testi-desktop:~$ cat /etc/apt/apt.conf.d/10recommends 
APT "";
APT::Install-Recommends "false";
APT::Install-Suggests "false";

Any ideas?

I'm annoyed of uninstalling and escaping to the console when wine updates. Really - what's even the point of having these fonts installed anyway. There is really just about 0.01% of applications which have problems without these fonts. It's pointless and obviously it's easier to install them afterwards then having to remove them in weird ways. They should just stop annoying me.

Ah forget it - I just forgot to do a "sudo apt-get update" after the configuration change

---

