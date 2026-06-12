---
title: "WoW crashes during the game"
date: 2008-07-12
forum: Wine
---

### Post by louis3234 on 2008-07-12
Hi guys. I just installed WoW using cedega 6.0. But when I try to run the game, after the 2 laggy intros, it crashes and send this error message:```
This application has encountered a critical error:

ERROR #132 (0x85100084) Fatal Exception
Program:	D:\.cedega\WoW\c_drive\Program Files\World of Warcraft\WoW.exe
Exception:	0xC0000005 (ACCESS_VIOLATION) at 0073:40E9E0FE

The instruction at "0x40E9E0FE" referenced memory at "0x00000014".
The memory could not be "written".


WoWBuild: 6080
```
By the way, the mouse is working normally like they are under Windows.
Any idea how to fix the crash?

---

### Post by NovruzeliH on 2008-07-12
i guess u wont be able to run WoW on linux cuz WoW is not meant to be played on linux, and about that error, it shows that ACCES_VIOLATIONS obv... meaning it cannot acces that area because there is no such file when u install WoW , click Browse, and install it to yourdesktop into a folder called WoW then launch it through there, and about the lag, its lags, because linux is not used to the WoW specs

---

### Post by louis3234 on 2008-07-12
I forgot 2 points, when i finished installing WoW, the WoW installer says:```
Unable to create an entry in the Add/Remove Programs Control Panel for "World of Warcraft."
```
because i use terminal to launch the installer.exe with cedega, terminal warning me as:```
File r300_render.c function r300Fallback line 469
Software fallback:ctx->Multisample.Enabled
wine: Unhandled exception, starting debugger...
```Then when i launch the game, it crashed with same reason.

---

### Post by NovruzeliH on 2008-07-12
i guess dont install the thing man, u might ruin your OS, WoW isnt that fun anyways let me find a good game :p that i play when i have time, i'll tell u it :p

---

### Post by louis3234 on 2008-07-12
Great..But I still want to try it. More ideas?

---

### Post by NovruzeliH on 2008-07-12
sure well here is one thing did u install that wow through cedega right ??? might be a cedega problem sometimes happenes u know, i'd tell u give it another shot with wine, that might help it out, but hmm not sure man, its up 2 u :( i helped all i could, and also about that add/remove program thing, i was just wondering are u the root user ???? of the ubuntu u got there or no ?? and what version of ubuntu are u using

---

### Post by louis3234 on 2008-07-12
I'm using Ubuntu 7.10 and i'm not the root but i can change to it. Well it doesn't matter now. Cause after i read the Configuration of this page:[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)
I'm able to fix the crash. But the game is UNBEARABLY slow, including the mouse and graphics. But the music works normally. When I launch it from terminal, I think I saw the same error message before:```
File r300_render.c function r300Fallback line 469
Software fallback:ctx->Multisample.Enabled
wine: Unhandled exception, starting debugger...
```
I gotta find a way to fix this.

---

### Post by NovruzeliH on 2008-07-12
multisample eabled might mean, its been opened twice or something o.O not sure, but yeah try restarting and launching it, and yeah WoW will lag on linux :p

---

### Post by louis3234 on 2008-07-12
I tried to run WoW.exe with wine in DirectX mode, which is:```
wine WoW.exe -d3d
```but it only fixed mouse, the graphics still run 1 frame in 10 seconds.

---

### Post by NovruzeliH on 2008-07-12
uh louis here is a little suggestion buddy, why dont u just install Virtual Box -.- and install WoW on xp and then play it cuz thats how i play the games now -.- :D

---

### Post by louis3234 on 2008-07-12
Ehh...Sure, I'll try that later

---

### Post by penguin master on 2008-07-12
how bout open arena or alien arena or quake wars or some other fps:)

---

### Post by NovruzeliH on 2008-07-13
wow penguin master that was a usless post, we're talking about wow here, not an FPS (first person shooter) -.- next time ready plz bud

---

### Post by Chromo on 2008-07-13
guys what happened to the Vortex wow server ?????

---

### Post by Vitamin-Carrot on 2008-07-13
I thought VB had no 3d support

---

### Post by NovruzeliH on 2008-07-13
actually there is some  3D supports man, because we're human and we deserver to play 2 even tho its linux :(, u amde me cry,, 

UHH THIS WAS TOTTALY USLESS POSt

---

### Post by Chromo on 2008-07-15
um yeah so does eny1 know what happened or can some1 just help me if sumin changed pls

---

