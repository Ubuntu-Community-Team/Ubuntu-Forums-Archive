---
title: "Editing the Application-&gt;Wine-&gt;Programs folders?"
date: 2008-06-21
forum: Wine
---

### Post by temaki on 2008-06-21
I tried to install my TomTom HOME software without success and now have removed it but the folder is still under the Application->Wine->Programs list. Can someone tell me how I can delete the folder from there?  

thx
T

---

### Post by atomkarinca on 2008-06-21
Right-click the menu and select "Edit Menu". Under Wine > Programs right-click the entry you want to delete and select delete. That should do it.

---

### Post by temaki on 2008-06-21
Got it!  Thought it would be a wine configuration.  Many thanks!

T

---

### Post by atomkarinca on 2008-06-21
No problem.

---

### Post by quequotion on 2010-02-12
That is the proper way to edit ubuntu menu items, but there's definetly more to it in wine. Applications that make their own menu entries make more than just a .desktop file. Furthermore, the location, filenames, and content of those files are odd to say the least.
I'd also like to know the proper way to edit wine's menu. I'd also like to see alacarte done away with permanently (has there ever been a more cumbersome means of making menus??)

---

### Post by Melcar on 2010-02-12
The menu entries for WINE are stored in the /.local/share/applications/wine folder.

---

### Post by Soulcage on 2010-02-13
Give this a read [http://wiki.winehq.org/FAQ#head-9893ae50079ca7a959258f0bc9a17aaf2e69b391]("http://wiki.winehq.org/FAQ#head-9893ae50079ca7a959258f0bc9a17aaf2e69b391")

---

### Post by quequotion on 2010-02-26
> **Soulcage said:**
> Give this a read [http://wiki.winehq.org/FAQ#head-9893ae50079ca7a959258f0bc9a17aaf2e69b391]("http://wiki.winehq.org/FAQ#head-9893ae50079ca7a959258f0bc9a17aaf2e69b391")

This is good guide for *removing* shortcuts, but not creating them.

I've looked into this a bit more and indeed there is more to it. If you want shortcuts that launch wine applications properly, you have to create them in a windows-like method. (Create a .lnk file with an installer and a corresponding registry key) There's a shareware program that can do this called "Total Commander" although it's a bit confusing (mouse support doesn't work well but it can be done with the keyboard). It would be nice if wine had it's own native Start Menu editor like windows has, but... it doesn't.

**This is what ought to happen:**
During installation a .lnk file is created and saved into the start menu directory. Wine then triggers the creation of a corresponding .desktop file to create a linux menu item. When the software is uninstalled, the .lnk is removed and wine removes the .desktop file, clearing the item from the linux menu as well.
In wine's native Start Menu editor, when shortcuts are modified or moved, the .lnk files should be updated and wine should update the .desktop files to match those changes.

***This is what does happen:***
During installation a .lnk file is created and saved into the start menu directory. Wine then triggers the creation of a corresponding .desktop file to create a linux menu item. When the software is uninstalled, the .lnk is removed and wine *does nothing about the .desktop file*.
Wine does not have a native start menu editor, so when shortcuts are modified or moved (by the linux menu editor), the .lnk files are not updated and the start menu folder and the linux menu become incoherent.

As a result, there are often duplicate, broken, or missing shortcuts in the linux menu (and not only in the "Wine" section!) and serious complication of the "open with" dialogue's list of choices.

##UPDATE##

I just realized my post is way off topic!

---

### Post by quequotion on 2010-03-04
> **quequotion said:**
> Wine does not have a native start menu editor


Oh wait, yes it does: ```
wineshelllink
``` but it's command line only...

---

### Post by paul7net on 2010-03-05
> **Melcar said:**
> The menu entries for WINE are stored in the /.local/share/applications/wine folder.
Thanks, that helped. But they under the Home folder.

---

