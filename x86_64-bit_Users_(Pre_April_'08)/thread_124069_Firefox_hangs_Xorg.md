---
title: "Firefox hangs Xorg"
date: 2006-01-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by thull on 2006-01-31
I've had two cases in the last two days where using Firefox to surf web, I click on a link, the new page partly loads, then I see rectangles of display scatter randomly in window, then X system hangs, keyboard inoperative. I can ssh in from another system. When I run top, Xorg is running 99% cpu, accumulating near real time. I haven't found any way to just restart Xorg. Only thing that clears it up is reboot.

I've been running the system for over a month, but only ran into this problem yesterday and today. I updated the system a day or two ago, so that most likely introduced the problem. No new updates are available today.

Video board is MSI NX6200AX, NVIDIA GeForce 6200 GPU, so it's using Xorg driver NV.

It seems like I noticed references to a similar problem when I was recently (unsuccessfully) trying to research a problem where gnome-cups-icon perpetually writes an error message to ~/.xsession-errors every few seconds. (Is not doing that right now; no idea why it stopped.)

I've been using Red Hat-based distros for many years, but this is my first experience with Ubuntu or anything Debian-based. Having a lot of trouble understanding how this system is put together and how to debug it. (Xorg is also new to me.) Don't know whether this is a good place to register this. I've tried searching both these forums and the Malone bug tracker to no avail.

---

### Post by steo on 2006-03-28
I just installed breezy amd64 smp last week and I noticed the same problem. I click on a website in Firefox and X just suddenly hangs. However, I still can ssh in and I can see that xorg is using 99% of the cpu. I thought it was a firefox issue but I changed from the default ubuntu firefox to 32-bitfirefox 1.5.0.1 but it still hangs once in a while.

I am using the 'nv' driver because the 'nvidia' driver (8178) does not work. My graphics card is an Asus Geforce 6200 (Nvidia GeForce 6200 GPU).

The instability is driving me crazy. I've tried looking on this forum and the wikis but to no avail.

---

