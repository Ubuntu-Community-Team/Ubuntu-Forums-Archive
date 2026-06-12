---
title: "Strange application font in Wine"
date: 2013-02-02
forum: Wine
---

### Post by Ranko Kohime on 2013-02-02
I'm having an issue with the fonts used for dialog boxes, menus, etc. in Wine.  See attached screenshot for example.

I've installed all of the fonts available using Winetricks, but that had no effect.

Is there a way to force which font is used?

---

### Post by dino99 on 2013-02-05
usually with wine1.5 you should not need additional fonts.
 If you only have font issues with wine, then create a new .wine (rename the actual one, then run winecfg again).
But if you get font problems outside wine too, then check your locale(s) into System Settings.

are you using wine 1.5.23 ?  (as you should)

---

### Post by Ranko Kohime on 2013-02-22
Ahh, I hadn't been.  I was using the 1.4.1 in the 12.10 repos.  Upgrading to the 1.5.23 release fixed it.  Thanks.  :D

---

