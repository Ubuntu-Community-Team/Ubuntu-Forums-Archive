---
title: "S.T.A.L.K.E.R. - Shadow of Chernobyl"
date: 2008-06-06
forum: Wine
---

### Post by Jimjim32 on 2008-06-06
Just installed Ubuntu, got Linux mint before that (Ubuntu variant).
Running latest version of wine, every seemed OK.
Wine appDB says that with the -dsound command line option, I will get a divide by zero error. When I start the command through the icon, I just end up with a black screen, which I assume is the divide by zero error. Starting through terminal give a whole bundle of errors as well as the same black screen. Any help recieved would be greatly appreciated, and I would be really grateful, as it suck to spend £10 for nothing. Thanks,

-JJ32-

PS - Yes I have a good enough graphics card, Geforce 8600.

---

### Post by cogadh on 2008-06-06
Did you already do all the other configuration steps on the AppDB page? Also, it might help if you posted the terminal output, it probably has some pretty informative error messages in there.

---

### Post by Jimjim32 on 2008-06-06
# Use -dsound command line option to start the game. Otherwise it will crash with "Divide by zero" error
# Enable GLSL - using ARB will brake some geometry (like flipped or missing guns). Note: GLSL is enabled by default since wine-0.9.49
# Set "OffscreenRenderingMode" to "fbo" and select "Static lighting" render in the game(dx8 mode) - fixes broken lighting (too bright/dark)
# Use -nodistort command line option to fix slowdown from using fbo
These steps stumped me.
Terminal= lots of errors about "unable to use first Mb of memory"

---

### Post by cogadh on 2008-06-06
The errors about the preloader can be fixed using the info here:
[http://wiki.winehq.org/PreloaderPageZeroProblem](http://wiki.winehq.org/PreloaderPageZeroProblem)

The "OffscreenRenderingMode" item is accomplished through a registry edit. You can find info on doing that here:
[http://wiki.winehq.org/UsefulRegistryKeys](http://wiki.winehq.org/UsefulRegistryKeys)

AFAIK, the "static lighting" fix is an in-game setting, once you get the game to launch, you can make that change.

You don't need to do the GLSL thing anymore and the "-nodistort" is accomplished the same way you did the -dsound thing:
```
wine <executable name>.exe -dsound -nodistort
```

---

### Post by cogadh on 2008-06-06
Hmm, I was just looking through the bugfix list for Wine 1.0-rc4 (just released today) and noticed this:
```
 10580  S.T.A.L.K.E.R. shadow corruption with ARB shaders
 12794  S.T.A.L.K.E.R. Screen is black
```
You might want to give that version of Wine a shot to correct your problem.

---

### Post by Jimjim32 on 2008-06-06
Thanks, but I ran into a little problem; the registry specified appears not to exist. Little odd. It may have something to do with my graphics card driver, which is non-proprietary. Geforce 8600 by the way.
That is to say that past "wine" on the registry list, there is no "direct 3D" part. None. No sign of it. Thanks for all your effort in helping, and stalker does work, but with giant errors, like revolving colored textured plants. Very surreal

Forgot to ask, how are you today?

---

### Post by cogadh on 2008-06-06
Those registry keys don't exist because you need to create them yourself.

Fine thanks, and you?:)

---

### Post by Jimjim32 on 2008-06-06
Ohhhhh... :)
I feel really stupid now. Thats awesome.
I'm also fine now, though yesterday I was so pissed about my failure with Ubuntu you could have cooked a three course meal from the heat over my ears.

[-o< I have it working now!

---

### Post by 1337 on 2008-06-09
> **Jimjim32 said:**
> [-o< I have it working now!

Can you post your computer specs and say something about performance while running Stalker? Cause I'm curious about this title.

Regards

---

### Post by MidsummerDreams on 2008-07-25
> **1337 said:**
> Can you post your computer specs and say something about performance while running Stalker? Cause I'm curious about this title.

Regards

I too would like to hear more about this and how it works/plays.

---

### Post by Viranh on 2008-07-27
I just installed S.T.A.L.K.E.R. today and patched it to v. 1.0004. I'm running it on a System 76 serval performance:
2.5 Ghz core 2 duo
4 gb RAM
nVidia 8600M GT w/ 512 Mb dedicated memory
Ubuntu 8.04x86_64

I am using wine 1.1.1. I have added the registry key for OffscreenRenderingMode and am starting it using -dsound -nodistort. I've been playing it for the last hour and haven't run into any problems. I was using static lighting. I think that the game looks good and plays well. It doesn't seem slow at all except when the new game loads. Game play is not slow.  I have the other graphics settings set to "high" and it seems to be handling that fine. I'd actually recommend it to someone running Linux before someone with Windows. Securom/Starforce copy protection can do a good job of trashing a Windows install.

---

