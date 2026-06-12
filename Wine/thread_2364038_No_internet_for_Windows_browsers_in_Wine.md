---
title: "No internet for Windows browsers in Wine"
date: 2017-06-17
forum: Wine
---

### Post by crosslink on 2017-06-17
Browsers running in wine don't connect to the internet. Applications install and run fine, except for connecting to internet. (Firefox installs. Chrome starts install, then fails when it reaches the connect to internet part.) I've tried 32 and 64 bit Windows versions of Chrome and Firefox (all permutations, plus an esr version of Firefox). None connect.

Details for my system:

Ubuntu 16.04 (64 bit)
wine 1:1.6.2-0ubuntu14
libnss-mdns:i386   0.10-7
libnss-mdns 0.10-7


Two things I've tried, per section 10.6 (networking) of the wine docs. ([https://wiki.winehq.org/FAQ](https://wiki.winehq.org/FAQ))
- installing 32 and 64 bit flavors of libdnss
- setting up /ect/hosts as described in 10.6.

The searching I've done generally indicates that having the right libraries fixes most issues, but this isn't working here.

I'd appreciate tips on how to fix it.


A bit more perspective: I'm trying this to watch hbonow on my Ubuntu machine. I've tried Pipelight, and it hasn't worked at all for me. My reading indicates it's no longer supported, and the reco was Wine.

---

### Post by monkeybrain20122 on 2017-06-19
[https://bbs.archlinux.org/viewtopic.php?id=223335](https://bbs.archlinux.org/viewtopic.php?id=223335)

---

### Post by crosslink on 2017-06-24
Thank you monkeybrain. The following part from the link got Mozilla connected.

*The fix involves browsing to about:config and setting browser.tabs.remote.autostart2 to false.*

---

### Post by monkeybrain20122 on 2017-06-24
You are welcome. By the way, there is another, elegant solution to watch DRM flash streams without wine. [https://ubuntuforums.org/showthread.php?t=2363550](https://ubuntuforums.org/showthread.php?t=2363550)

---

