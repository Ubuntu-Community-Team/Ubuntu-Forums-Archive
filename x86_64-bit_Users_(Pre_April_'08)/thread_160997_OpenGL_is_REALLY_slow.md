---
title: "OpenGL is REALLY slow"
date: 2006-04-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by 3rdalbum on 2006-04-16
I'm using Breezy on an old iMac 333MHz, which has the standard ATI Rage 3D accelerator in it.

I've noticed that OpenGL runs very, very, VERY slowly. The glxgears program comes in at about 1 frame per 7 seconds. SuperTux is playable without OpenFL, but much slower and jerkier with it. Other games are even worse.

Is there anything that might be causing this behaviour, or do I need to install more software to get OpenGL to run properly? I'm just using the default open-source ATI driver.

EDIT: I went into my xorg.conf file and commented out the DRI section and the load DRI line, and restarted the xserver. Now, when I start glxgears, the animation goes at a good speed for about a second, then drops back to 1 frame per 4 seconds.

---

### Post by Jason_25 on 2006-04-16
Were you able to get acceptable opengl performance in macos?  I have the pc equivalent in a server and it's a horrible card.  Also, i'm virtually certain that the closed source ati drivers don't support it.  They don't even fully support the newer cards.

---

### Post by 3rdalbum on 2006-04-17
[QUOTE=Jason_25]Were you able to get acceptable opengl performance in macos?  I have the pc equivalent in a server and it's a horrible card.  Also, i'm virtually certain that the closed source ati drivers don't support it.  They don't even fully support the newer cards.[/QUOTE]

Oh yes, Open GL works fine on the Mac side (glTron for Mac is very smooth and fast). You're right in saying that the closed-source ATI drivers don't support the card - it's way too old. I heard that the open-source drivers do support some 3D acceleration on older cards, but maybe they're a bit buggy.

What intrigues me is that glxgears goes fine for the first second, then slows to 1 frame per 4 seconds.

I'm going to get a PC in a month and a bit anyway, so I suppose if nobody knows what's wrong it doesn't really matter. Does anyone else have the same problems with similar Macs?

---

### Post by dpny on 2006-04-17
When I first installed Ubuntu on my Pismo, direct rendering and double buffering were not turned on, which meant that the video was slow. I had to include the line ```
Load "dbe"
``` in my xorg.conf file under the "Module" section and refer to [this]() link to get Ubuntu to support direct rendering. I chose the option of including the kernel drivers and setting the color depths to 16 bits.

---

### Post by 3rdalbum on 2006-04-17
[QUOTE=dpny]When I first installed Ubuntu on my Pismo, direct rendering and double buffering were not turned on, which meant that the video was slow. I had to include the line ```
Load "dbe"
``` in my xorg.conf file under the "Module" section and refer to [this]() link to get Ubuntu to support direct rendering. I chose the option of including the kernel drivers and setting the color depths to 16 bits.[/QUOTE]

Thanks, but the link doesn't go anywhere :)  I'm adding the line in anyway and seeing what that does in anticipation of you fixing the link. Should I enable DRI again then? (disabling it didn't make a difference anyway)

---

### Post by dpny on 2006-04-17
[QUOTE=3rdalbum]Thanks, but the link doesn't go anywhere :)  I'm adding the line in anyway and seeing what that does in anticipation of you fixing the link. Should I enable DRI again then? (disabling it didn't make a difference anyway)[/QUOTE]

Sorry about the dead link. Will fix tonight at home.

---

### Post by dpny on 2006-04-17
[QUOTE=3rdalbum]Thanks, but the link doesn't go anywhere :)  I'm adding the line in anyway and seeing what that does in anticipation of you fixing the link. Should I enable DRI again then? (disabling it didn't make a difference anyway)[/QUOTE]

[http://ubuntuforums.org/archive/index.php/t-3723.html](http://ubuntuforums.org/archive/index.php/t-3723.html)

---

### Post by 3rdalbum on 2006-04-18
Thanks for the link. I made the changes suggested in the first post of that thread, and when I've finished surfing I'll restart X.

---

