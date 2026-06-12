---
title: "fglrx fails to upgrade..."
date: 2007-06-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by tblancher on 2007-06-29
I received notification that there were some updates available for my system (via the update manager applet), and I tried to apply them.  Everything except the fglrx update applied correctly.  The update gives me the following error, which I suspect is due to a bug, but I wanted to run it through these forums first before I went to Launchpad:

E: /var/cache/apt/archives/xorg-driver-fglrx_7.1.0-8.34.8+2.6.20.5-16.29_amd64.deb: trying to overwrite `/usr/share/man/man8', which is also in package lsof

Not a show stopper or anything, I'd just rather it update cleanly...

---

### Post by tblancher on 2007-07-05
I figured it out.  Turns out a third-party software install overwrote the man8 directory, making it a single man file.  I also had uninstalled lsof to see if that was blocking it.

Everything seems to be working now.

---

