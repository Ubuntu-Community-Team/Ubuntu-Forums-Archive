---
title: "CNC3 Shadow Support? Unreal 2K4 Question?"
date: 2007-11-30
forum: Wine
---

### Post by GSF1200S on 2007-11-30
Finally, Ive got around to installing Command and Conquer 3 under wine, and after a few tweaks.. im impressed! It runs better under wine than it did on XP!! I did notice, however, that I dont have any shadows projecting from buildings or units. I dont think I even saw them when I installed it on Windows, so im not sure what the deal is. Do you CNC3 people have shadows within the game? I turned Shadows to Ultra High and still nothing...

Also, is there any way I can minimize CNC3 while playing? I can do it if I emulate a virtual desktop, but the game looks so much better running fullscreen. Its a pain because if I need to do something on the desktop or anything, I have to exit the game. Actually, since ill be installing 2 other games under wine, is there any way to make wine minimize games running fullscreen?

A final question: will Unreal Tournament run on 64bit 'Buntu (the native linux binary I mean)? Im pretty sure it would install 32bit if nothing else, but id like to make sure before I buy it...

Once Diablo 2 LOD and Counter Strike Condition Zero are installed under wine, im wiping my Windows partition and giving it all to Linux. Ill be all-Linux for the first time ever (well, except for a VM)!

---

### Post by cogadh on 2007-12-01
Regarding the shadows thing, there are a couple of Windows DLLs required for the game to run fully (d3dx9_29.dll and gdiplus.dll), so if you don't have those added to your Wine directory, you may not get full performance out of the game. I don't have CNC3, so I can't confirm this myself.

Generally speaking, you can't directly minimize full screen games, especially those run through Wine (Windows games like to claim the whole desktop). You might be able to ALT-TAB out of the game to a different running app, which will effectively minimize it, but that has always caused problems for me when I have tried it.

I'll leave a definitive answer to the UT question for someone who knows better, but it might be possible to run it in 64-bit if you have the 32-bit support libraries installed already.

---

