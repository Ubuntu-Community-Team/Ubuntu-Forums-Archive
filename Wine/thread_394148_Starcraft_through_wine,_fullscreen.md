---
title: "Starcraft through wine, fullscreen"
date: 2007-03-26
forum: Wine
---

### Post by fearpi on 2007-03-26
I am having some trouble running Starcraft through wine. If I run winecfg, and then choose a virtual desktop of 640x480, I can run Starcraft in a window just fine. However:

1) If I choose a virtual desktop of 800x600, the game actually runs full-screen. But I have a widescreen monitor, and the game retains its 4:3 ratio so that the bottom of the screen goes off the monitor.

2) If I un-check virtual desktop and try to run it full-screen, the screen goes completely black and I see thin white lines sporadically move down the screen. I hear sound, but I can not exit the game with any set of keystrokes.

I am using the latest nvidia drivers, and am using a notebook.

---

### Post by fearpi on 2007-03-27
Also, I have several modes including "640x480" and "800x600" in each of 24, 16, 15, and 8 bpp in xorg.conf, so that doesn't seem to be the problem.

---

### Post by ben-g on 2007-04-19
I'm having the same problem. It was working for me before I upgrade to wine-0.9.35. 

I'm upgrading to feisty right now I'll see if that does anything.

---

### Post by fearpi on 2007-04-19
Please post back here if it does. I haven't tried it since upgrading to feisty and I'd be interested in seeing how it works for you.

---

### Post by Hawk__0 on 2007-05-05
I made it work.
fiesty + NO beryl/desktop effects, and it works.

---

### Post by fearpi on 2007-05-06
I tried it without Beryl on Feisty. The game still goes off the bottom of my 16:10 screen.

---

### Post by priegog on 2007-05-19
I have the exact same problem. If I run it fullscreen a part of the bottom goes off the screen. If I do a 640X480 window, well, It's too tiny and uncorftable to play well (even with my glasses on, which I normally dont use to play games).
Anybody has any more ideas? 
I am running feisty with no desktop effects or beryl, on a laptop with a widescreen. My screen resolution is 1280X800

---

### Post by Green_86 on 2007-05-21
You just need to add the line 
```

Section "Monitor"
  identifier "Generic Monitor"
  vendorname "Generic"
  modelname "Flat Panel 1280x800"
  HorizSync 31.5-90
  VertRefresh 60
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync <------ This one
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
  modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
  modeline  "1600x1024@60" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
  modeline  "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
  modeline  "1920x1200@60" 193.16 1920 2048 2256 2592 1200 1201 1204 1242 -hsync +vsync
  gamma 1.0

```
to your xorg.conf
hope this helps it did the trick for me :D

---

### Post by priegog on 2007-05-21
Well, I was hopeful, but no, a part from the bottom is still missing :(
Come on, I know there's an X and/or WINE expert out there who can help us. 
Thanks a lot, tho.

However, my xorg.conf file was different than yours in that section:
It lacked both these lines:

  vendorname "Generic"
  modelname "Flat Panel 1280x800"
 as well as every "modeline", and gamma too.

I know xorg files are supposed to be different, just sayin in case the problem lies there by any chance.

---

### Post by meldroc on 2007-05-21
I'm getting the exact same problem on my Asus A8Js, which has a screen with a native resolution of 1440x900 (16:10 aspect ratio.)  When I switch to 640x480, the bottom of the screen is cut off, not just in WINE, but even if I hit Ctrl-Alt-+ to switch video modes in X.

For now, my workaround is to run Starcraft in a window, then hit Ctrl-Alt-+ to zoom to 800x600, which makes the game playable.

Modelines don't seem to do much - the Nvidia drivers are rigged to auto-detect the display, come up with what it thinks are reasonable modes, including one for the native resolution, and a few lower resolutions like 1024x768, 800x600, 640x480, and use the detected modes instead of modelines.

---

### Post by priegog on 2007-05-21
Well, at least I learnt your little shortcut. (Crtl+alt++).
Altho not ideal, it makes it a little bit better.
Still looking for that answer tho!

---

### Post by man40 on 2007-11-15
I also miss the last inch of my starcraft from the bottom while running on 6480x480.
But I found a solution... at least works :)

when you wish to play starcraft, change the resolution to 640x480 from
 System -> Preferences -> Screen Resolution.
Start StarCraft with wine.
Enjoy!!!

/* put the resolution back to normal afterwards.*/

---

### Post by priegog on 2007-11-16
well, thanks, but that is hardly an ideal solution. I just wish there was a way to know who's fault it is (wine's probably) to report the bug.

---

### Post by werries on 2008-06-07
just now finding this a year later. did this ever get fixed? cause i have the same problem. no other issues except im missing an inch off my screen

---

### Post by priegog on 2008-06-07
not that I know of. It seems to happen with a lot of older games in widescreens. Now I just use another monitor to play them.

---

### Post by werries on 2008-06-07
i just now figured it out.
looked at some starcraft stuff and ran
wine "C:\\Program Files\\Starcraft\\StarCraft.exe" & sleep 1 ; xrandr -r 57 

This worked, as it started, waited 1 second, and then changed the refresh rate to 57. This works because of how the 640x480 uses the refresh rate...for some reason. if it doesnt, try changing the thing after sleep, so that it has time to change your resolution and refresh rate when starting,(wine does this), and then it will switch to 57.

---

### Post by priegog on 2008-06-07
whoa, that's a completely unexpected aproach. I will install starcraft later and try it. thanks for the tip

---

### Post by werries on 2008-06-07
yeah it really surprised me. i threw it into gedit and made a bin file, so i could just run "starcraft" in terminal.

---

### Post by frenchn00b on 2008-06-07
> **fearpi said:**
> I am having some trouble running Starcraft through wine. If I run winecfg, and then choose a virtual desktop of 640x480, I can run Starcraft in a window just fine. However:

1) If I choose a virtual desktop of 800x600, the game actually runs full-screen. But I have a widescreen monitor, and the game retains its 4:3 ratio so that the bottom of the screen goes off the monitor.

2) If I un-check virtual desktop and try to run it full-screen, the screen goes completely black and I see thin white lines sporadically move down the screen. I hear sound, but I can not exit the game with any set of keystrokes.

I am using the latest nvidia drivers, and am using a notebook.

dont  use wine

there is  a program that runs under linux, opensource, and use the original cdrom

---

### Post by werries on 2008-06-07
wine is open source, under linux, and uses the original cdrom.
but are you talking about opensource starcraft?

---

### Post by calcfreak83 on 2008-06-08
I use a cute little script to start StarCraft. It puts Starcraft in a completely new Xserver, so you can actually hit Ctrl+Alt+F7 to switch back to gnome, and retain your default resolution. The only thing that might be troublesome (at least for me), is that my volume keys won't work in the new Xserver, probably because the gnome volume manager isn't running. The install is pretty lengthly, you have to change some settings for X11 plus add a completely new Monitor and Server Layout to xorg.conf, but it's pretty cool to see it work. If you guys want the nitty, gritty details, I can post them.

---

### Post by calcfreak83 on 2008-06-08
Wrote a quick Howto, check it out here 
[URL]("http://ubuntuforums.org/showthread.php?p=5144003")

---

### Post by priegog on 2008-06-08
bookmarked, thanks!

---

### Post by werries on 2008-06-08
i like the idea. but why all that hassle when the fix i used works?

---

### Post by calcfreak83 on 2008-06-11
Changing the refresh rate didn't work on my box, plus if you run Starcraft in a separate server, you can switch back to your full resolution anytime you want by pressing Ctrl + Alt + F7

---

### Post by ma7hatter on 2008-11-10
> **werries said:**
> i just now figured it out.
looked at some starcraft stuff and ran
wine "C:\\Program Files\\Starcraft\\StarCraft.exe" & sleep 1 ; xrandr -r 57 

This worked, as it started, waited 1 second, and then changed the refresh rate to 57. This works because of how the 640x480 uses the refresh rate...for some reason. if it doesnt, try changing the thing after sleep, so that it has time to change your resolution and refresh rate when starting,(wine does this), and then it will switch to 57.

This worked for me, although I had to change it to 5 seconds instead of 1 because it was trying to set the refresh rate to early.  I'll bet this solution will work for a lot of the games I run on wine.

Thanks...

---

### Post by Kingsley on 2009-03-08
Anybody have a fix that's compatible with Xorg 1.5?

---

### Post by maudin88 on 2009-07-08
:lolflag: [calcfreak83]("http://ubuntuforums.org/member.php?u=597556") YOU ARE THEE MAN!!  THANK YOU!!!

---

