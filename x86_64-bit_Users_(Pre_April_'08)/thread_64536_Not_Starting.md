---
title: "Not Starting?"
date: 2005-09-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by IvanGrozny on 2005-09-11
I tried installing the 5.04 version of Ubuntu for the 64 bit processor, and i have a 64 bit AMD Athlon 3200+, it gets to the login screen, I log in but it wont start, it just doesent display any icons or starting up screen, just freezes, is there anything I can do to solve this problem?

---

### Post by mlomker on 2005-09-11
When you say login screen, do you mean you are getting to the graphical login screen or a text prompt?  My first thought would be that it's a video driver problem.

---

### Post by IvanGrozny on 2005-09-11
its the graphical screen, i dont think theres a driver issue at all.

---

### Post by XopherMV on 2005-09-12
I'm also having this exact same issue as well.  I login, then it freezes right before it should load the desktop.  I'm running an AMD 64 4000+ with an ATI Radeon Xpress 200M graphics card.

---

### Post by Jiilik on 2005-09-13
When you get to the login screen, hit CTRL-ALT-F1 really fast.  It should dump you to a prompt. 

Then, type "sudo nano /etc/X11/xorg.conf" and under the section that says: Section "Device", either change "ati" to "vesa" OR add the line as follows:
Option "noaccel" "true"

Edit: oh, and then either reboot or restart [gkx]dm.

---

### Post by atrus325 on 2005-09-13
It's your graphics card, promise.

edit your xorg.conf in /etc/X11 and change the ati driver to vesa.  See if that fixes it.  If not, then I really am wrong and it's a different problem, but I bet it'll work.

J.

---

### Post by mlomker on 2005-09-13
[QUOTE=Jiilik]Then, type "sudo nano /etc/X11/xorg.conf" and under the section that says: Section "Device", either change "ati" to "vesa" OR add the line as follows:
Option "noaccel" "true"
[/QUOTE]

What he said.  You could also select the 'rescue' option of the grub menu.  I didn't know about nano...looks a lot friendlier than vim.

Changing the line to VESA will result in a slow video setup but it'll serve as a good test.  If things work under VESA then you can look at installing the latest ATI driver (it can be an adventure and I've helped a number of folks do it).

---

