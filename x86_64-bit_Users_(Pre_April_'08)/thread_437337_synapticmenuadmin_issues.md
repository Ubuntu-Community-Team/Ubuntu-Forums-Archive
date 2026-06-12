---
title: "synaptic/menu/admin issues"
date: 2007-05-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by lcolson on 2007-05-08
I'm currently having several issues with the Ubuntu 7.04 install that I think may be issues related with how Ubuntu grants administrator status.  First off, I installed 7.04 after running the live cd, and clicking on the "install on hard drive" icon.  

Issues:

1) I can't add the add/remove programs to the **Applications** tab by going to **System** --> **Preferences** --> **Main menu**, then checking the box for the program.  I can check it, but the check will remove itself after a few seconds, and it will not get added to the tab.  

2) If I open synaptic in a terminal, it will tell me that I'm starting without administrative privileges and any changes I make won't take effect.

I tried to use the sudo command prior to using synaptic and it has no effect.  Does anyone have any idea what I can do so that I can more easily modify my settings?  I have Debian installed on another cpu and it doesn't have these same issues.

Also, if anyone feels like shooting fish in a barrel... 

3)What do I need to do to get ubuntu to recognize my nvidea 7600GS video card 

4)and/or give me better resolution.  

5) I currently dual boot, and my girlfriend is scared of Linux, how do I modify the grub loader so that XP is the one that starts automatically, and I manually have tell it to load Ubuntu (oppisite of how it is now set up).

I would appreciate any help on these issues anyone could give me.  I have searched for answers to these issues and have not been having any luck.

---

### Post by Priapus891 on 2007-05-08
Man, I need help with numbers 1,2, and 5 also. 
* Patiently waits for response :D *

---

### Post by tapaculo on 2007-05-08
For number 5, you will need to modify menu.lst file
```
sudo gedit /boot/grub/menu.lst 
```
and change the default argument to the correct entry for windows.  You need to count the linux kernel options and the divider in the file.  I usually have to give it a couple tries before I get the correct number.

Sorry, I'm no expert but the nvidia solution will involve installing the nvidia-glx or nvidia-glx-new packages.  Try a search on those in the forum.  There is also a post on the wiki about nvidia proprietary drivers.

good luck

---

### Post by tapaculo on 2007-05-08
Wiki entry for the nividia drivers:

[https://help.ubuntu.com/community/Latest_Nvidia_Dapper](https://help.ubuntu.com/community/Latest_Nvidia_Dapper)

---

### Post by lcolson on 2007-05-09
I managed to solve issues 1) and 2) by going into the recovery option at start up and adding this line:

adduser <your username> admin

This appaerently adds your username to the admin group, which then lets you modify stuff.  I'll post back as soon as I try the other suggestions for changing the boot sequence.

---

### Post by Priapus891 on 2007-05-09
cool, even though this is not my topic im getting some of my main questions answered :D

---

