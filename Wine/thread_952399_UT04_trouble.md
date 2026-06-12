---
title: "UT04 trouble"
date: 2008-10-19
forum: Wine
---

### Post by Spekke on 2008-10-19
Heya

I installed UT04 through wine 1.1.4 (and steam because I bought it on steam)

now if I try to play the game then it's like I am controlling the mouse in the ut screen 
and the one on my background, 
it's also like the ut screen is smaller while it is the same size as my screen resolution 
but when the mouse on the background for example goes to much down, then the one in the ut screen is stuck on a certain hight... 
a very odd and irritating problem since most of the times I can't look left, up, down, right (depending on where the mouse on my background is)

I have tried playing windowed, playing smaller resolutions, but none worked

the solution on WineappdB: "Edit your UT2004.ini file and scroll down until you find something about a viewport. These control your menu, windowed, and fullscreen resolutions, each in different sections. Edit each of these to reflect your desktop resolution, and save it. Restart the game and you should be all set.

 NOTE: It likes to switch to windowed mode and change to a strange resolution, with a warning about it not being supported by your monitor. if this occurs, click ok to dismiss the warning, and continue normally. It should not adversely affect gameplay."

only... I don't understand what they mean, they say: "edit each of these...." but edit to what?

greetings

---

### Post by lavinog on 2008-12-20
Have you tried installing the linux version of ut2004?
I don't know how the steam version works, but my ut2004 cd came with a linux installer.

---

### Post by epitaph on 2008-12-21
UT2004 runs natively under linux very well. I would opt for that over the current solution.

But, to explain:

```

[WinDrv.WindowsClient]
WindowedViewportX=1024
WindowedViewportY=768
FullscreenViewportX=800
FullscreenViewportY=600
MenuViewportX=640
MenuViewportY=480

[SDLDrv.SDLClient]
WindowedViewportX=1024
WindowedViewportY=768
FullscreenViewportX=800
FullscreenViewportY=600
MenuViewportX=640
MenuViewportY=480

```

Are the valid parts of the UT2004.ini found in the /System folder under your UT2004 install. I'm not sure where you would find this since you installed it with Steam under WINE.

```
locate UT2004.ini
```

Should tell you where it is, though.

---

