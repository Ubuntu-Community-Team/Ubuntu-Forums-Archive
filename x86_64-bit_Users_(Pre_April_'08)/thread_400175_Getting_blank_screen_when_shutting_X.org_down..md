---
title: "Getting blank screen when shutting X.org down."
date: 2007-04-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by Gelinder on 2007-04-03
Hi, I am a new Linux user. I tried it 10ish years ago but couldn't find my monitors syncs and got headaches :( Now I really want to get started with it again.

I've sucessfully installed 6.10 and updated it.
I'm having resolution problems, despite having reconfigured the xserver-xorg multiple times trying different settings. I have 23" LCD with 1920x1200 resolution but can only choose 1024x768. I've tried many tips I've read here, among them finding out my monitors vertical and horizontal syncs and entering them.

Problem are grafic card driver i figure since I havent installed any and are running it on the VESA setting.

The problem is that I get a blank black screen as soon as I exit the grafical interface. This happens when I do any of the following:

Ctrl + alt + f1
Ctrl + alt + backspace
Choosing Log Out, or Switch User from the Reboot meny in the OS.
sudo /etc/init.d/gdm stop

When I get the black screen its game over and I need to restart with the button on my PC.

Any way I can install the driver without getting the problem or anyway to fix the problem so I can install the driver?

My hardware:
Core2Due E6600
Asus Commando (Intel P965)
nVidia 8800GTX
2GB Corsair
Some sata drives and optical drive.

---

### Post by renzokuken on 2007-04-03
have a look at Envy to install your drivers (nice gfx card btw!!)

[www.albertomilone.com](www.albertomilone.com) and look at the projects/guides parts

---

### Post by Gelinder on 2007-04-03
I installed and ran Envy and everything seemed to work fine. After the reboot however I get a black screen with some wierd white blips after the Ubuntu splash screen(when I should be looking at the log in screen), then nothing.

---

### Post by Kilz on 2007-04-03
In the past its been necessary to revert to older versions of drivers to avoid this problem.

---

