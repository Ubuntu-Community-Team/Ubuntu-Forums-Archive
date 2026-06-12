---
title: "Minor problem."
date: 2006-07-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by Draknats on 2006-07-25
I'm new to Linux and Ubuntu, and have been trying to get my wireless card working.  I'm running on AMD x64 with a fresh Ubuntu 6.06 install.

In doing so, I needed to log in under the 'root' account.  For some reason, I was not allowed to log in as 'root', so I [recklessly?] modified a user setting in the user administration panel:  I changed the "/home/draknats" in my normal account ("draknats" to "/root" in hopes that I'd then be able to install my wireless chipset driver in conjunction with the "ndiswrapper -i Rt2500.INF" command.

Anyway, Ubuntu still boots fine, but when I go to login, I get an error message that is clearly the direct result of my setting change.  It'd be a bitch for me to go upstairs and write down the exact message, but I really just need to know how to manually revert to the original setting via the Ubuntu terminal.

Though, actually, a simpler solution might be found if I could somehow log in as 'root'.  I've tried that, but it tells me that I can't log in as root at that screen (the initial login screen), which doesn't exactly make any sense to me because I know its password and all.

---

### Post by Draknats on 2006-07-26
[http://www.ubuntuforums.org/showthread.php?p=1302181&posted=1#post1302181](http://www.ubuntuforums.org/showthread.php?p=1302181&posted=1#post1302181)

---

### Post by arkaos on 2006-07-26
I'm fairly new to Linux and Ubuntu as well, but I've been reading the Ubuntu docs for days now. As I understand, for root usage, any user with admin privilidges are to use the "sudo" statement to run a root level command and simply enter your own user password when prompted. Forcing Ubuntu to log on as user "root" is not necessary and very much not recommended. The "sudo" usage is supposed to be a secure layer between the user and the filesystem to prevent maliscious activity from damaging the filesystem.

I really don't know how to get back to the original user setting. I just posted this as food for thought. Good luck, and if you fix your problem, please post how you did it. I would really like to know.

---

### Post by Kilz on 2006-07-26
> **arkaos said:**
>  really don't know how to get back to the original user setting. I just posted this as food for thought. Good luck, and if you fix your problem, please post how you did it. I would really like to know.

If you use a sudo command and leave the terminal open for 15minutes it reverts automatically. You can also close the terminal to get the same result. If you need a gui to move files around in you can use 
```
gksudo nautilus
```to open the file manager up as root. I even added a menu shortcut to the System > Administration menu with the Alacarte Menu editor using the command.

---

### Post by Draknats on 2006-07-26
Indeed, arkaos, I discovered that myself AFTER I ****** up my user settings. (A la the link I provided in my second post.)
I wanted the system to recognize user "draknats" as root in order to install my wifi driver, so I fudged a setting by changing /home/draknats to /root, which is what's the cause of my inability to login as user draknats.

Hmm, "gksudo nautilus" didn't work; it said that I don't have authorization.  This didn't surprise me, because what I did essentially was render my the "draknats" user completely invalid.

The easiest solution for me at this point would be to create a new admin user from within the terminal (I can't boot GNOME at all).  I'm going out for a bit, so it'd be cool if someone could point me to (or provide) a set of instructions on how to create a user from the terminal.  If not, there ought to be instructions somewhere online. 

Anyway, much appreciation to both of you for your concern and advice.

---

