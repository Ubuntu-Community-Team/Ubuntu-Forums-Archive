---
title: "Left 4 Dead Demo (Slowness Abound for Linux users)"
date: 2008-11-06
forum: Wine
---

### Post by sixstorm on 2008-11-06
For those of you who ordered the game early, you get early access to the demo!  But I'm already having performance issues with this game.

Specs:
1.4GHz Core 2 Duo
NVIDIA 8400GS M 128MB
2GB RAM

CS:S works decent, around 40-50FPS but I know that it can do better (in Windows at least).  So how can we improve the performance in Source games for my laptop?

I've tried both NVIDIA 173 and 177 drivers, both give the same performance on CS:S and L4D demo.  I've tried using the "dxlevel 81" under launch options, but that doesn't really help.  All the graphics settings and resolution are set to the lowest possible settings.  Finally, I've turned Compiz-Fusion completely off and still get the same results.

Any more hints, tips or clues?

---

### Post by mbezik on 2008-11-07
same problems here with a 2.7 core 2 duo with 4gig of ram and a gtx260 - barely playable in a 800x600 window with everything set on its lowest settings....

---

### Post by Brynster on 2008-11-07
Ok L4D low frame rates i cannot help you with as i don't have it installed sorry.

However i find setting the screen resolution in CS to 1024x768 improved my frame rates hugely, cannot explain or give a reason for it it just seemed to work.

I have a AMD Athlon x2 64 6000 2gig ram and an Nvidia 8800gts OC and get around 100 to 150 fps constantly. Thats running in dxlevel -81 and low settings. If i run at full image settings then i get around 75-80fps. It makes no real difference if disable compiz or not.


I if i get chance install the L4D demo and play around see what the results are.

---

### Post by sixstorm on 2008-11-07
I really wish games worked better on Linux . . . I guess we'll have to wait a few months for L4D to work.

---

### Post by Dizzle7677 on 2008-11-07
> **sixstorm said:**
> For those of you who ordered the game early, you get early access to the demo!  But I'm already having performance issues with this game.

Try setting GLSL to disabled in the registry under HKCU->Software->Wine->Direct3D. I don't think L4D supports dxlevel 80 & 81 so it may not work.

---

### Post by kroenecker on 2008-11-10
sixstorm,

So did you get it to run pretty well on wine?

---

### Post by captaincrook on 2008-11-11
Wine needs to have UseGLSL enabled to be able to see/use the title screen cause of the shaders it uses. I dunno the command to start a single player game from console (if any), and using DXLevels of 80 & 81 showed no increase in performance. It stays locked in around 10-15 frames at all times mostly. Perhaps if there's a way to start the game via console we could see if it runs better/at all without GLSL.

---

### Post by Dizzle7677 on 2008-11-11
> **captaincrook said:**
> Wine needs to have UseGLSL enabled to be able to see/use the title screen cause of the shaders it uses. It stays locked in around 10-15 frames at all times mostly. Perhaps if there's a way to start the game via console we could see if it runs better/at all without GLSL.

Do you mean ...

 wine Steam.exe -applaunch 530 (add a "changelevel/changelevel2" here or start new game(?))

Well at least yours runs. Mine locks/hangs (in the typical Source way of skipping) at starting a new game. Bug report filed.

Or if you want to get haxxor-y and have HL2:EP2 around you could copy over the ep2shaders to the l4d demo\hl2\shaders directory or something of that nature. Haven't tried it myself....yet.

---

### Post by captaincrook on 2008-11-11
> **Dizzle7677 said:**
> Do you mean ...

 wine Steam.exe -applaunch 530 (add a "changelevel/changelevel2" here or start new game(?))

Well I'm not familiar with the all the commands in Valve games, but if you can start games using those launch options, it'd be possible to check to check if it runs better with or without GLSL. I doubt it will work, considering the lobby style way to start the game.

> Or if you want to get haxxor-y and have HL2:EP2 around you could copy over the ep2shaders to the l4d demo\hl2\shaders directory or something of that nature. Haven't tried it myself....yet.

Yeah thats a little too far, haha. Sounds like it won't work. But if it works for other games it should be possible eh?

Anyways, the demo was only released today. Give it some time to circulate and there will be a bunch of new commands to toy with and maybe we can get this working good as quickly as Spore. Something keeps the game locked in at my frame speed. I wonder if its some of the new things Valve added to the engine that needs disabling.

EDIT: I also have Crossover Games (lucky check when it was Lame Duck Day :P) and will test on that.

---

### Post by Dizzle7677 on 2008-11-11
> **captaincrook said:**
> Well I'm not familiar with the all the commands in Valve games, but if you can start games using those launch options, it'd be possible to check to check if it runs better with or without GLSL. I doubt it will work, considering the lobby style way to start the game.

  No go. Just a big black screen.


> **captaincrook said:**
>  Yeah thats a little too far, haha. Sounds like it won't work. But if it works for other games it should be possible eh?

Anyways, the demo was only released today. Give it some time to circulate and there will be a bunch of new commands to toy with and maybe we can get this working good as quickly as Spore. Something keeps the game locked in at my frame speed. I wonder if its some of the new things Valve added to the engine that needs disabling.

  You could go into the \hl2\shaders\fxc[?] directory and make the extensions to .old for motion_blur,ssao,etc. But it would just mean they won't load and would produce another error output. It's worth experimenting with though to see what is what.

  The most direct way is to file a bug report @ [http://bugs.winehq.org]("http://bugs.winehq.org"), with the console error/fixme/problems output, to get the developers attention. If enough people do then something good might happen with the next build or wine 1.2. [#15946 ]("http://bugs.winehq.org/show_bug.cgi?id=15946")

  Another concern is that this new Source engine build will also power HL2:Episode 3. It's better to help nip these bugs/problems early.

---

### Post by Phil Urich on 2008-11-12
Things like this are why we really need to pressure developers to outright support Linux instead of relying on Wine.  Definitely Wine does some stellar work, but especially for things like games, if they can be made to work so well with Wine then likely they could have been made to work natively without more effort than it would be worth, even just speaking monetarily (hell, the fact alone that the majority of games have Linux dedicated servers shows that everything but the graphics themselves tends to be *already* ported to Linux).

---

### Post by Brynster on 2008-11-12
Wine 1.18 has better GLSL support according to [http://www.winehq.org/?announce=1.1.8](http://www.winehq.org/?announce=1.1.8)

I installed it yesterday and will fiddle tonight :-)

---

### Post by stuart.crouch on 2008-11-12
for those wondering how the hell they managed to install l4d demo considering how wine doesnt play well with steam.

```

cd ~/.wine/drive_c/Program\ Files/Steam
wine Steam.exe -applaunch 530

```

(530 = the code for l4d demo, as can be found by looking at the steampowered website)

---

### Post by kroenecker on 2008-11-12
Everything works for me.

Core 2 Duo E7200
3 gigs ram
nVidia Corporation GeForce 8600 GTS

Runs ok in Hardy using the wine repository.

The download and install of the demo through steam went fine.  When I tried to play I got a black screen.  Using winecfg I checked "Allow Pixel Shaders" (under Graphics) and it works.  I've played several games.  In order to get it playable though you have to turn down all of the graphical settings in the game itself.

Heres what I use on the command line to start it up:

env WINEDEBUG="fixme-all" WINEPREFIX="/home/<USERNAME>/.wine" wine "C:\Program Files\Steam\steam.exe" -applaunch 530 -heapsize 512000 -novid

Change the WINEPREFIX to your home directory.

So if you have similar hardware you should be able to play!

---

### Post by Brynster on 2008-11-13
runs ok for me but does get sluggish when multiple zombies appear on screen

AMD athlon x2 64 6000
2 GB ram 
Nvidia 8800gts.

I might try the pixel shaders option to see if that improves it for me a little

---

### Post by captaincrook on 2008-11-13
I guess heapsize helped. I also changed my resolution to 640*480. It can get as high as 30 frames when nothing is on screen. Still, hovers usually between 10-20 frames now.

---

### Post by cactuar32 on 2008-11-13
> **kroenecker said:**
> Everything works for me.

Core 2 Duo E7200
3 gigs ram
nVidia Corporation GeForce 8600 GTS

Runs ok in Hardy using the wine repository.

The download and install of the demo through steam went fine.  When I tried to play I got a black screen.  Using winecfg I checked "Allow Pixel Shaders" (under Graphics) and it works.  I've played several games.  In order to get it playable though you have to turn down all of the graphical settings in the game itself.

Heres what I use on the command line to start it up:

env WINEDEBUG="fixme-all" WINEPREFIX="/home/<USERNAME>/.wine" wine "C:\Program Files\Steam\steam.exe" -applaunch 530 -heapsize 512000 -novid

Change the WINEPREFIX to your home directory.

So if you have similar hardware you should be able to play!

This helped make the game just about playable for me.

---

### Post by kroenecker on 2008-11-13
This is slightly related.

I was trying to figure out how to get the microphone to be usable while playing L4D.  I am using the ALSA driver under winecfg (audio).  Basically all I had to to was run alsamixer (command line) and adjust the mic boost to 0 and lower the "Digital" column value to around 10.

The trick is that the "Digital" column is under the capture values which you access by hitting the <tab> key until either [Capture] or [All] are highlighted (upper left).

Thats all!  Kind of a note to self.

---

### Post by captaincrook on 2008-11-15
Funny, I had to use OSS. Wish my mic worked well in wine using ALSA. :C

Anywhoo, someone hilariously rated this as Platinum on the Wine appdb. I know why (it does WORK outside the box), but its not so good to rate it so high when you get bad performance. Lets hope someone can get this working smoothly. CodeWeavers? X)

---

### Post by Phil Urich on 2008-11-23
I was about to give this another go . . . and then when I loaded up Steam I was treated to the demo being retroactively disabled.  I mean, christ, I'd have settled for even just standing around in a room in single player, I just want to see if it'll run decently (or at all!) on my computer before I actually buy it.  Way to go Valve, you've successfully lost a customer.

---

### Post by Dizzle7677 on 2008-11-23
> **captaincrook said:**
> Anywhoo, someone hilariously rated this as Platinum on the Wine appdb. I know why (it does WORK outside the box), but its not so good to rate it so high when you get bad performance.

  I found this very curious too. Who would have a vested interest in seeding good scores/ratings about their games.....Hmmmmmmmmmm

  For my gpu, poor performance is mainly centered around translating XBOX360 ports / HLSL shading language based games. I've never had a problem with Cg shading probably b/c it's designed to be compiled into OpenGL & Directx. Course you could compile HLSL into Cg and GLSL and back again. The tools are out there.  Sorry is this the wine-dev forum?! my bad. :)

---

### Post by satbunny on 2008-11-25
Well I have just wasted 30 minutes investigating this to doscover that Steam no longer offer the demo, and I am NOT risking buying the full game.

Mind you, my son just has and installed it on his XP box so I guess I'll have to have a go on that when he's out!

Silly Valve.

---

### Post by kroenecker on 2008-11-30
The game does run well enough for me to play.  I posted the specs of my machine a couple pages back.  I am using the stock version of wine on Intrepid.  Possibly 1.1.0?

---

### Post by kroenecker on 2009-01-03
Here is the latest command that I use to play L4D:

env WINEDEBUG="-all wine-pthread" WINEPREFIX="/home/<user>/.wine" wine "C:\Program Files\Steam\steam.exe" -applaunch 500 -heapsize 512000 -novid +mat_hdr_level 0

The "+mat_hdr_level 0" removes the hdr lighting which does make the ambiance of the game less appealing.  However, the game plays much more smoothly!

---

