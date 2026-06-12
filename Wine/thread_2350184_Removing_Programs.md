---
title: "Removing Programs"
date: 2017-01-22
forum: Wine
---

### Post by apol1 on 2017-01-22
Hi, I just tripped on my shoelaces and installed EA download manager while attempting to install The Sims 3 using wine

I want to get it off and Id hate to completely reinstall my whole system just for one weird program

So how do I do this? 

Thank you for your help

---

### Post by wildmanne39 on 2017-01-22
*Thread moved to **Wine**.*

---

### Post by howefield on 2017-01-22
Have you tried using the Uninstall Wine Software application ?

Search for wine in Dash and launch *Uninstall Wine software*".

---

### Post by apol1 on 2017-01-22
Im guessing you mean the swirly thing at the top of the tool bar, lol im very new. I went ahead and tried that but I got nothing. I installed wine through the Ubuntu software center and also removed it the same way. I can't find the actual file the EA manager comes from either, I might have to use command line once i learn what to type in.

---

### Post by howefield on 2017-01-23
If you have removed Wine already you might still have some hidden files in your home folder, open up the File Manager which should open in your /home folder, press the Ctrl + H keys to show hidden files/folders and look for a folder called .Wine - delete it.

---

### Post by apol1 on 2017-01-23
Very cool, but no dice, I deleted the folder and searched my dash for EA, its still haunting my computer

---

### Post by deadflowr on 2017-01-24
Look in the hidden folder /home/you/.local/share/applications.
This is where the launchers you would see in the dash for wine apps will be located.
They'll be marked as .desktop files.
Removing these should clear them from the dash.

Note it might not take automatically since you also need to reload the database.
A logout login should work to fix that.

---

### Post by yoshii on 2017-01-25
For future reference, there's a really nice freeware Windows / wine-compatible program called MyUnInst(aller).  It's on [http://nirsoft.net](http://nirsoft.net)

It's one of the many very useful utilities.  At the very least you can use it to verify if parts of Wine and related Windows pieces got installed.  And you can use it to remove them pretty calmly similar to how Windows does it.

---

