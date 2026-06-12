---
title: "How Uninstalling Wine and everything that goes with it."
date: 2008-12-01
forum: Wine
---

### Post by Arukas on 2008-12-01
I want to uninstall wine and everything that came with it.  A program I installed got installed wrong and will not uninstall.  So I want to delete everything and reinstall it.

I add/remove to undo wine, but when I reinstalled it, the incorrectly installed software was still installed.

---

### Post by poisonkiller on 2008-12-01
Here's what I do, when I want to get rid of Wine:
1. Uninstall Wine
2. Go to my home folder, press Ctrl+H and delete .wine folder.
3. I go back to my home folder, navigate to .local->share->applications and delete wine folder.
4. I go back to share and navigate to desktop-directories and delete everything inside there.

There is probably a script to do all this, but I'm too lazy to search for it. :lolflag:

---

### Post by dslax27 on 2008-12-08
Awesome, thanks!

---

### Post by Arukas on 2008-12-08
I've done this, but when I reinstall Wine now, it doesn't put the icons back in the menu.  Is there a way to get it to do this?

---

### Post by hikaricore on 2008-12-08
The menu issue is a known bug, don't rely on the functionality until it is stable.

Just add your own icons to your menu for software you install under wine, it's not that difficult.

---

### Post by Arukas on 2008-12-08
Didn't realize it was a bug.  It may not be that hard, I"m not use to resetting everything up in ubuntu.

---

