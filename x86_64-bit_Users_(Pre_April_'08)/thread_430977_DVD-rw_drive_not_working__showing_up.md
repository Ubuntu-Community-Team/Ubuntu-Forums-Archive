---
title: "DVD-r/w drive not working / showing up"
date: 2007-05-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by xeocub on 2007-05-02
Since noone replies in the other forums I decided to post this here aswell:


I just got a new DVD-RW drive and it does not want to work in ubuntu (feisty)
Bios detects it fine, windows 2k runs it fine, but here I cannot figure out why it doesn't work.

I've tried detecting it with various ways I've thus far found on the net:

I tried looking for it with Gparted, doesn't show.
I tried "ejecting" just about every mountable object in /dev/
I've tried sudo cdrecord -scanbus, everything else BUT the drive shows up..
some hotswap thing.. etc

It doesn't seem like it even shows up in the "device manager"

So what do I have to do to get this thing to work?

---

### Post by kuja on 2007-05-17
What's the model of the drive? Seeing as it's not showing up, and likely not even getting its own /dev device (if it's an IDE drive, it's almost definitely somewhere in /dev/hd*, you should probably report it as a bug on launchpad. I recommend also trying to recognize it with LiveCDs, Knoppix and/or older versions of Ubuntu would be a good bet, just to see if you can get it to work. Another thing potentially worth trying is to try it on a different IDE controller, or if necessary to play with the jumpers (dunno, I always had issues with "cable select", so I always set it to master or slave respectively) Plenty of things you can play with, I hope you can get it to work, or if you can't, confirm that it's a bug.

---

