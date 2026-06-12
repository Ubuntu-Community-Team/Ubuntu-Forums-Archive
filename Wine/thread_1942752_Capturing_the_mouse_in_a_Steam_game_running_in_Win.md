---
title: "Capturing the mouse in a Steam game running in Wine"
date: 2012-03-18
forum: Wine
---

### Post by ZICODIAN on 2012-03-18
Hi *

I'm running Mass Effect with Steam using Wine in Ubuntu 11.04. I'm having difficulty with mouse capture.

Essentially, the game will run and the keyboard is captured while the mouse is not (though it was captured a few intermittent times). Would anyone have any tips on how I might approach this problem? I've tried a few winecfg options (DirectX mouse capture, virtual desktop etc.) to no avail.

Preemptive thanks

---

### Post by vhaarr on 2012-03-24
I am having mouse capture problems as well, with the game Dungeon Defenders running in Steam with xserver-xorg-core 2:1.11.4-0ubuntu7 and xserver-xorg-input-evdev 1:2.7.0-0ubuntu1.

I think it might be related to XInput2 not being properly supported under WINE, but I am not certain.

---

### Post by aveplatter on 2012-05-04
anyone figure this out yet? it's driving me crazy

---

### Post by forrestcupp on 2012-05-05
Go into the winecfg, and click on the "Graphics" tab. Check the box that says "Automatically capture the mouse in full screen windows". If it still doesn't work, try clicking the box that says "Emulate a virtual desktop". That isn't the best choice, though because it will all be put into an Ubuntu Window. Hopefully the first choice just works for you.

---

