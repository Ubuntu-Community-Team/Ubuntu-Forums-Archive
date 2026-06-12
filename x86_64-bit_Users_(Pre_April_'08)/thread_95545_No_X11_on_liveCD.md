---
title: "No X11 on liveCD ?"
date: 2005-11-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by juanfer2k on 2005-11-26
Hi all
am loading liveCD on eMac and get blank screen after charge ubuntu brown screen.

when trying to edit etc/X11/xorg.conf
 HorizSync to 70-73
 VertRefresh to 70-140
as read on this forum to solve silimar issues... i can't find any X11 folder on any mode live-expert-powerpc an others... 

So, What to do to have video mode on Ubuntu?

---

### Post by ssam on 2005-11-27
are you new to the linux commandline?

---

### Post by linear on 2005-11-27
[QUOTE=juanfer2k]i can't find any X11 folder on any mode live-expert-powerpc an others... 

So, What to do to have video mode on Ubuntu?[/QUOTE]

In order to edit xorg.conf:

After booting is complete (just normal "live" boot will do),
1. ctrl-option-F1 (should give you a command prompt)
2. type: sudo nano /etc/X11/xorg.conf (return)
3. make your edits
4. ctrl-O (return) to write edited file
5. ctrl-X to exit nano back to command line
6. type: sudo /etc/init.d/gdm restart (return) to restart Gnome

Good luck.

---

### Post by juanfer2k on 2005-11-27
Thanks A Lot! 
Just What I needed, Im writing this from the same Ubuntu, I cant believe this, an Yes am totally new to command line, Linux, an of course Ubuntu, I now i'll enjoy a lot using linux
Thanks Linear:D :D :D

---

### Post by linear on 2005-11-27
Glad it worked for you. Unfortunately, with a live CD you will need to do it every boot... :(

---

### Post by jonathanp on 2006-03-17
Hey I've been having the same problem.
Only etc/X11/xorg.conf doesn't exist!
Should i run the install CD again?

---

### Post by tidris on 2006-03-17
[QUOTE=jonathanp]Hey I've been having the same problem.
Only etc/X11/xorg.conf doesn't exist!
Should i run the install CD again?[/QUOTE]
The correct path is /etc/X11/xorg.conf  
The / at the beginning is important.

---

