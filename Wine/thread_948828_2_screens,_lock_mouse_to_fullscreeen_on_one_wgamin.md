---
title: "2 screens, lock mouse to fullscreeen on one w/gaming"
date: 2008-10-15
forum: Wine
---

### Post by Sceiron on 2008-10-15
Hi,
i have a dual screen set-up. Running as Separate X-screens at the moment.
I'm trying to find a solution to playing Warcraft 3 in fullscreen mode and at the same time arrange a shortcut to lock the cursor to that screen when i'm actually playing.

First i installed WC3 in wine and install "Mouse Jail" ref this link:
[http://gentoo-wiki.com/HOWTO_Dual_Monitors](http://gentoo-wiki.com/HOWTO_Dual_Monitors)
look in chapter 7,but i was not completely satysfied with this solution: if i make a sudden movement with the mouse, the pointer would not respond in warcraft when the mousepointer ended up approx 1 cm in the next screen.

Tried to install VMWARE, but VMWARE server does not support direct x, and i dont wanna use 200$ on VMWARE workstation (wich supports direct x i belive).

So im looking for some way to have Warcraft 3 running in fullscreen one one screen and the mouse is locked to this screen. But i wanna be able to unlock the mousepointer with some shorcut/hotkey so i can use the other screen when i.e. waiting for the game to start.
Is there someone who has a solution to this problem ?

Sceiron

---

### Post by Sceiron on 2008-10-24
Bump

---

### Post by Espryon on 2008-10-24
Try these links

1. [http://www.ubuntugeek.com/dual-monitors-with-nvidia.html](http://www.ubuntugeek.com/dual-monitors-with-nvidia.html)

2. [http://www.howtoforge.com/dual-monitor-setup-on-ubuntu7.10](http://www.howtoforge.com/dual-monitor-setup-on-ubuntu7.10)

3. and the search i found these on 

[http://www.google.com/search?hl=en&rlz=1G1GGLQ_ENUS298&q=how+to+set+up+dual+monitors+on+linux+xserver+under+ubuntu](http://www.google.com/search?hl=en&rlz=1G1GGLQ_ENUS298&q=how+to+set+up+dual+monitors+on+linux+xserver+under+ubuntu)

hope this helps

---

### Post by Sceiron on 2008-10-24
Well,
if i didnt miss anything, the problem is not setting up the dual monitors.

But lock the mouse cursor in warcraft 3 when i'm running wc3 in fullscreen mode of one of the screens....

---

### Post by Espryon on 2008-10-24
ill find a fix

---

### Post by Espryon on 2008-10-24
try this [http://appdb.winehq.org/objectManager.php?sClass=version&iId=3126](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3126)

there some fixes here

---

### Post by Sceiron on 2008-10-25
well,
some pointers there, but still not excatly what im looking for.
Using wine 1.1.7 and i have set the tick for "Allow DirectX apps to stop the mouse leaing their windows", but it doesn't  work. 

This is a very annoying problem...
I read somwhere that it works for some people, should I reinstall anything, maybe ubuntu ?

thnx

---

### Post by Sceiron on 2008-10-26
bump

---

### Post by Sceiron on 2008-11-09
Well,
i somehow got my hands on vmware workstation, but i did not give the result i was looking for. The game is working but...... the display drivers can't handle the processing apperantly. The latency is just to bad, or fps or, hm i dont really know...

So i'm back to trying to lock the mouse in one fullscreen with wine.
Also posted a thread on the warcraft forum on wine, but no respons so far.

EDIT: This is another BUMP!
EDIT II: I have read about running apps in another Xserver, is there somhow possible that this is the way to go ?? 
Or am I totally lost direction here ?

---

### Post by Sceiron on 2008-11-10
If anyone is still watching this thread....
I think i have found the solution in this thread:
[http://ubuntuforums.org/showthread.php?t=634067&highlight=Wine+apps+X-server](http://ubuntuforums.org/showthread.php?t=634067&highlight=Wine+apps+X-server)
    -the second post

but for a "mortal" user as me there is some basic things i need help to straighten out:

1. ```
#!/bin/sh
#uncomment if launching from console session
#sudo /etc/init.d/gdm stop
#KDE use this instead
#sudo /etc/init.d/kdm stop
```
Console - does that mean GUI terminal or do I need to switch to run level 3 or what is is ??

2. Can i start a new X-session "inside" an existing X-session (run it from GUI terminal iow) ?

3.> Just use a launch script to launch the game in a seperate X server
Launch script, what is that. Do i make a script executable and the create a launcher on my desktop ??

There are more things that are unclear on this subject for me, but an answer to this questions would be a nice start.
I just wanna play wc3 :)

Best Regards
Sceiron - :confused:

---

