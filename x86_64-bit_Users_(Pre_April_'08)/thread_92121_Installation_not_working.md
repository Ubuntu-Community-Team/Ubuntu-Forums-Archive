---
title: "Installation not working"
date: 2005-11-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by ddevore on 2005-11-18
I am trying to install the 64bit version with win xp. I installed Ubuntu without any problems on a clean HD on the same computer. But I need win also so I am trying to do a dual boot. 

This are the problems:

During the install it will not accept a user. It keeps asking for the same information and doesn't give an error. 

Then in the second stage: 
It asks multiple times (3 I think) for the video card settings, I don't remember this from the first time I set it up. 

When it gets to the user part it asks for the root password and gives a warning about not having another user but instead of setting one up it asks for a password and then gives a warning about the user not being valid. 

When I get through the installation it gives me a xserver error with not a whole lot of information in the logs, something about a value not being available. When I check the xorg.conf file it is empty, completely empty. 



Now when I installed it before without trying the dual boot it worked fine, though I did have some problems with the dual monitors, the xserver started and it allowed me to try to config things correctly. But I don't remember the same amount of installation questions. 

Any suggestions.

---

### Post by Ocxic on 2005-11-28
When your asked about the user info, the first dialog is for the users real name, the second is the user name for the computer, mine is admin, the third if for the user password, entring the wrong info can put u in a loop and keep asking for info untill u get it right.

---

### Post by ddevore on 2005-12-01
I found that if I have the /usr/local directory or the /home a fat32 partition the loop happens if not it works fine. Yes I even tried different names for the real/login name with no success.

---

### Post by RAOF on 2005-12-01
[QUOTE=ddevore]I found that if I have the /usr/local directory or the /home a fat32 partition the loop happens if not it works fine. Yes I even tried different names for the real/login name with no success.[/QUOTE]
I'm not surprised that the install doesn't work well if important directories are on FAT32 - it has no support for permissions, which are an integral part of the install process.

---

