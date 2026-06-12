---
title: "Constantly Running Up and Left"
date: 2012-06-04
forum: Wine
---

### Post by er00ic on 2012-06-04
I just bought Psychonauts through Steam and the game starts up fine, but I am unable to play it because the character keeps running up and left. I am running Ubuntu 11.04 with Wine version 1.4. I found an [old thread](http://ubuntuforums.org/archive/index.php/t-912522.html) about the issue and disabled visual effects, but it did not work. I also followed a link in the thread to [this,](http://ubuntuforums.org/showthread.php?t=613697) but have been unable to really figure out what it is I need to do. I use a two button wireless optical mouse. I also plugged in my two button wired optical mouse and had the same issue. I have a Mircrosoft Wired 600 keyboard. I'll give any other specs as requested.

Also, I'm going to want any instructions laid out in a step by step fashion, I don't have extensive knowledge of linux or computers in general.

---

### Post by zuti on 2012-06-04
Your Microsoft keyboard is probably being detected as a joystick, and it's borking up the input the game is receiving. 

If you don't have any actual joysticks/pads/etc, a quick fix you could try is disabling the joydev module. This can be done in the terminal by typing "sudo rmmod joydev". This will revert at every reboot, though (and if you have actual devices depending on this, don't do it:)

---

### Post by er00ic on 2012-06-04
> **zuti said:**
> Your Microsoft keyboard is probably being detected as a joystick, and it's borking up the input the game is receiving. 

If you don't have any actual joysticks/pads/etc, a quick fix you could try is disabling the joydev module. This can be done in the terminal by typing &quot;sudo rmmod joydev&quot;. This will revert at every reboot, though (and if you have actual devices depending on this, don't do it:)

That does seem to be the problem because your quick fix worked. Thank you very much for it. Do you or anybody else know how to convince my computer a keyboard is not a joystick?

---

