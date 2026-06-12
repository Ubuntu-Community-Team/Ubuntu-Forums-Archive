---
title: "Video playback issues / system hangs"
date: 2009-07-19
forum: x86 64-bit Users
---

### Post by cybermage1 on 2009-07-19
I've recently installed Ubuntu 9.04 64-bit on a Dell Inspiron 531 Athlon 64 X2 5600+ with 4gb of ram and a radeon hd 4670/512mb graphics card. 

I applied all available updates and installed the ATI Radeon drivers via envy.

For video playback I installed VLC and Mplayer. I also installed the gstreamer packages and w32codecs.

Worked like a charm.

However, I've run into a couple of problems that I've been unable to resolve:

1. video playback is very choppy and slow. It sometimes feels as if  I'm sitting in front of a 2/86 pc.

2. nine times out of ten, VLC---or any other video player---brings the whole system to a halt: When I double-click on an AVI, for example, VLC opens, then everything hangs, keyboard and mouse don't respond to any input. I always have to cold-reboot.

I'd very much appreciate any pointers or suggestions as to what I could do to solve these two issues. Because other than that I'm quite happy with Ubuntu.

---

### Post by Moop on 2009-07-19
Did you mean that you installed the w64 codecs?  

Have you tried turning off the visual effects so you can rule out compiz being the problem?

---

### Post by cybermage1 on 2009-07-19
> **Moop said:**
> Did you mean that you installed the w64 codecs? 
 
Have you tried turning off the visual effects so you can rule out compiz being the problem?
 
Yes, sorry, I meant the w64codecs.
 
Yes 2: I turned off visual effects completely. That's the first thing I did because Gnome was way too slow with it.

---

### Post by Moop on 2009-07-19
Using visual effects shouldn't have slowed down gnome on your pc. I'd guess that you have a video card driver problem. I have an older ATI x1950 and use the open source ATI driver with good results. 

Why did you use envy? Was there no restricted driver available?

---

### Post by cybermage1 on 2009-07-19
> **Moop said:**
> Using visual effects shouldn't have slowed down gnome on your pc. I'd guess that you have a video card driver problem. I have an older ATI x1950 and use the open source ATI driver with good results. 

Why did you use envy? Was there no restricted driver available?

Whenever I enabled the proprietary restricted drivers Ubuntu offers, the system would boot into a blank screen where nothing worked at all. I tried some of the solutions I found online but none of them worked for me. I even re-installed Ubuntu once. Same results. That's why I gave envy a shot.
Envy pulled the drivers from the ATI site and installed them with no problems (at least that I could tell---no blank screen at last).

fglrxinfo:
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 4670
OpenGL version string: 2.1.8575

fgl_glxgears reports
5211 frames in 5.0 seconds = 1042.200 FPS
8772 frames in 5.0 seconds = 1754.400 FPS
8138 frames in 5.0 seconds = 1627.600 FPS
7767 frames in 5.0 seconds = 1553.400 FPS
6942 frames in 5.0 seconds = 1388.400 FPS

The drivers seem to work just fine.

In addition, I added the following line to xorg.conf

        Option      "VideoOverlay" "on"

under the "Device" section.

---

### Post by Thelasko on 2009-07-21
It could be an audio issue.  Install pavucontrol and run it to determine if the programs in question are utilizing pulse audio.  If this is the case, you may need to install lib32asound2 and/or libasound2.

---

