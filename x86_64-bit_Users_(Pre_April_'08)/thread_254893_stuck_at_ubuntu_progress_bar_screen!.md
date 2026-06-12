---
title: "stuck at ubuntu progress bar screen!"
date: 2006-09-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by arkon123 on 2006-09-10
I pop in my live CD, restart my comp, and start up the menu screen. I select the first choice which is "Start or Install Ubuntu".
Everything seems to go ok, decompressing liux, booting kernel, and loads bunch of things.
Then it gets me to this black screen with ubuntu logo on it and has a little bar under. From what i know, it's a progress bar, but mine's just frozen there. I've waited about 30 min, still nothing.

I'm using AMD64 X2 3800+, ATI Radeo X1800GTO

Could anyway explain why this is happening? Thank you

---

### Post by kopilo on 2006-09-12
Try the graphical safe option, I'm not sure of the exact name but it is something along those lines.

Also if you are trying to install Ubuntu, the alternative version may actually work better.

I couldn't tell you what is happening but it does seem a lot of people are having troubles with the live discs.

---

### Post by arunesh on 2006-09-12
Hi.. 

I'm running a:
Compaq Pressario v3000
amd64 turion X2

Installation went fine. Had the same problem when i was tweaking with "xorg" on kubuntu 6.06.1 64 bit. I tried the graphical safe option and it gave me a command line. (i'm not sure whether its always the case.)
Then i ran:

sudo dpkg-reconfigure xserver-xorg

And fill in the rest instinctively.
I have an LCD and "vesa" driver seems to work for that.
If u have a monitor, select accordingly.

I'm guessing that u might have a problem with video driver detection, but i can't really be sure. It could possible be a totally different problem. I,m not really an expert, so do check around before trying the above...

All the best

---

