---
title: "FIX for WoW w/ Intel 965GM 4.1.3002 x86/MMX/SSE2"
date: 2008-11-15
forum: Wine
---

### Post by Zhiro on 2008-11-15
I thought I would post this because I had spent days trying to figure out how to run WoW with Wine on my Dell.  Computer specs:

Model: XPS M1330
OS: Ubuntu Hardy 8.04
Video: Intel(R) 965GM 4.1.3002 x86/MMX/SSE2

After spending days of getting hardlocked and rebooting and reinstalling WoW, I finally erased all my WoW files and did a clean install of it.  Here is what I came up with; what worked, what didn't, and how I fixed it.

Initially running WoW without messing around with anything, I could get through to the character log-in screen, but as soon as the world loaded, I couldn't move and the colors would get funky and my computer would hardlock.  Running in -openGL and adding
```
SET ffxGlow "0"
SET ffxDeath "0"
SET ffxSpecial "0"
```
to my WTF.config file, I was able to run the game in pre-BC/WotLK content only.  (Running BC content allowed me in game, but would crash after about 3 seconds and hardlock my computer.)

Then, I tried the same settings using d3d, but the game would just crash and hardlock even in pre-BC content upon entering the game.

I tried going into my winecfg file and allowing pixel shading, but wine wouldn't even open WoW after that, it would make the mouse cursor into a black square and hardlock.

**NOW, FOR THE FIX**
I changed the lines:
```
SET pixelshaders "1"
SET gxColorBits "24"
SET gxDepthBits "24"
```

to these lines:
```
SET pixelshaders "0"
SET gxColorBits "16"
SET gxDepthBits "16"
```

Everything worked perfectly fine!  I was even getting decent fps in Shattrath and crowded areas!  I hope this fix helps some of you out there, so you don't have to spend days trying to figure it out =)!

[I][B]
NOTE:[/B] After I logged out of WoW, my WTF.config file listed the ColorBits and DepthBits as this:[/I]
```
SET gxColorBits "24"
SET gxDepthBits "32"
```
*I don't know why it automatically changed these, but I logged back in and everything was just fine like before.*

***NOTE:** I have not yet tried this with the WotLK expansion.  This is running while only using the BC expansion.*

---

