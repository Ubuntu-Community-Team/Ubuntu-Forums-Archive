---
title: "I need the so called &quot;Virtual Desktop&quot;"
date: 2005-11-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by clamshell77 on 2005-11-18
Some years ago I used the virtual desktop features to use software with large windows(in that cases that is impossible to use it resizing windows) with 14 inches PC monitors(with max 800x600 res). Now after a long time I need again that feature with the last Ubuntu installed on Ibook 13 inches. I don't know how to set it. i don't know even if the correct term is "virtual desktop". I've tried to modify xorg.conf with the word virtual followed by 1024x768. But I've had to return to the original file because the xserver didn't start with the new configuration. Could anyone help me please? The part of the xorg.conf to modify and the right syntax are welcomed. Ahh with ubuntu there aren't xorg configuration tool like xorgcfg xorgconfig(i don't know why...) and i don't want to install a generic deb version of xorg(with xorgcfg etc...) because the os runs ok and i don't want any more problems :-) above all with graphics. I need that features to use electric(an electronic design software). thanks in advance for your replies :confused:

---

### Post by felix_stegerman on 2005-11-18
According to [http://wiki.x.org/X11R6.8.2/doc/xorg.conf.5.html](http://wiki.x.org/X11R6.8.2/doc/xorg.conf.5.html),
you should add
 Virtual 1024 768
to your "Display" section.


Felix

---

### Post by clamshell77 on 2005-11-18
I try it now. thanks

---

### Post by clamshell77 on 2005-11-18
All is okay now. Thak you very much. Ciao:p

---

