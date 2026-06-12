---
title: "Blockland - No Internet Access on Ubuntu"
date: 2013-02-18
forum: Wine
---

### Post by Jincux on 2013-02-18
Hey there,

I'm trying to get a Blockland dedicated server to run on my Ubuntu server through Wine. It runs fine, but all internet access is dead. The game is compiled as 32-bit. When I open up a VNC connection and run the game, it works fine, but I'm using an automated start/stop system and console capturer (written in java) that can't use "wineconsole --backend=curses" because of an extremely hacky behavior, and running the game through plain "wineconsole" disables the console capture, and running the game through plain "wine" disables the internet access.

Does anyone know if this is a common issue among games and how to fix it?

Ubuntu 12.04.2 LTS
Wine 1.5.23

Thanks

---

