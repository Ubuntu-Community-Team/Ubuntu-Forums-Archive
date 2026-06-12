---
title: "iMac flat-panel monitor / xorg problems"
date: 2006-02-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by mcubed on 2006-02-06
I've installed Breezy on an iMac G4 (800MHz) with a 15" flat panel monitor and an nVidia GeForce2 MX (32MB DDR).  The display looks great, but I have a few problems, probably related:

1)  No virtual consoles.  CTRL+ALT+Fn does nothing.

2)  More troubling:  The monitor won't go into sleep mode.  Instead of turning off, it turns white.  Also, I can't properly shut down -- again, the monitor just turns white.  I can, however, reboot.

I had a look through the xorg log and I didn't see anything obvious.  In the way of warnings, here is this:

```
(WW) Ignoring request to load module GLcore
```

And later this:

```
(WW) NV(0): config file hsync range 28-51kHz not within DDC hsync ranges.
(WW) NV(0): config file vrefresh range 43-60Hz not within DDC vrefresh ranges.

```

Am I using the wrong refresh rates?  Or is some module causing this problem, or the framebuffer?  I don't know much about how the xserver works and I don't want to start randomly changing things to see what happens.

These are the modules from xorg.conf:

```
Section "Module"
        Load    "GLcore"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

```

I'm using "DPMS" and the DRI is 066.  Driver (obviously!) is "nv".  GLcore does get loaded, later in the log:

```
(II) Loading /usr/X11R6/lib/modules/extensions/libGLcore.a
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_norm.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_xform.o":  No symbols found
(II) Module GLcore: vendor="X.Org Foundation"
        compiled for 6.8.2, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.2

```

All other modules seem to get loaded without issue.  Any help, advice?

---

### Post by jlgoolsbee on 2006-02-07
I have similar issues, though I wonder - did you at least get X running?  I cannot get that far.  Parts of my log are very much like yours (mine also ignores GLcore, and skips the libGLcore)..

My thread is [here]("http://www.ubuntuforums.org/showthread.php?t=126936"); maybe the solution to your problems will help mine?

---

### Post by mcubed on 2006-02-07
Yeah, X looks very nice.  The problem is the lack of consoles and the inability to sleep the monitor.  But the latter (and probably the former) is because of the nVidia card.  I read on the debian-powerpc list that the sleep function in these flat-panel iMacs is controlled by the video card rather than the processor.  ATI gave the developers the code they needed to implement sleep in Debian, but nVidia of course has not.  I will never buy another machine with one of their products again.

I don't think, though, that we have the same problem, exactly.  Maybe the "GLCore" thing is just the way it happens.  X has not crashed on me, and the only time I got a constrained display (the desktop was surrounded by a 1.5-inch thick black border, as if my monitor was 10" instead of 15") it was because I used the fbdev driver by mistake.

Is there a reason you're not using the "nv" driver?  From your log file, it looks like you're using fbdev.

**edit:  I meant to say that the nVidia issue also applies to PowerBooks with nVidia cards, which it looks like you have.

---

### Post by jlgoolsbee on 2006-02-08
I'm really not sure why, or even what fbdev is... I am a newb on a lot of this; I have experience with UNIX, but not enough to know how to roll my own kernel, or even know how to define what drivers X uses (is that in the X conf file?).  I can say with certainty that I could do it if I could find it oulined...

---

### Post by jlgoolsbee on 2006-02-09
Well, i did manage to fix part of my issue by redoing the X server configuration (sudo dpkg-reconfigure xserver-xorg), and defining the driver as "nv."  I'm not sure why, but I'm pretty certain that it didn't ask me which driver to use during the initial install... oh well.

But... not all is well in PowerBook land.  It only lets me use 640x480.  I found [this thread]("http://www.ubuntuforums.org/showthread.php?t=93719&highlight=640x480"), but his fix (and yes I defined the correct resolution for my book) didn't work for me, which is odd because his was also a PB (though his was a 667 mhz 15" w/ ATI and mine's a 1.33 ghz 12" w/ Nvidia).

---

### Post by mcubed on 2006-02-09
Hmm ... choosing the right driver fixed the display issue for me, and allowed me to use the correct resolution (on this machine, it's 1024x768 ).  Did xorg ask you where your card was and did you specify the location?  I think the first time I installed, I didn't put anything in (and there was no default value), which probably contributed to the display being off.  Strangely, I have the same issue cybergypsy mentions:  lspci reports the controller at 00:10:00, but I know from before it was PCI:0:16:00, which is what I entered when I reconfigured xorg.  Now I'm confused!:confused: 

I will have to look into that, but I don't think it will help with my issue.  For you, it sounds like maybe you need to enter the correct modelines manually?  I think that's what cybergypsy was referring to in his last post -- the modeline for 1152x768.  Hopefully, he (or somebody with your model PowerBook) will respond.

---

### Post by jlgoolsbee on 2006-02-09
ok, well... if I was going to input that information into my xorg.conf manually, where would I find that sort of detailed information about my 1024x768 (12" PB) lcd?

---

### Post by mcubed on 2006-02-09
There are at least a few modeline generator websites.  Here's one:
[http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl)

You can find more via Google.  Might want to compare the output from a few of them, to be on the safe side.

---

### Post by jlgoolsbee on 2006-02-10
that did it for me!  thanks a bundle; i'm learning so much so quick!

---

