---
title: "Game fullscreen in Wine under 12.10?"
date: 2013-01-03
forum: Wine
---

### Post by qrwe on 2013-01-03
Hi,
My problem is exactly the same as in [http://ubuntuforums.org/showthread.php?t=1814133]("http://ubuntuforums.org/showthread.php?t=1814133"), but as the Code of Conduct tells me to not post in old threads, here I go:

In Ubuntu 12.10, when trying to launch Starcraft (+ Brood Wars), the Launcher menu is visible, which covers the mini map and other things. This is really annoying, as the game seems to be fully playable overall. The Alt+Enter trick doesn't help here.
Has anyone seen this and maybe has a solution? Thanks.

---

### Post by Lyfang on 2013-01-03
Hi! Try Configure Wine > Graphics and uncheck "Allow window manager to control the windows". Original source: [https://bugs.launchpad.net/ubuntu/+source/wine1.4/+bug/966839](https://bugs.launchpad.net/ubuntu/+source/wine1.4/+bug/966839)

---

### Post by qrwe on 2013-01-03
> **Lyfang said:**
> Hi! Try Configure Wine > Graphics and uncheck "Allow window manager to control the windows". Original source: [https://bugs.launchpad.net/ubuntu/+source/wine1.4/+bug/966839](https://bugs.launchpad.net/ubuntu/+source/wine1.4/+bug/966839)

Excellent! That made the trick. =D> Huge thanks and cheers!

---

