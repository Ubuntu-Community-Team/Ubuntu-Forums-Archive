---
title: "Add Wine to Menu"
date: 2008-06-28
forum: Wine
---

### Post by bossa on 2008-06-28
Hi all 
I have done something stupid and somehow deleted Wine from my menu!
Can some one please tell me how to put it back . Progammes and preferences,registry editor etc
Thanks ;)

---

### Post by Kevbert on 2008-06-28
Right click on Applications and select edit menus.  Tick the Wine menu (where you decide you want it as there's at least 2 places available).

---

### Post by bossa on 2008-06-28
> **Kevbert said:**
> Right click on Applications and select edit menus.  Tick the Wine menu (where you decide you want it as there's at least 2 places available).

Hi Kevbert

Hmm yeah..thats the problem I have deleted it from there !!! Why or how I did this I dont know .(must of been half a sleep). So the Wine is not in th edit menu. How would I go about adding it and what would be the command?

---

### Post by Kevbert on 2008-06-28
Probably the best thing to do is to go to Synaptic, search for wine and mark for reinstallation, then apply.  There are four wine items that are displayed in the menus.

---

### Post by bossa on 2008-06-28
> **Kevbert said:**
> Probably the best thing to do is to go to Synaptic, search for wine and mark for reinstallation, then apply.  There are four wine items that are displayed in the menus.

Hi Kevbert 
Tried that earlier with no luck I'm afraid :confused:

---

### Post by Kevbert on 2008-06-28
OK.  You can do this manually but may have problems with what icons are displayed.
Firstly you want to check if the commands still work in terminal
Here are some:
```
notepad
winecfg
xdg-open ~/.wine/drive_c
uninstaller
```
These are the four menu items within wine.  In each case they should run a wine application.  If all goes fine, we can now generate some menus/items.
Right click on Applications. Select Edit Menus.
Let's create the Notepad menu item.  Under Applications add a menu 'Wine' (without quotes).  Now under Wine create a new menu 'Programs'.  Under Programs create a new menu 'Accessories'.  Under Accessories create a new item Application  Name - Notepad  Command - notepad  Comment - A clone of Windows notepad.
Under the Wine menu create new items (all Applications) as follows:
Name - Browse C:\Drive  Command - xdg-open ~/.wine/drive_c  Comment - Browse your virtual C:\Drive
Name - Configure Wine   Command - winecfg                   Comment - Change application specific and general wine options
Name - Uninstall Wine Software  Command - uninstaller       Comment - Uninstall Windows applications for Wine
Hopefully you'll now have all working wine menu items.

---

### Post by bossa on 2008-06-28
I keep getting an error 

: Could not launch menu item 
                          Failed to execute child process "/home/steve/.wine/drive_c/Program" (no such file or directory)

---

### Post by bossa on 2008-06-28
OK Kevbert Sorted it out now. I was putting the wrong address.
Thanks for your help mate ;)

---

