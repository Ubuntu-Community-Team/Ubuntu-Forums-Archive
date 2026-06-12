---
title: "[Help] Portal"
date: 2008-06-17
forum: Wine
---

### Post by Viter on 2008-06-17
Hi guys i have a problem :-)

If you guys knows the game : portal
I got extremely low FPS it laggs all the time. on lowest graphics. and on windows i could play it on the best without any lagg (Yes im opening it from WINE)

And my other question is this:
And why do i have no crosshair ? it's just black.
And i can't see the text ingame :S

---

### Post by cogadh on 2008-06-17
Portal needs to be run in DirectX 8 mode. Launch it like this from a terminal:
```
cd ~/.wine/drive_c/Program\ Files/Steam
wine steam.exe -applaunch 400 -dxlevel 80
```
If the FPS performance is acceptable, then add the "-dxlevel 80" to the game's launch options in Steam.

The crosshair issue may go away with the dxlevel change (I can't remember for sure). The text issue, I'm not sure about, but when you run the game from the terminal, it will produce error output in the terminal that may explain what is going on. If the text (or crosshair) problem still occurs, post the terminal output here and we'll see if there are any clues in it.

---

### Post by Viter on 2008-06-17
> **cogadh said:**
> Portal needs to be run in DirectX 8 mode. Launch it like this from a terminal:
```
cd ~/.wine/drive_c/Program\ Files/Steam
wine steam.exe -applaunch 400 -dxlevel 80
```
If the FPS performance is acceptable, then add the "-dxlevel 80" to the game's launch options in Steam.

The crosshair issue may go away with the dxlevel change (I can't remember for sure). The text issue, I'm not sure about, but when you run the game from the terminal, it will produce error output in the terminal that may explain what is going on. If the text (or crosshair) problem still occurs, post the terminal output here and we'll see if there are any clues in it.
Thanks! :D it worked ^^
But i have some ugly portals (no problem there)
Now the problem is:
When i completed level 10 it says: SV_cheats = 1 and then sv_cheats = 0
and then it closes.
And the crosshair and the text thing worked btw :)


And last question :)
What's the app number fot Teamfortress 2?

---

### Post by cogadh on 2008-06-17
It sounds like you are running "Portal: First Slice" which is only a level limited demo. That's just the way it ends.

Here's a full list of Steam application ID numbers:
[http://developer.valvesoftware.com/wiki/Steam_Application_IDs](http://developer.valvesoftware.com/wiki/Steam_Application_IDs)

---

### Post by YokoZar on 2008-06-18
> **Viter said:**
> Thanks! :D it worked ^^
But i have some ugly portals (no problem there)
Now the problem is:
When i completed level 10 it says: SV_cheats = 1 and then sv_cheats = 0
and then it closes.
And the crosshair and the text thing worked btw :)

I've ran into this problem before too.  It's actually a portal bug and not a Wine problem.  I forget what I did to fix it, but it involved something from within the game after some googling.

---

### Post by Viter on 2008-06-18
Well im sure i'm running the real game ;)
I completed it on Windows :)

---

### Post by DoorKnob5001 on 2008-07-01
Sorry for bringing up an older topic, but I need help.

Hi, I'm not really new to Ubuntu but I still have lots to learn.  Right now, my problem is that, like this gentleman's problem above, I have no crosshair or text while playing Portal: The First Slice.  Normally, since it's a demo, I wouldn't care BUT the same problem is in Garry's Mod, which I just bought.  I've tried the command that was said earlier but to no luck, but it has added a new error saying that I need a source engine now.(I have CS:S and TF2) When I open Steam without the command, I can play the game but it sometimes crashes after getting hit by something, still no text or HUD, it's all black boxes.

Your help will be very appreciated. Thanks in advance.

---

### Post by DoorKnob5001 on 2008-07-01
Sorry for double post.  But I just tried TF2 for the first time, and say problem. (Tried it without the command above) The HUD and in-game text is all black boxes.  The menu, loading screen and character selection screens are all perfect.

---

