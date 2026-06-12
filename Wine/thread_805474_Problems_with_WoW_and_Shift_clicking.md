---
title: "Problems with WoW and Shift clicking"
date: 2008-05-24
forum: Wine
---

### Post by Eera on 2008-05-24
Hi there, I'm still fairly new to using Ubuntu as well as Wine so be gentle with me :p
A few days ago I managed to install Wine and World of Warcraft so I could start playing again, everything works fine (apart from when my resolution on desktop and ingame are different which causes a crash, but I can live with that).
The reason I'm posting though is one very annoying problem that I'm sure any WoW player can understand, for some reason I can left or right click fine, I can use Shift combined with any key on the keyboard and these work fine, but for some reason I cannot use Shift left/right click, as well as Ctrl or Alt clicking while I'm playing World of Warcraft, I've had a look through a few guides and asked in the World of Warcraft forums but no one has had any idea what can sort this, so I thought the best idea would be asking here.

I'm using the latest Ubuntu release (8.04 I believe it is) as well as the latest version of Wine.
Thanks in advance for any help
~Eera

---

### Post by ille.pugil42 on 2008-05-27
Unfortunately, I don't have anything to help, but I can add that WoW works fine for me -except- for the same exact problem.  I'm researching it as well, and I'll report back if/when I find some answers.

---

### Post by ille.pugil42 on 2008-05-27
...and guess what I found.  I went over to [http://winehq.org](http://winehq.org) and I found this page here: 


and it led to this post here:> 
This particular issue rest squarely with Metacity, I think. My wife had the issue on her WoW installation. Straight Hardy Gnome. I could shift-click away freely in Openbox. When I installed Openbox on her machine and replaced Metacity with OB as WM, The problem with shift-clicking vanished. Ctrl-clicking (Getting the Dresing Room to open, etc) worked like a charm, too.

Looks like the immediate solution is to replace metacity, which means giving up Compiz. May not be the prettiest, but until Metacity gets it&#347; fix, this should work.

Openbox. NEver thought that would be the answer to a WoW bug. :)

I'm not inconvenienced enough to have to switch WMs, but I will soon - I LOVE COMPIZ :)

---

### Post by ille.pugil42 on 2008-05-27
Ok, I got to keep Compiz and the lovely cube *and* get shift+clicking to work.  I removed wine 1.0 and installed wine 9.58 (found here: [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)) and then opened up winecfg and under the graphics tab, removed the check for "allow the window manager to control the windows".  I'd love to be running the latest version of Wine, but as of now I've got everything working wonderfully.  Hope this helps!


Sources Cited:
[http://ubuntuforums.org/showthread.php?t=459936&highlight=wow+shift+key](http://ubuntuforums.org/showthread.php?t=459936&highlight=wow+shift+key)
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=11329](http://appdb.winehq.org/objectManager.php?sClass=version&iId=11329)

---

