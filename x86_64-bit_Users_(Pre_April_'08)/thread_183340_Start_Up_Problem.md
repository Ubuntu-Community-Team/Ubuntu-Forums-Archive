---
title: "Start Up Problem"
date: 2006-05-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by Skia_42 on 2006-05-27
I was successfully able to install Ubuntu on my eMac and the 2nd part of the installation occured without problems. When I start up my computer with Ubuntu it starts up and everything shows up as "ok" but after that I get a black screen with a white underscore blinking. The underscore then goes away and it stays black. (I have left it alone for an hour with no change.) Does anyone know what is wrong?

---

### Post by nkbj on 2006-05-29
Looks like a Xorg configuration error.

---

### Post by Skia_42 on 2006-05-29
Okay, would reinstalling Ubuntu help? If not does anyone know how I could fix it?

---

### Post by linear on 2006-05-29
Try first:

Ctrl-option-F1 to get a shell prompt. If that works, then enter
**sudo** **dpkg-reconfigure xserver-xorg**. This will re-do the configuration.

---

### Post by Skia_42 on 2006-05-30
I was able to get to the shell prompt and get to the re-do configuration. When I get to the point where I define the depth color in bits I get a warning that shows up in the command prompt. It is: "xserver-xorg postinst warning: overwriting possibly-customised file; backup in /etc/x11/xorg.conf. 20060538222" My question is how do I navigate back to main window and continue the re-configuration (and get out of the prompt)?

---

### Post by nkbj on 2006-06-01
If you get a prompt try to type 'reboot' and see if it works. Another problem could be the 'date bug'. Before you reboot type 'date' and see if the output makes sense. If not: Set the date before rebooting using 'date --set'.

---

### Post by Skia_42 on 2006-06-01
The date was set correctly so that is good but now I cannot even access the command line. I am going to wipe everything and install Dapper Drake. Thank you Nkbj and Linear for your help.

---

