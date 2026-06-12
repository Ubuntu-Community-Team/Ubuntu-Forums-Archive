---
title: "ubuntu on ibook g3 300Mhz"
date: 2005-10-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by clamshell77 on 2005-10-18
Hi all. I've just installed ubuntu 5.10 on my ibook g3 tangerine. I've a problem with the windows manager start.
With xdm, after login I get only an empty colored screen and stop. With startx only the typical screen before the gnome start and again stop. There is the pointer that also I can move but only that. The console mode is ok, so I can modify a configuration file if it's necessary. But I don't know what to do. Any suggestions? :confused:

---

### Post by guoweiok on 2005-10-18
maybe you can try to reconfigure your X environment by 
$: sudo dpkg-reconfigure xserver-xorg

---

### Post by clamshell77 on 2005-10-18
Thanks, but i've found solution. The problem was the date. It was about in 1900 and it is all ok since i put 2005. Why? I don't understand the fact that the console was ok with 1900 and gnome not. Bohh :-)

---

