---
title: "Random System Crashes, Any Suggestions?"
date: 2008-10-08
forum: x86 64-bit Users
---

### Post by Lee05162004 on 2008-10-08
Hi, I have Ubuntu 8.04, 64 bit edition installed and my computer is randomly crashing. Mostly what happens is I'll be just using it and all of a sudden the screen flashes and then it goes blank. About the only thing that I am always doing when it seems to occur is minimizing windows. I'm not sure what all information you'll need to help me diagnose the problem. But again, I'm using the 64 bit version of Ubuntu 8.04. I have an ATI Radion Express 200m graphics card installed and I'm using the gnome desktop environment. The most common programs I am running when this occurs are Firefox, Pidgin, Banshee and a couple screenlets. Let me know if you need anymore info. Thanks

---

### Post by nordrasor on 2008-10-08
What "Desktop Effects" do you have enabled? Latest ATI drivers? Any extra window managers/docks? Are you able to restart Gnome with CTRL+ALT+Backspace?

---

### Post by saru411 on 2008-10-09
What do you mean crashes? Does it power down? restart? screen lock? If the screen locks what happens when you hit cntrl+alt+f2?

---

### Post by Lee05162004 on 2008-10-09
> **nordrasor said:**
> What "Desktop Effects" do you have enabled? Latest ATI drivers? Any extra window managers/docks? Are you able to restart Gnome with CTRL+ALT+Backspace?

I have compiz enabled with some advanced desktop effects. I do have the latest ATI drivers and I'm also using AWN. No, I'm not able to restart gnome either. The screen simply goes black.

---

### Post by Lee05162004 on 2008-10-09
> **saru411 said:**
> What do you mean crashes? Does it power down? restart? screen lock? If the screen locks what happens when you hit cntrl+alt+f2?
 
The screen flashes lines and then goes black. Nothing happends when I hit ctrl+alt+f2.

---

### Post by Jouke74 on 2008-10-09
With random crashes, the first thing you need to do is test your memory. Start up using Grub and select option 3 "Memtest". Then let it run for about an hour (preferably longer) and see if none of the tests fail. If it crashes during this test, or indicates errors (in red) you should check your memory.

I don't think memory will be the problem however, just to make sure that it isn't. Seems to me like your video driver is crashing on something. Try to disable the desktop effects for a while, without screenlets, awn etc. and see how that works out. If there are no crashes, turn them on one by one and see where the problems start. Also check if your cpu / videocard are not getting too hot.

---

### Post by dabl on 2008-10-09
If the keyboard isn't totally "disconnected" by the display crash, then you'd be well advised to use the "magic sysrq" technique to shut it down:

While holding Ctrl-Alt-SysRq keys down, press in sequence, R  S  E  I  U  B


It's easier on your filesystem than pushing the reset button.

:)

---

### Post by Lee05162004 on 2008-10-12
> **Jouke74 said:**
> With random crashes, the first thing you need to do is test your memory. Start up using Grub and select option 3 "Memtest". Then let it run for about an hour (preferably longer) and see if none of the tests fail. If it crashes during this test, or indicates errors (in red) you should check your memory.

I don't think memory will be the problem however, just to make sure that it isn't. Seems to me like your video driver is crashing on something. Try to disable the desktop effects for a while, without screenlets, awn etc. and see how that works out. If there are no crashes, turn them on one by one and see where the problems start. Also check if your cpu / videocard are not getting too hot.

I tested the memory and I let it run for awhile and all the tests passed.

---

### Post by Lee05162004 on 2008-10-12
> **dabl said:**
> If the keyboard isn't totally "disconnected" by the display crash, then you'd be well advised to use the "magic sysrq" technique to shut it down:

While holding Ctrl-Alt-SysRq keys down, press in sequence, R  S  E  I  U  B


It's easier on your filesystem than pushing the reset button.

:)

I will try this if it happens but so far it has not done it again. All I have done so far is disable the screenlets app and I have not had the problem since.

---

