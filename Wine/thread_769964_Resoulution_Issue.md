---
title: "Resoulution Issue"
date: 2008-04-27
forum: Wine
---

### Post by Etheredge on 2008-04-27
Small issue really...

When i was first configuring WINE i did not know exactly what to do as far as the screen resolution or DPI or things of that nature so i kinda guessed.

Well now all of the windows including the same config screen are blown up to high heaven leaving me no way to change things.

Lil help?

PS i have already tried uninstalling and reinstalling but the configs stay the same

---

### Post by schtufbox on 2008-04-27
I always find the default dpi setting to be fine :p
Have you installed any windows apps/games in wine yet? If not the simplest solution would be to delete the .wine directory in your home folder, then just run winecfg again to make new configs, this time leaving the dpi setting alone :)
If you HAVE instaleld stuff and don't want to reinstall, then hopefully someone knows which file in .wine has the dpi setting, because I don't :p

---

### Post by schtufbox on 2008-04-27
After a bit of searching, I MAY have come up with a fix.
Try the method I posted in reply to a similar post:

[http://ubuntuforums.org/showthread.php?t=771316](http://ubuntuforums.org/showthread.php?t=771316)

If it works great, if not. Then only thing I can think of is removing the .wine folder and running winecfg again as I suggested above.

---

