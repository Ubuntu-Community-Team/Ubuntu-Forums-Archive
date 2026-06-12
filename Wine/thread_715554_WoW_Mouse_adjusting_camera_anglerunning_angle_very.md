---
title: "WoW Mouse adjusting camera angle/running angle very jerky"
date: 2008-03-05
forum: Wine
---

### Post by Rae III on 2008-03-05
Hey, I'm a relative n00b when it comes to Linux, just made the switch last week and I'm rather thrilled. I got WoW running no problem, just followed the really simple guides, but I'm having a problem with my mouse. When i hold down either the left mouse to adjust just camera angle or the right mouse to adjust both camera angle and facing, it will often start randomly changing my angle, often to directly behind. I'm currently leveling my paladin so this isn't a huge problem at the moment, but I have to switch back to xp to play my rogue, which is rather annoying.

Now here's the interesting part. I'm running duel monitors from a Nvidia 7900 GTX. One is a CRT at 1600x1200 connected through VGA, the other is an LCD at 1680x1050 connected through DVI. I run WoW in windowed mode because 1) it allows me to quickly switch out of the window 2) my LCD is my main monitor placed directly in front of me and the CRT is to the right, but Ubuntu recognizes the CRT as the main monitor, so I am forced to put it in windowed mode and then drag it to the LCD. I'm running off of Nvidia's drivers and I'm using a Logitech MX 610 mouse.

Any help would be much appreciated because this glitch is rather annoying!

---

### Post by Rae III on 2008-03-06
I figured out that the problem was the fact that my computer recognized that my crt as the main monitor. I found this out because if i put the window WoW was in on the crt, this problem did not occur. Also, if i ran it in maximized mode it would also not occur (although parts of the game would be outside the monitor). I installed envy and then ran the Nvidia settings control panel, which finally allowed me to make the lcd my main monitor, and now it works great. Only problem i have is WoW seems to think that its running at 3280x1200, but it looks fine to me so im going to just leave it be.

---

