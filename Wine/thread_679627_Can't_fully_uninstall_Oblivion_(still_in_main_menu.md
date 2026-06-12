---
title: "Can't fully uninstall Oblivion (still in main menu)"
date: 2008-01-27
forum: Wine
---

### Post by kipling100 on 2008-01-27
Hi,

I was trying to uinstall oblivion, but I kept getting a 'no access' error through the uninstaller.  So I removed wine via the synaptics package manager, and deleted the .wine folder in my home directory.

However, I still have oblivion listed in my Other Programs in my Start Menu.  I try to edit the menu by going to Preference > Main Menu, but it doesn't load.

I'm using Ubuntu 7.10...

Any help will be greatly appreciated

Thanks,

Dennis

---

### Post by Mze on 2008-01-27
Keep your mouse on "Applications". Right-click and choose option "Edit Menus". I'm sure the rest is easy.

---

### Post by kipling100 on 2008-01-27
Thanks for you response...

When I do that, I get the same result...it just says Starting Main Menu for a few seconds, and then disappears.

I tried making sure all the directories in my home were set to my user group, and reinstalled alacarte (and other suggestions on these boards), but I'm having no success...any ideas?

Thanks!

---

### Post by kipling100 on 2008-01-28
fix:

So I realized there were some folders in my home directory that were still set to root after my wine uninstall.  So I went ahead and changed them all back, in particular:

.local/share/desktop-directories/

and

.config/menus/applications.menu

And then I deleted the Oblivion links from the .local/share directory.

---

