---
title: "Diablo 2: Direct3D Fails on Fullscreen- Glide looks crappy..."
date: 2007-12-03
forum: Wine
---

### Post by GSF1200S on 2007-12-03
I installed Diablo 2 LOD under wine, and it works awesome, except that im currently forced to use Glide instead of Direct3D. Glide leaves the graphics looking like crap when fullscreen.

If I try to use DirectDraw, it returns a message saying it cannot initiate the game client window (when using the D2Loader), Error 25: A critical error occured initializing direct3D (if using the regular d2.exe) and spits out this in the terminal regaurdless of which one I use:
```

err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found(640x480x16)! (XRandR)
```

I tried adding 640x480 to the xorg.conf, and changing the default depth to 16 as an experiment, but I still got the same message. If I emulate a virtual desktop, Direct3D works fine- its just that the window is very small and hard to see anything in.

If I use the 3dfx glide wrapper, I can run fullscreen, but it looks like crap as the graphics are very blurry... If I enable the render to texture option in glide-init.exe, the game looks sharp, but the framerate is literraly so horrible the mouse will only move once every five seconds. Its strange, I have a badda** video card, at least as far as D2 is considered... 

I would have posted this in wine, but this isnt a wine issue- I think it has to be something in xorg, because emulating a virtual desktop essentially just takes linux out of the picture... Any ideas on this?

---

### Post by Glenn1337 on 2007-12-03
I dinstaled D2:LOD on wine and it ran like crap... wine seems to be one or the crappiest emulators ever... are there any alternatives?

---

### Post by hikaricore on 2007-12-03
> **Glenn1337 said:**
> I dinstaled D2:LOD on wine and it ran like crap... wine seems to be one or the crappiest emulators ever... are there any alternatives?

.... /slap

---

### Post by cogadh on 2007-12-03
> **Glenn1337 said:**
> I dinstaled D2:LOD on wine and it ran like crap... wine seems to be one or the crappiest emulators ever... are there any alternatives?
***W***ine*** I***s*** N***ot an ***E***mulator...

and no, there really aren't any alternatives (that aren't actually based on Wine) other than using Windows. Diablo 2 actually runs very well on Wine. If it doesn't work for you then you either configured Wine or the game incorrectly.
Diablo 2: [http://appdb.winehq.org/appview.php?iVersionId=49](http://appdb.winehq.org/appview.php?iVersionId=49)
LOD: [http://appdb.winehq.org/appview.php?iVersionId=315](http://appdb.winehq.org/appview.php?iVersionId=315)

---

### Post by GSF1200S on 2007-12-03
Well, if nobody knows, does anyone at least have direct3d working with fullscreen? It even says on the Wine page to not run in virtual desktop mode, and it makes no mention of the glide wrapper, so im assuming someone has this working...

---

### Post by cogadh on 2007-12-03
I hate to say it, but D2 is one of those apps that "just works" in Wine. Other than making sure your xorg.conf includes the correct resolution / BPP and making sure your CD-ROM is configured correctly in Wine, you shouldn't have to do anything at all to get it working.

Since you did edit your xorg.conf to include the correct resolution, did you happen to remember to restart the X server afterwards? The change isn't actually in effect until you do that.

---

