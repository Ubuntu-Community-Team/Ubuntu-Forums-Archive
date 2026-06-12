---
title: "How do i compeltely remove something i installed through Wine?"
date: 2008-05-28
forum: Wine
---

### Post by Kidfork on 2008-05-28
I need to remove things i installed through wine. I uninstall them, but it still doesn't leave th Applications>Wine>Programs Bar? How can i remove them?

---

### Post by happyhamster on 2008-05-28
Right-click the main menu and choose Edit Menus to get rid of the menu entries.

Other things you can do: take a look in the hidden .wine folder in your home dir. Perhaps there are still old savegames, config files and such. (When using nautilus, press ctrl-h to be able to see hidden files.)
And in case you like to do things manually: there are also some wine-menu related things in the .local and .config folders in your home dir.

---

### Post by cogadh on 2008-05-28
I don't think the right-click method works in Gnome, you have to go to System > Preferences > Main Menu and manually delete the entries. Or you can just type "alacarte" in a terminal.

---

