---
title: "Computer logged out automatically now screen is messed up..."
date: 2008-03-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by emiii0 on 2008-03-05
I've had Gutsy Gibbon installed on my computer for quite some time (A few months). Anyway, I was just doing some editing to my website and working with phpmyadmin. I left these things open and went to play some Rock Band for a little while. I came back 30 minutes later to continue and Ubuntu logged me out all of a sudden. Now, whenever I log back in, the desktop is bigger than my screen...meaning if I just move the mouse up or down I can scroll in that specific direction, which I have to because I can't see either my applications/places/system bar or the opened application bar. Anyone have any ideas?

*I was working with a 1600x1200 resolution. I can change it to another and the screen turns out ok. However, using a 1600x1200 setting, I can not view the whole desktop at once. I have to scroll.

---

### Post by Defrector on 2008-03-06
Sounds like one of the following may have happened, from most likely to least:

* Your /etc/X11/xorg.conf got corrupted and you may need to try your most recent backups of the file. I've seen this happen when updates get installed and mess with xorg.conf.
* Your video driver got corrupted up and may need to be reinstalled.
* Some hardware failure (unlikely but possible)

The logout anomaly is peculiar and probably is important. I don't know what would cause that though.

---

### Post by emiii0 on 2008-03-21
Anyone else have any idea about this? The screen is fine now, however my computer still logs me out. It happens about every other day, and I could be doing any task when it happens. The screen goes black for one second then the login screen appears.

---

