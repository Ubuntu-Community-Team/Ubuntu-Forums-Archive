---
title: "Diablo 2 + LOD + Lastest ATI + Latest Wine = LOW FPS"
date: 2007-01-11
forum: Wine
---

### Post by cjr2k3 on 2007-01-11
I got Diablo 2 + LoD installed just right. Played "out-of-the-box" with latest patch with 3D aceleration.

I've been playing nicely with Sound and everything maxed out in video settings.

In Act 4 it is almost impossible to play, i get 2~3FPS. Even with everything at minimum, no sound...

My graphic card is a Radeon X1400 512Mb, no its not a problem from there. Also the drivers are well installed. Im NOT using Xgl or Beryl.

I have wine using a Virtual Desktop (800x600). 

Any help would be apreciated.

---

### Post by hugh on 2007-01-17
> **cjr2k3 said:**
> I got Diablo 2 + LoD installed just right. Played "out-of-the-box" with latest patch with 3D aceleration.

I've been playing nicely with Sound and everything maxed out in video settings.

In Act 4 it is almost impossible to play, i get 2~3FPS. Even with everything at minimum, no sound...

My graphic card is a Radeon X1400 512Mb, no its not a problem from there. Also the drivers are well installed. Im NOT using Xgl or Beryl.

I have wine using a Virtual Desktop (800x600). 

Any help would be apreciated.

Run wine D2VidTst.exe and choose DirectDraw 2D for your rendering.

---

### Post by Fitzy_oz on 2007-01-18
> **cjr2k3 said:**
> I got Diablo 2 + LoD installed just right. Played "out-of-the-box" with latest patch with 3D aceleration.

I've been playing nicely with Sound and everything maxed out in video settings.

In Act 4 it is almost impossible to play, i get 2~3FPS. Even with everything at minimum, no sound...

My graphic card is a Radeon X1400 512Mb, no its not a problem from there. Also the drivers are well installed. Im NOT using Xgl or Beryl.

I have wine using a Virtual Desktop (800x600). 

Any help would be apreciated.

> **hugh said:**
> Run wine D2VidTst.exe and choose DirectDraw 2D for your rendering.

And try it with the WINEDEBUG="-all" wine D2VidTst.exe or the normal executable.  Direct rendering is definitely on?

---

### Post by FrostDust on 2007-03-11
I am in a similar situation as cjr2k3, and the DirectDraw 2d option doesn't appear when I run D2VidTst.exe, only Direct3D and 3dfx Glide. Using the Glide wrapper, as it says to here: [http://www.ubuntuforums.org/showthread.php?t=362457&highlight=diablo+2](http://www.ubuntuforums.org/showthread.php?t=362457&highlight=diablo+2), results in the game crashing during start up, and the Direct3d option is miserably slow. The game had been running perfectly until recently.

---

### Post by God Of Atheism on 2007-05-23
> **Fitzy_oz said:**
> And try it with the WINEDEBUG="-all" wine D2VidTst.exe or the normal executable.  Direct rendering is definitely on?

After another Ubuntu reinstall, I've run into more or less the same problem, with the 2d option not appearing in the videotest, glide being recommended and actually running as opposed to last time I tried, but the game slowing down severely when encountering monsters (in town it seems to do fine).

The output of WINEDEBUG="-all" wine D2VidTst.exe was:
```

libGL error: drmMap of framebuffer failed (Cannot allocate memory)
libGL error: reverting to (slow) indirect rendering

```

So according to the above, something goes wrong with direct rendering.

Graphics settings in winecfg:
```

allow the window manager to manage created windows
vertex shader support: hardware
all the rest disabled

```

I managed to get the sound running (which was greyed out earlier) by using ALSA with driver emulation. In the audio tab of Winecfg, Hardware Acceleration is set to Emulation. Should other settings be faster here? Full did not work this time, default sample rate and bits per sample are still set at 44100/16, which might be too much.

My videocard is unfortunately also an ATI card, but a 9600XT with 256MB.

Any ideas?

---

### Post by Akingboy on 2008-07-15
I got the same problem. Is there fix for low fps with direct3D on ati card please?

---

### Post by darklegion on 2008-07-16
Try the unofficial glide-to-opengl wrapper : [http://www.svenswrapper.de/english/index.html](http://www.svenswrapper.de/english/index.html)

I haven't tested it myself, but it's reported to work well on Diablo 2's appdb page.

---

### Post by evets25 on 2008-07-16
The answer to your problem is probably a lot simpler than reinstalling ubuntu or using the glide wrapper. Try running Diablo fullscreen and not in a virtual desktop, and try switching to software rendering mode instead of direct3d. Either one of those two things should fix it, if not, then you have bigger problems...

---

