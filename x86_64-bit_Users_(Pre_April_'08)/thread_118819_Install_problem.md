---
title: "Install problem"
date: 2006-01-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by markim on 2006-01-17
I've used the 32 bit ver of Ubuntu in the past, install and live.
Now that I have a 64 box, I figure why not try Ubuntu64.
When I try the live CD all gets loaded fine up untill the desktop loads.
Nothing but a brown screen. I thought I nurned the CD wrong so tried the install cd, same thing, brown screen nothing else.
I tried the expert intall, same thing, brown screen.
Any idea whats up?

:confused:

---

### Post by jim-fwb on 2006-01-18
I'm no guru, but here's what's given me the best Ubuntu-64 desktop:

1) install as a server

2) sudo apt-get update, followed by 

3) apt-get dist-upgrade, followed by 

4) apt-get install ubuntu-desktop.

Other installs required me to run "dpkg-reconfigure xserver-xorg" & choose a vesa driver before I got a working desktop & then it didn't seem to work as well.

Hope this helps.

[My hardware AMD 64 @ "3700" (Socket 939) with ATI Express 200 integrated graphics.  Not much support for the latter under default , i.e. not updated, install]

---

### Post by dsierpin on 2006-01-20
I have an ATI graphics card, and I had to get rid of the 3D acceleration for it to work.  You can either switch to the vesa driver like jim said, or you can get rid of the accelerated graphics by adding a line in /etc/X11/xorg.conf that says

Option        "NoAccel"

In the video card module section.  Hope this helps!

---

