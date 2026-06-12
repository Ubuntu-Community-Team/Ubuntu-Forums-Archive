---
title: "Flash Acting Ridiculous"
date: 2007-12-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by fragility14 on 2007-12-17
I'm on 64 bit Gutsy Kubuntu, and have had flash working on both Konqueror [preferred browser] and firefox for months. Today it started acting funny for no apparent reason.

The current situation is as such: konqueror will have sound on youtube but no video, and the video area (or any other flash area on a page with a flash widget) will be a frozen up part of the screen. On firefox it will either work all the way, or the whole browser will freeze. Firefox has been acting strange for a while but since I only use it if a page wont work on konqueror it hasnt been a problem. I have tried uninstalling and reinstalling the nspluginwrapper and the adobe flash non-free plugins, and I end up back at ground zero of flash audio working on konqueror, and flash working inconsistently on firefox. (Note: on firefox once it crashes it seems I need to uninstall and reinstall flash to get it to work again).


It's all very strange...thanks for any help!

---

### Post by samjh on 2007-12-17
I've just reinstalled Kubuntu 7.10 on my computer and am experiencing the same problem.

Tried the usual flashplugin-nonfree installation, as well as manual installation using nspluginwrapper, but to no avail.

Some help would definitely be nice. :)

---

### Post by John.Michael.Kane on 2007-12-17
These may help in answering why you  are having issues.

[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/173890](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/173890)

[https://lists.ubuntu.com/archives/ubuntu-devel/2007-December/024877.html](https://lists.ubuntu.com/archives/ubuntu-devel/2007-December/024877.html)

Until they have decided how to proceed you may want to use one of these methods
[http://ubuntuforums.org/showthread.php?t=202537&highlight=java](http://ubuntuforums.org/showthread.php?t=202537&highlight=java)
[http://ubuntuforums.org/showpost.php?p=3941685&postcount=11](http://ubuntuforums.org/showpost.php?p=3941685&postcount=11)

---

### Post by tgalati4 on 2007-12-17
When firefox crashes:

>sudo killall firefox-bin

Normally this will remove the memory-resident bits of firefox when it acts up.  You shouldn't need to reinstall.

Run memtest overnight.  Make sure you don't have a RAM problem.

---

### Post by fragility14 on 2007-12-17
I completely broke it, and then using something recommended on the bug report, got back to being able to hear audio on konqueror, and everything working on firefox until it breaks again, which it will, at which point I appear to need to reinstall and killing firefox doesn't help.

---

### Post by samjh on 2007-12-18
I believe the issue we're facing is the XEmbed dependency problem for Konqueror.  The latest Adobe Flash release depends on XEmbed, which Konqueror doesn not support: [http://bugs.kde.org/show_bug.cgi?id=132138](http://bugs.kde.org/show_bug.cgi?id=132138)

[EDIT]

OK, I've got Flash to work on 64-bit Konqueror by manually installing r48 of the Flash plugin.

Oh, by the way, older versions of Flash can be downloaded here (61.8MB zip archive): [http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp9_archive.zip](http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp9_archive.zip)

---

