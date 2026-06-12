---
title: "Stuck on splash (network icon)"
date: 2009-05-12
forum: x86 64-bit Users
---

### Post by obdu on 2009-05-12
Hi.

I recently installed kubuntu. It has worked fine so far, but earlier today something snapped. At first, I lost connection to the Internet and my router. Several seconds later an error message of some sort popped up telling me that something that handles KDE connections had failed. Unfortunately, by instinct, I shut the popup before I had time to read it trough.

At first I thought it was a minor problem that would probably fix itself with a reboot. Well, I never found out if it would, as since then I haven't been able to reboot. The splash screen jams to the third icon, the blue globe. I'm on live CD now, and everything works just fine.

Since I'm new to linux, I don't really know which conf files I should paste to reveal where the problem lies, so I pasted the logs files that seemed potentially useful from the last boot.

Any ideas?

---

### Post by pixel :-) on 2009-05-12
Have you set automatic upgrade in the background?

Disconnect your router, maybe it will allow you to boot.

It could be hardware problem, stuff don't just get broken on there own. Do a memory test, 3° in the grub.

It stops at the globe, so it's actually in KDE that get blocked.
ctrl+alt+del works? or you had to do a hard reboot?
ctrl+alt+shift reboots the screen only, it works?
You have automated login anabled? If KDM workds

Maybe the .kde folder got corupted in some way, kde4 is not quite stable.
In grub start the 2° option, drop in a shell, use 

for real men

for a new user

adduser newuserName
adduser newuserName admin

nano is just a text editor

nano /etc/kde4/kdm/kdmrc

near the bottom section
[X-:0-Core]

change the valiou of
AutoLoginEnable=true

to false

this way you will not autologin

for little girls

startx 

is that command for gnome only? i don't remember, i guess you'll find out.

with a gui tool add an other user(with admin group, so that he can use sudo), and remove your self from autostart
close it

continuou normal boot, and login at the new user and cross you fingers that it works.

Sory i couldn't figure out something usefull from the logs, but this doesn't man anything. Some one else might.

If it doesn't work, detail what happens at each of the tries

---

### Post by obdu on 2009-05-13
I left my computer on at the jammed state and approx few mins later I got an error message about KDE not being able to start because something had no writing privelages to home/usr/.ICEauthority.
I sudo chmodded it to 777, and got KDE running just fine. Is this a major security flaw?

...But I cant get internet to work unless I completely disable the firewall (by using guarddog). For a former windows user this doesn't sound like a very good idea. I've tried ipconfig -F and reseting to factory defaults with guarddog... No results. What do you think I should do with that?

---

