---
title: "[SOLVED] WoW FPS issues"
date: 2008-08-18
forum: Wine
---

### Post by jamesxross on 2008-08-18
i've tried everything in the [ubuntu walk through]("https://help.ubuntu.com/community/WorldofWarcraft") for installing WoW, as well as the [wow-wiki walk through]("http://www.wowwiki.com/Linux/Wine") and i still have one major problem: i can't seem to get over 10 fps. when i run WoW in windows, i get up to 40 fps in the lower-population/less graphics intensive areas, dipping down to about 15 in shattrath city at peak hours. i've tried the registry tweak, grabbing the .dll files from my windows installation, everything i could find. still no joy :( this is the only thing keeping me on windows, and i'd like to be free of it. halp pls!

i've got 1gb ram, 1.66 GHz processor (this is a 2 year old dell inspiron 6400, let me know if you need any more specs)

---

### Post by Eviljim on 2008-08-19
What graphic card type, and model do you have? Also what driver version are you using for the card?

---

### Post by shazzed on 2008-08-19
Shattrah is aweful for fps even in windows on some rigs.
I drop my view distance down, to about half way and it helps alot!

dell inspiron 6400
I gather this is a laptop ?
If you want to game you need a decent laptop made for gaming or a cheaper tower.

---

### Post by jamesxross on 2008-09-10
sorry! i was away from the internet for a while. yes, it's a laptop. it's got the Mobile Intel(R) 945GM Express Chipset Family (integrated graphics), using driver version 6.14.10.4814.

also, i know that it's not an optimal gaming computer, but i got it as a graduation present from high school (in 06') and i'm gonna be getting a new one when i graduate from college (another 2-3 years). being a poor college student, i'm having to make due with what i've got, and (as i'm sure you know) linux is much more friendly in terms of resource usage.

---

### Post by hikaricore on 2008-09-10
For a good to excellent WoW experience on linux you're going to need atleast an Nvidia GeForce6xxx and above OR a linux friendly ATI card.
The intel chipset has laughable OpenGL support and terrible Linux drivers (thank Intel for that).

You can pick up a half decent video card for around 50 bucks.
Go for PCIe (best) or AGP (good) depending on what your system supports, standard PCI does an awful job with video throughput.

---

### Post by jamesxross on 2008-09-11
it's a laptop, though, and the gpu is integrated into the motherboard.

---

### Post by darkknight045 on 2008-09-11
Have you tried running in direct3D, I've heard that Intel cards sometimes support d3d far better than opengl


try the following:

```
wine "C:\Program Files\World of Warcraft\WoW.exe" -d3d
```

If your path is different just adjust accordingly.

---

### Post by hikaricore on 2008-09-11
WINE doesn't actually use directx.  It converts it to OpenGL.
Most of the time (some exceptions to this) running in d3d mode will actually make it worse.

---

### Post by darkknight045 on 2008-09-12
I'm aware of the typical incompatibility.  From what I have read, in these forums, this is an exception with _some_ Intel cards.

---

### Post by bhart007 on 2008-09-12
Dude this is far from an incompatibility.. on-board Intel whatever model it is will always suck.  I'd be surprised if your laptop doesn't lock-up while riding a Gryphon from flight paths.

It's probab,y safe to say that no amount of tweaking will get the framerates that your wanting.  You just dont have the hardware.. and I wouldn't be holding your breath for Wine, or the Linux community to spend any time improving the drivers for such hardware.

Not to be a killjoy here but the bottom line is.. if you wanna game, next time ask for or invest in a real laptop.

---

### Post by Caedis on 2008-09-12
I happen to have a Intel 945GM and do run Hearty on it with WoW. Suffice to say, me and my fiancée are saving for System76 laptops. 

You MUST run WoW in Direct3D mode, no way around it, period, give up all hope of OpenGL. Intel screwed you and I and decided that they weren’t going to support OpenGL directly. I have a config.wtf that I use on 945GM linux systems. I can’t guarantee you’ll get much more than 10-15 FPS out of WoW, even with this wtf. But that’s just how it is on this chipset.

Sorry I cant be of more help. Below is the WTF I use.

System76: [http://www.system76.com](http://www.system76.com)

Leave out the "SET gxApi" line as WoW defaults to D3D when none is specified. And even if you specify it, wow deletes the line when the game is run since it’s a useless line when all you wanna do is run d3D
```

SET SoundOutputSystem "1" 
SET SoundBufferSize "232" 
SET ffxDeath "0" 
SET gxMultisampleQuality "0.000000" 
SET gxFixLag "0" 
SET fullAlpha "1" 
SET lodDist "100.000000" 
SET SmallCull "0.070000" 
SET DistCull "500.000000" 
SET farclip "477" 
SET particleDensity "1.000000" 
SET unitDrawDist "300.000000" 
SET gxCursor "0" 
SET baseMip "1" 
SET spellEffectLevel "0" 
SET weatherDensity "0" 
SET pixelShaders "0" 
SET ffxGlow "0"

```

---

### Post by hikaricore on 2008-09-12
-

---

