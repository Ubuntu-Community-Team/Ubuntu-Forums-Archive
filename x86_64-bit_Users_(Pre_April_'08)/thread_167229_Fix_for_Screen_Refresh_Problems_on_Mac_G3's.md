---
title: "Fix for Screen Refresh Problems on Mac G3's"
date: 2006-04-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by madpiratebippy on 2006-04-28
Hey guys, I wanted to post what I had a problem with on my machine, when I tried to switch my old B&W G3 to Ubunto.

I got everything to work, but then I would get a blue screen with an ugly, mean, red box that said something along the lines of "Refresh Rate outside of expected frequency, 60-80 hz", and then the screen would die. I spent about ten hours fiddling with this thing. ](*,) 

Basically, with the old-school blue and white macs, with origional monitors, the xorg.conf files aren't set up quite right. First, go to [www.apple.com](www.apple.com) and find the exact monitor you have and it's refresh rate. Second, so as soon as you get the computer to boot, switch it to a text-only screen, and and get to your xorg.conf files, and change the paramaters to match those of your monitor. I vaugely recall that what you want is to change it from the default 30-80 to 30-60, but like I said, this was at the end of 10 hours of battling the thing.

I finished it up two weeks ago and just threw out all my pen-and-paper notes, but that was the problem, and it's a relatively easy fix once you know what's going on. If you need to know how to get to the text-only command line, or to the xorg.conf files, check out [http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

Sorry I didn't document this better, but I hope that someone finds this and saves themselves 10 hours.

---

### Post by towsonu2003 on 2006-04-30
you might wanna post a bug report to launchpad ( launchpad.net/distros/ubuntu/ ) for the devels to fix this so Dapper G3 users don't go weird on their machines :) 

though I'm not sure devels would fix it -who knows.

---

### Post by Rxke on 2006-04-30
I have a blue&White G3 too, and haven't seen this problem, but then again, I have a fairly recent flatscreen (that's recent as in : 2002-ish)
So it is probably related to the original Apple screens? I do notice though, when I boot from the installCD (Breezy) my screen is nudged some pixels to the right, which might point to a 'weird' frequency-setting... After the full install it seems to rectify itself.

---

