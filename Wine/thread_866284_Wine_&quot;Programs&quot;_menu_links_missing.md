---
title: "Wine &quot;Programs&quot; menu links missing"
date: 2008-07-21
forum: Wine
---

### Post by Akingboy on 2008-07-21
After I installed patched wine to make wc3 hosting work I lost some wine shortcuts from the programs menu. Now I got "Wine" there and inside is ONLY "Programs" and inside there I got games.

I used to have something like "Uninstall" and "Wine config" which is winecfg in terminal. I need at least know that what is the uninstall command or get those things there.

---

### Post by skunkTrader on 2008-07-21
On my system I have the following items

"Browse C:\ Drive"    xdg-open ~/.wine/drive_c
"Configure Wine"             winecfg
"Uninstall Wine Software"      uninstaller

---

### Post by YokoZar on 2008-07-21
Did you install from source then?  Or someone else's package?

The winehq and stock ubuntu packages create those links for you.

---

### Post by Akingboy on 2008-07-22
I installed from source
And thanks skunkTrader: I needed that uninstaller command

---

### Post by lamborghiniwang on 2008-07-22
I have never been able to figure out how Wine deals with the menu links, but you may find all of the shortcuts at $HOME/.local/share/applications/wine/Programs

An interesting thing is that, if you uninstall a program using Applications->Wine->Uninstall Wine Softwares, the menu link of that program would not be removed, but if manually remove the link using Sysmtem->Preferences->Main Menu, the same menu link won't appear in your gnome start menu even after you reinstall the program again.

---

### Post by Voland on 2008-12-10
> **lamborghiniwang said:**
> I have never been able to figure out how Wine deals with the menu links, but you may find all of the shortcuts at $HOME/.local/share/applications/wine/Programs

An interesting thing is that, if you uninstall a program using Applications->Wine->Uninstall Wine Softwares, the menu link of that program would not be removed, but if manually remove the link using Sysmtem->Preferences->Main Menu, the same menu link won't appear in your gnome start menu even after you reinstall the program again.

So I had the same problem. But after manual clean of ~/.config/menus and ~/.local/share/applications I've got it but can not update - [http://ubuntuforums.org/showthread.php?p=6342510](http://ubuntuforums.org/showthread.php?p=6342510) Could anyone help with it?

---

### Post by k@e on 2008-12-10
See my post here: [http://ubuntuforums.org/showthread.php?t=985120&p=6197728](http://ubuntuforums.org/showthread.php?t=985120&p=6197728)

EDIT: Did you actually delete everything that was in those two folders? If yes, then there is no chance to restore your lost shortcuts other than reinstalling your Windows software manually.

---

