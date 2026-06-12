---
title: "Installed Steam-CounterStrikeSource but can only play windowed..."
date: 2007-09-23
forum: Wine
---

### Post by ROUBOS on 2007-09-23
Hi I installed wine and ran Steam from my CD. I downloaded CounterStrike Source and managed to get it working.
The problem is that I can only get it to work in windowed mode. When I change that in winecfg it does not work.
I need to have wine to emulate a virtual desktop in order for it to work.

This is my shortcut on my desktop:

env WINEPREFIX="/home/thephantom/.wine" wine "C:\Program Files\Valve\Steam\steam.exe"  -applaunch 240 -gl -dxlevel 90 -console

OK I also sometimes get the following error:

Steam Startup() failed: Steam Startup failed with error 1: The registry is used by another process, timeout expired.

Now the steam menu is slower.

I also notice that the sound (which I have set to OSS but I'm using ALSA) might be slowing my gaming down.

I also change the launcher properties to:
env WINEPREFIX="/home/thephantom/.wine" wine "C:\Program Files\Valve\Steam\steam.exe"  -applaunch 240 -gl -dxlevel 90 -console -fullscreen -width 1280 -height 1024

Any ideas? Am I doing something wrong?

Any recommendations for the audio settings in wine?

---

### Post by ROUBOS on 2007-09-23
Don't worry about it. It's not playing properly anyway. I have the ATI RADEON X1950pro and it's killing me that I cannot use my card and play games on my Linux box. 
I know it's not Linux's fault but I should just stick to Neverwinter Nights that works natively under Linux.

---

### Post by Nim-X on 2008-05-25
any solutions to play counsterstike in full screen?

---

### Post by Rusty023 on 2008-05-25
You're doing better than me, I can't even get Steam to run. I'd be happy with Windowed mode.

---

