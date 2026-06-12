---
title: "ubuntu/wine/wow runs with garbled split screen"
date: 2008-09-08
forum: Wine
---

### Post by jal3 on 2008-09-08
I'm using UBUNTU Hardy Heron on an Acer Aspire with an ATI Radeon x1400.  I've got WoW installed. All the screens outside of the game look fine (launcher, download windows).  

When I run WoW however, the screen splits into two identical screens--almost as though I have two desktops on the same screen.  The screens are somewhat garbled as though the resolution is wrong, but I can login. I can get to the screen where you choose the realm but it is too garbled to tell what I'm supposed to check.

I've tried most of the tweaks I've found in the help forums and even used the one that starts WoW in a separate window, but nothing seems to help.  It seems to be most readable in the 1024x768 mode, since vertically, everything is aligned.  Any other resolution looks much worse.

Any suggestions would be appreciated.  I've spent a couple of days just getting WoW installed.

---

### Post by AceOnline on 2008-09-08
After intensive installation and re-installation of Linux & different versions of ATi drivers. I have concluded that the Issue is probably lying with the graphics drivers and it's compatibility with Wine. 
I do not have a Nvidia card or I would have loved to give the card a test and see how would have things gone with Wine+Nvidia!

Right now I'm on the latest ATi Drivers dated as of 20th August 2008 with Wine 1.1.3 which apparently has a gold rating from most users since it is running the game(Team Fortress 2 in Steam) well for them.

Everytime I run the game up, the screen gets messy, It's like some of the game is on the left side of the screen and some of it on the right side, and I can make out the desktop compressed to an inch wide size right smack in the middle of the monitor and the two game parts on different sides. The whole screen is awfully pixelated! I'll Try to take a picture with my bro's mobile and Attach it here soon, hopefully!

---

### Post by jal3 on 2008-09-08
Those are my symptoms exactly. Both games screens look exactly alike to me though.  Hopefully, someone else will have encountered it and found a fix.  

A new graphics card is not an option for me, I'm using a laptop and I think it's integrated with the MB.

---

### Post by Eviljim on 2008-09-08
Heres some things to try.

1. Try using ATI driver 8.4.
2. Try Wine 1.0 and newer.
3. Make sure you have the extra lines added into your config.wtf file.

See here for those lines.

[https://help.ubuntu.com/community/WorldofWarcraft]("https://help.ubuntu.com/community/WorldofWarcraft")

Especially the Opengl and M2Useshader lines.

---

