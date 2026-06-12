---
title: "[SOLVED] Gnome applications start as blank frozen panels"
date: 2008-05-15
forum: x86 64-bit Users
---

### Post by Êisdur on 2008-05-15
I looked for this bug in several places all over the internet, but it seems it has not been reported yet.

I've upgraded my PC from Feisty to Hardy in two steps. First, I've upgraded from Feisty to Gutsy using apt-get dist-upgrade, and then I've upgraded from Gutsy to Hardy. After the upgrade, gnome applications cannot start. Although the Gnome environment starts, when I try to open an application, it opens as a blank frozen panel which I cannot resize or click onto it. Even the terminal window cannot be open: it starts as a blank panel and then becomes greyish. Startx sessions also do not work: besides the blank pannels, applications have no top menu (I mean, no frame; they are simple panels glued onto the desktop, not resizable, clickable, etc). Restart buttons also do not work. 

It seems the mouse works normally. KDE works normally and I can still use the computer, although I would like to have Gnome back.

Before hardy, I had Gnome problems under Gutsy: after login, Gnome froze in a brown tan splash screen. Mouse functionality was ok, but, otherwise, nothing happened. That&#347; why I decided to return to Feisty, until yesterday, when I took the courage to try to bypass the problem by updating to Gutsy and then to hardy, hoping the bug was fixed.

I don't have much experience on linux. The hints I can give you in hope to find a solution are some lines in the Xorg.0.log after a failed Gnome session:

```
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
```

This block repeats 4 times in the end of the Xorg.0.log. I'm not sure this could point to the cause of my problem.

I use an intel video adapter. The driver in xorg.conf was set to i810 by Hardy during the installation.

Any help is appreciatted.

---

### Post by doobydave on 2008-05-17
I wouldn't be at all surprised if what you are experiencing is due to the upgrades between distros.

Try downloading the latest intall cd and seeing if you still experience the same.

---

### Post by Êisdur on 2008-08-11
Last week, I've managed to solve this bug by completely removing Gnome and reinstalling it from the ubuntu repositories after restarting the PC.

---

