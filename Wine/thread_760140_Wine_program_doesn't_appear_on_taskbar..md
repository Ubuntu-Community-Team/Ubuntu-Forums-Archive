---
title: "Wine program doesn't appear on taskbar."
date: 2008-04-19
forum: Wine
---

### Post by SuperBo on 2008-04-19
I use wine to run Rapget and USDownloader, it run but doesn't appear on taskbar. I press Alt+Tab, but there isn't wine window. Please help me fix this error.

---

### Post by UCAP on 2008-04-20
Are you running Hardy Heron? If so, it's a bug in wine 0.9.59 [http://forum.winehq.org/viewtopic.php?t=452&highlight=taskbar](http://forum.winehq.org/viewtopic.php?t=452&highlight=taskbar)

---

### Post by mjuhasz on 2008-04-20
I reported this bug to the launchpad as well: [https://bugs.launchpad.net/bugs/216235](https://bugs.launchpad.net/bugs/216235)
It is still not working with 0.9.60 so the only workaround I am aware of is the one I described in the launchpad (building a new package after changing some lines in the winex11.drv).

---

### Post by SuperBo on 2008-04-20
I'm using Gutsy, not Hardy.

---

### Post by mjuhasz on 2008-04-20
The problem is not distribution related as long as there are no distro-specific patches applied. The problem is in the wine code itself (winex11.drv, winpos.c). According to the wine changelog there were some attempts to fix this in 0.9.60 but it seems we have to wait for the next release.

---

### Post by motin on 2008-04-27
Upgrade to wine 0.9.60 to solve this issue. 

It's in launchpad too: [https://bugs.launchpad.net/ubuntu/+source/wine/+bug/216235](https://bugs.launchpad.net/ubuntu/+source/wine/+bug/216235)

---

### Post by phreakaholic on 2008-04-28
still learning how to get my wine works well :)

---

### Post by SuperBo on 2008-04-28
I use Wine 0.9.60 under Hardy, but that error is still.

---

### Post by JGSD on 2008-05-31
I have just installed the newly-released Wine 1.0-rc3 package and this problem seems to be fixed. The program that I was having problems with (Nusphere phpEd) is now displaying properly in the panel / taskbar.

To get this Release Candidate version of Wine, you'll need to add the Wine repo to your system. Go to [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb) for instructions on how to do this on Hardy.

---

