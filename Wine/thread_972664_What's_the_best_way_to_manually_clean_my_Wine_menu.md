---
title: "What's the best way to manually clean my Wine menu?"
date: 2008-11-06
forum: Wine
---

### Post by diablo75 on 2008-11-06
On occasion, I've managed to install software that ended up not running on Wine, and for some reason, failed to uninstall.  So I would end up manually deleting the program files and folders from the hidden Wine folder.  But I'd also like to delete the useless short cuts.  Should I just use my menu editor to disable the links so they don't show, or is there a way I can delete them?  Using the Main Menu tool in my system menu helps, but it wasn't able to delete everything...

---

### Post by 16777216 on 2008-11-06
I have some clutter in the wine sub-menu that I have hidden but would like to remove and the menu editor does not allow me to.

I can't remember where the folder with the menu items is and I can't find it for the life of me. :lolflag:

---

### Post by sdowney717 on 2008-11-06
the menu item s are in
 /home/username/.local/share/application/wine/programs

use nautilus, view hidden files (.local is hidden)

---

### Post by david_kt on 2008-11-06
> **sdowney717 said:**
> the menu item s are in
 /home/username/.local/share/application/wine/programs

use nautilus, view hidden files (.local is hidden)

In addition to above, also delete files you do not need in:

/home/username/.config/menus/applications-merged/

DK

---

### Post by bobbob1016 on 2008-11-06
Alacarte is good too.  It is a gui way to edit all menus.  Just do Alt+F2 then alacarte or enter alacarte in a terminal.  I don't think it needs sudo, didn't when I ran it just now.

---

### Post by david_kt on 2008-11-06
> **bobbob1016 said:**
> Alacarte is good too.  It is a gui way to edit all menus.  Just do Alt+F2 then alacarte or enter alacarte in a terminal.  I don't think it needs sudo, didn't when I ran it just now.

I have tried Alacarte, it did not really delete the entry, just exclude it, even when I tried to delete it not just remove the tick. Further more, it could cause problem when you reinstalling wine, menu will not appear until you manually edit the menu and remove the "exclude" line.

DK

---

### Post by YokoZar on 2008-11-06
Use Wine's uninstaller to remove programs rather than deleting them.

The shortcuts, as you've noticed, still won't be deleted however.  This is a simple bug in Wine with an oddly difficult solution.  Unfortunately, manual editing of files is pretty much the only sure way at this point.

---

