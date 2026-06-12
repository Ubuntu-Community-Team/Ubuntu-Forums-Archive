---
title: "8 bit graphics - Wine or Ubuntu?"
date: 2008-08-29
forum: Wine
---

### Post by Minguo on 2008-08-29
Ok, so I'm trying to run a game that requires 256 colors.

The console says that It can't switch to 8 bit from 36 or 24 or whatever, so I tried some of the 256k workarounds on the wine site here:
[http://wiki.winehq.org/256ColorsWorkarounds](http://wiki.winehq.org/256ColorsWorkarounds)

but I can't spawn an Xnest session in 8 bit mode (It just sits on a black screen), and while the game would start up if I did it with vnc4server, the colors were in black and white and the text was unreadable.  

So I thought I'd just change my xorg.conf to 8 bit and reboot, however when I do that, at the log in I get a message stating that ubuntu is running in 'low color mode' and when trying to run the game the console complains that it can't switch from 16 bit to 8 bit graphics.  

Is this a wine problem, or is there something wrong with X/Ubuntu that can't do 8 bit graphics?  The fact that I can't open an xnest window in 8 bit color depth apart from wine seems fishy.

---

