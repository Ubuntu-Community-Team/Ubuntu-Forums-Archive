---
title: "World of Warcraft OpenGL color bug"
date: 2008-11-16
forum: Wine
---

### Post by n1ghteyes on 2008-11-16
Hello everyone!

Since I installed the 3.02 patch WoW is showing some really weird colors when I try to run it in OpenGL. I also made a post about this on the AppDB, but so far I don't see a solution and only 1 person to replicate this problem. Direct3D is showing perfectly well apart from some shadows, but the main thing I have against it is the performance. Direct3D with 2-10 fps max, whereas OpenGL was doing a way way better job at it.

[http://img58.imageshack.us/my.php?image=problemmt5.png](http://img58.imageshack.us/my.php?image=problemmt5.png) (how it looks on my screen)
[http://imagebin.ca/view/pXax0vE.html](http://imagebin.ca/view/pXax0vE.html) (other AppDB user)

The screenshot is taken a month ago, but giving exactly same faulty colors, the distorted dragon is something which came after making the screenshot so that is not really the problem, only the colors is. Models are all showing great but colors are weird and when I login textures are like they are made of clay and icons are the same as when people were having the "icon-bug".

**Info on my system and settings**

* Done the registry tweak (GL_ARB_vertex_buffer_object)
* Direct rendering: Yes
* OpenGL version string: 1.3 Mesa 7.0.3-rc2
* Glxgears giving average of 1500 fps
* Disabled Compiz
* Running Hardy with latest updates
* Last three releases of wine give the same error
* You would've guessed it by now, I'm using an ATI card (Mobility 9200)
* Installed WoW again from scratch (from another source to exclude corrupt files)
* Loading OpenGL through console works and gives proper colors, problem is it doesn't seem to be rendered through OpenGL as I'm still having the same bad fps
* Both -opengl and editing config.wtf file with SET gxApi "OpenGL" give weird colors

Relevant lines from my config.wtf file:
```
SET ffxDeath "0"
SET ffxGlow "0"
SET hwDetect "0"
SET weatherDensity "0"
SET M2UsePixelShaders "0"
SET M2UseShaders "0"
SET showfootprints "0"
SET Sound_EnableHardware "1"
SET pixelshaders "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxRefresh "60"
SET Gamma "1.000000"
SET gxMultisampleQuality "0.000000"
SET farclip "397"
SET Sound_SoundOutputSystem "1"
SET Sound_SoundBufferSize "150"
SET particleDensity "1.000000"
SET gxTripleBuffer "1"
SET environmentDetail "0.5"
SET baseMip "1"
SET spellEffectLevel "1"
```

Xorg.conf is nothing fancy, just basic:
```

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

```

The colors in the top left corner seem to be allright, also the introduction movie and loading screen are not giving any errors, only rendering models/textures.

It was running fine in 2.4 and really enjoyed playing it on my linux box, but playing with such a low fps in d3d kills me. Does anyone have a solution for this or look remotely familiar to something? Is it ATI related, or because it came up with 3.02 in faulty WoW files?

---

### Post by n1ghteyes on 2008-11-19
bump

---

### Post by Prefader on 2008-12-02
For what it's worth, I've got the same problem.  Eagerly awaiting a fix.

---

### Post by michelefrost on 2008-12-06
Same situation here.

And the worst is that without openGL, the login screen and the character modelling pages are perfect, but then the game hangs in entering the world.

I have checked all tweaks in config file, wine register etc. - all seems to be ok. I installed yesterday so I cannot say if before last patch it was working!

Any hint anyone?

---

### Post by Prefader on 2008-12-06
Got it working . . . someone posted a workaround on the appdb page, but I can't find it anymore.

Anyway, first, edit config.wtf, and remove the line:```
SET gxApi opengl
```then, run WoW with ```
wine $path_to_WoW/WoW.exe -console
```

Once you're at the login screen, hit "~" to open the console, and type ```
gxApi OpenGL
``` then ```
gxRestart
```  This got me into the game with good colors.  Make sure that your Config.wtf doesn't have the line setting opengl before you run it, and it works fine.  Framerate is a little lower than it used to be in game, but I think that's a separate bug.

Hope this helps!

---

### Post by michelefrost on 2008-12-08
ciao

I have no tilde key on my italian keyboard - if I make to it (with AltGr + ^ = ~) I have no WoW console anyway... so I am blocked here. Any hint?!

Meanwhile I go on trying and finding a way...

---

### Post by ajackson on 2008-12-08
Have you tried it without the registry tweak? Mine now works better without it and some people have had stability problems when using the tweak.

Also see if you compiz enabled and disable it if you do, just in case that is causing problems.

---

### Post by Prefader on 2008-12-08
> **michelefrost said:**
> ciao

I have no tilde key on my italian keyboard - if I make to it (with AltGr + ^ = ~) I have no WoW console anyway... so I am blocked here. Any hint?!

Meanwhile I go on trying and finding a way...

Try the "`" key.  I just realized that I don't need to hit shift + ` to open the console, just "`".  Aside from that, I don't really know how to help you.

Good luck!

---

### Post by Eviljim on 2008-12-09
Try Wine version 1.01 and set the program type to Windows XP.

---

### Post by Prefader on 2008-12-09
```
$ wine --version
wine-1.1.10
```

OS version is set to WinXP.

I'm fairly certain that, unless the version you are suggesting we use is a newer one than 1.1.10, this bug appeared AFTER the release of 1.1.  For now, the fix I re-posted to this thread is the only way I can get into the game on my laptop (ATI mobility 9000) with the OSS driver.  On my desktop with the nvidia driver, the game still works fine without any tapdance.

---

### Post by Eviljim on 2008-12-09
> **Prefader said:**
> ```
$ wine --version
wine-1.1.10
```

OS version is set to WinXP.

I'm fairly certain that, unless the version you are suggesting we use is a newer one than 1.1.10, this bug appeared AFTER the release of 1.1.  For now, the fix I re-posted to this thread is the only way I can get into the game on my laptop (ATI mobility 9000) with the OSS driver.  On my desktop with the nvidia driver, the game still works fine without any tapdance.

No, I said 1.01, the stable release version. Anything above that is classed as development and therefore prone to all sorts of glitches/bugs etc.

---

### Post by n1ghteyes on 2008-12-09
> **Prefader said:**
> Got it working . . . someone posted a workaround on the appdb page, but I can't find it anymore.

Thanks for responding but I have already given up :) The guy you mention in your post is actually me, I provided that "fix" on the AppDB in order to play in OpenGL, somehow though it doesn't fix my framerate and therefore doesn't work. 

I found out that I could partially fix it by adding the line below in my config.wtf
```
Set FixedFunction '1'
```
Although this does indeed solve the purplish glow on your textures and models, in my case action bar icons are still looking weird (adding a UIFaster 0-3 doesn't help). Waiting for Blizzard to come up with a patch with the ability to _really_ disable all shader effects.

---

### Post by Prefader on 2008-12-09
[quote=Eviljim]No, I said 1.01, the stable release version. Anything above that is classed as development and therefore prone to all sorts of glitches/bugs etc.[/quote]

Ah, I see the confusion.  1.0.1 is the stable release.  The lack of a point in your post(s) is what made me think you meant 1.1.

Anyway, the problem exists for me in 1.0.1 as well.

[quote=n1ghteyes]The guy you mention in your post is actually me, I provided that "fix" on the AppDB in order to play in OpenGL . . .[/quote]

Then I owe you a thanks!

---

### Post by Eviljim on 2008-12-09
> **Prefader said:**
> Ah, I see the confusion.  1.0.1 is the stable release.  The lack of a point in your post(s) is what made me think you meant 1.1.

Anyway, the problem exists for me in 1.0.1 as well.



Then I owe you a thanks!



Sorry, but there was no confusion my end. 1.01 is not 1.1 whatever way you look at it.

---

### Post by Prefader on 2008-12-09
> **Eviljim said:**
> Sorry, but there was no confusion my end. 1.01 is not 1.1 whatever way you look at it.

Wow, guy, I didn't say you were confused. I said there was confusion, and I understand why now.

---

