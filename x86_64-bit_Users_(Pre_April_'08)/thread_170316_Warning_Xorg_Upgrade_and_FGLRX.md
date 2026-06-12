---
title: "Warning: Xorg Upgrade and FGLRX"
date: 2006-05-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by Hygelac on 2006-05-04
There is an upgrade for xorg and the xserver in the repositories.  When I installed it, it ruined my FGLRX (performance was dismal and 'fglrxinfo' would tell me that it was running the inferior Mesa version from the repositories, not the version from the ATI site).  This problem seems to have been remedied by replacing 'libdri.a' (I was using the pre-Breezy version as the Ubuntu FGLRX Tutorial recommends ([http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide)](http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide)), which dpkg seems to have replaced; I just restored the old pre-Breezy version again).  So, I guess this is just a warning to those who are going to upgrade to backup their libdri.a before they do so. [-X  :rolleyes:

- I already posted this in the Kubuntu AMD64 section, but since I know there are more people here and that many of them probably do not visit the Kubuntu section (That is just an assumption of mine; am I correct?), I posted it here.  I assume that it is just as relevent to GNOME as to KDE.

---

### Post by matthew on 2006-05-04
I gave this same response in your other thread, but am adding it here for the same reasons that you posted here as well. The more data available about people's experiences, the better.

Hmm...

Granted, I am not running Kubuntu, but rather Ubuntu. I am also using the 32 bit version.

I did the upgrade and rebooted. This is the output from fglrxinfo on my computer.
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9700 Generic
OpenGL version string: 1.3.5272 (X4.3.0-8.16.20)

```In other words, the update worked fine for me.

---

### Post by Hygelac on 2006-05-04
I had some browser problems and accidentally posted this thread thrice here; sorry.  Matthew, I responded to your post in the Kubuntu section.

---

