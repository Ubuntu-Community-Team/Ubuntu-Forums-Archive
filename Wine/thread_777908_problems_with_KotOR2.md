---
title: "problems with KotOR2"
date: 2008-05-01
forum: Wine
---

### Post by evil_urna on 2008-05-01
I did a normal install from disks with wine. My problem is when ever I try to actually play the game it will only play in windowed mode. I tried forcing it into fullscreen with the config file to no avail. Any help would be greatly appreciated.

---

### Post by cogadh on 2008-05-01
I'm assuming that you are not running Wine with the "virtual desktop" enabled.

When you say you tried forcing it with the config file, do you mean you tried to manually edit the swkotor2.ini file and change **all** "FullScreen=0" references to "FullScreen=1"? There are actually two places in the file that have that entry; the first is just for the cutscenes while the second is for the game itself. If you don't change both, it will probably stay in windowed mode.

BTW - Have you tried just htting ALT+ENTER when the game launches in a window? That is the game's default command for switching from windowed to full screen.

---

