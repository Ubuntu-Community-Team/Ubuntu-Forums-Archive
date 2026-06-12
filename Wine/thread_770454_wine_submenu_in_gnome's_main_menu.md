---
title: "wine submenu in gnome's main menu"
date: 2008-04-27
forum: Wine
---

### Post by mriedel on 2008-04-27
Trying to edit the wine menu through gnome's main menu config gui (system -> preferences -> main menu), I noticed that I couldn't change an existing entry's command. It let me enter a new command and stored it (next time I opened the main menu config I could see my changed entry) but when I run the entry from the main menu it just executes the menu item's default command. Also, the "revert to original" context option is grayed out for those manually edited wine menu items, but isn't for other entries I edited.

Other, non-wine menu entries can be edited properly.

Is there another way to manipulate the wine menu and/or is this a bug?

---

### Post by schtufbox on 2008-04-27
.wine/drive_c/windows/profiles/All Users/Start Menu/Programs

and

.wine/drive_c/windows/profiles/INSERTYOURUSERNAMEHERE/Start Menu/Programs

contain start menu items, obviously change INSERTYOURUSERNAMEHERE  to your actual username :p  Not sure if it'll help or not, haven't needed to clear anything from my wine menu yet :D

Hope it helps!

---

### Post by mriedel on 2008-04-27
The shortcuts in that folder do not equal the ones that appear in the gnome menu. Thanks anyway though.

---

### Post by happyhamster on 2008-04-27
Both the .config and .local folders in your home dir store wine-menu related stuff. (Press ctrl-h in nautilus to be able to see hidden files.)

For example:
.config/menus/applications-merged
.local/share/desktop-directories

And you'll probably have to restart gnome-panel or such to see any changes (press  ctrl-alt-backspace for example; this will close all programs though. Perhaps "killall gnome-panel" works also.)

---

### Post by mriedel on 2008-04-27
With happyhamster's info, I was able to identify the problem:

It's apparently a bug. The gnome menu editor writes the changed wine .desktop files to ~/.local/share/applications. The correct directory is ~/.local/share/applications/wine. So this probably has to be fixed.

---

