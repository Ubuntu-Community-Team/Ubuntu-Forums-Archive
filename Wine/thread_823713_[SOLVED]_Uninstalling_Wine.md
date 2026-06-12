---
title: "[SOLVED] Uninstalling Wine?"
date: 2008-06-09
forum: Wine
---

### Post by EnergySamus on 2008-06-09
Hi!
I tried to uninstall wine, but the folders are still there. According to Synaptic and add/remove, Wine is completely gone from my PC. Should I just delete these folders?

EnergySamus

P.s: the folders are in my home directory

---

### Post by dje on 2008-06-09
yes it is safe to delete the .wine folder in your home folder but you will lose all of your wine settings and programs you installed in wine so if you ever want to install wine again you will have to reconfigure it and re install all your windows programs again

hope that helps,
dje

---

### Post by 4th guy on 2008-06-09
Go ahead, the only files in that folder are the programs you installed and their settings.

---

### Post by Sammi on 2008-06-09
If it's gone from Synaptic, and you aren't worried about deleting any program you installed with Wine, then it's safe to delete the .wine folder in you home folder.

The .wine folder contains the fake disk drives that wine uses + some configuration files. Usually there's just a fake C: drive in the folder named drive_c.

---

### Post by EnergySamus on 2008-06-09
Thanks! I just wanted to make sure that it was ok! I wanted to reinstall Wine in the first place, but accidentally deleted it:oops:


Thanks
EnergySamus

---

### Post by EnergySamus on 2008-06-09
Ok, now I have another problem! When I go to my applications menu, there is still a WINE area. There is nothing inside of the folder, but I can't delete it! Does anyone know?

Thanks
EnergySamus

---

### Post by dje on 2008-06-09
Right click on the menu bar on the panel and select edit menus. In the left hand column of the window that opens select Applications and then in the right hand column either untick Wine or right click it and select delete

hope that helps,
dje

---

### Post by EnergySamus on 2008-06-09
Thanks again!

EnergySamus

---

### Post by dje on 2008-06-09
No problem :KS

dje

---

### Post by Victormd on 2008-06-09
You can safely remove this folder as well:
~/.local/share/applications/wine

---

### Post by Jedah on 2008-06-09
When I tried to delete a menu item created by an application installed to Wine my whole Application menu disappeared! The file $HOME/.config/menus/applications.menu is 0 bytes! Can somenone help me with this? Can I restore the applications menu as it was previously? The undo files in the same folders contain only menu changes not the whole menu...

---

### Post by tom66 on 2008-06-09
Also, there's no need to reconfigure it after reinstalling wine, as soon as wine notices .wine is missing (e.g. running an application under wine), it recreates it and does all necessary stuff.

---

### Post by Jedah on 2008-06-09
I was not clear enough...
The WHOLE Applications menu is gone! Everything! Accesories, Games, Development, etc. The corresponding config file is 0 bytes, therefore no applications menu is displayed at all. How can someone solve this? I cannot reinstall all applications from scratch...

---

### Post by dje on 2008-06-09
> **tom66 said:**
> Also, there's no need to reconfigure it after reinstalling wine, as soon as wine notices .wine is missing (e.g. running an application under wine), it recreates it and does all necessary stuff.

yes but it just creates the default wine settings, if you have custom settings they will be lost

---

### Post by dje on 2008-06-09
> **Jedah said:**
> I was not clear enough...
The WHOLE Applications menu is gone! Everything! Accesories, Games, Development, etc. The corresponding config file is 0 bytes, therefore no applications menu is displayed at all. How can someone solve this? I cannot reinstall all applications from scratch...

what happens when you go to System >> Preferences >> Main Menu?

ps. you would probably do better creating a new thread as the OP has marked his problem and this thread as solved ;)

---

### Post by Jedah on 2008-06-09
The main menu settings program won't start at all....

Found a fix [here]("http://ubuntuforums.org/showthread.php?t=527580&highlight=fix+disappearing+menu+icons+shortcuts") but the problem persists when trying to delete a specific menu item again.

---

### Post by Victormd on 2008-06-10
Please post the steps you're taking to delete it... it should be straight forward
right click on top of the menu, edit, click on the WINE menu, and un-check it. If you want to delete it, you'll have to open the WINE menu and delete the entries inside it and only then will you be able to delete the WINE menu... just un-check it and you'll be Ok...

---

