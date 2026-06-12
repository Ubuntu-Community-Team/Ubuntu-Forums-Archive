---
title: "Ubuntu AMD64, ATI and MPlayer??"
date: 2005-07-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by Ruud on 2005-07-05
I've read through a bunch of posts here in this forum, and still I can't get MPlayer to work! :cry: 

Have installed the MPlayer package with Synaptic, and even tried compiling it myself with the help from [arnieboy's guide](http://www.ubuntuforums.org/showthread.php?t=31061).

The output I get from MPlayer is:
```

ruud@ruudtv:/media/movies$ mplayer Amiga*.mpg
MPlayer 1.0pre6-3.3.5 (C) 2000-2004 MPlayer Team
CPU: Advanced Micro Devices  (Family: 8, Stepping: 0)
Detected cache-line size is 64 bytes
Cannot test OS support for SSE, disabling to be safe.


Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0 : No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing Amiga1000Commercial.mpg.
Cache fill:  0.00% (0 bytes)    MPEG-PS file format detected.
VIDEO:  MPEG1  384x288  (aspect 8)  25.000 fps  1150.0 kbps (143.8 kbyte/s)
==========================================================================
Trying to force audio codec driver family libmad...
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 44100 Hz, 2 ch, 16 bit (0x10), ratio: 28000->176400 (224.0 kbit)
Selected audio codec: [mad] afm:libmad (libMAD MPEG layer 1-2-3)
==========================================================================
vo: X11 running at 1024x768 with depth 24 and 32 bpp (":0.0" => local display)
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 384 x 288 (preferred csp: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
**The selected video_out device is incompatible with this codec.**
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm:libmpeg2 (MPEG 1 or 2 (libmpeg2))
==========================================================================
Checking audio filter chain for 44100Hz/2ch/16bit -> 44100Hz/2ch/16bit...
AF_pre: af format: 2 bps, 2 ch, 44100 hz, little endian signed int
AF_pre: 44100Hz 2ch Signed 16-bit (Little-Endian)
alsa-init: got device=0, subdevice=0
alsa-init: 1 soundcard found, using: default

``` 

I've set -vo to xv as described in many posts, but still: Nothing.

Installed the fglrx driver described in the [BinaryDriverHowTo](https://wiki.ubuntu.com/BinaryDriverHowto),
and modified the xorg.conf file like this:
```

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 9600 XT (RV350 AR)"
	Driver		"fglrx"
	BusID		"PCI:2:0:0"
	Option "UseInternalAGPGART" "no"
	Option "VideoOverlay" "on"
	Option "OpenGLOverlay" "off"
	Option "XaaNoOffscreenPixmaps"
EndSection

``` 

I know I'm totally new to Linux, but I actually don't know how much it should take to get it working???
Really love Ubuntu and it's driver support, everything but the ATI-card works perfectly on my Shuttle SN85G4v2 box... :) 

Somebody, please help me!  :grin:

---

### Post by bk452 on 2005-07-05
> Somebody, please help me!

I wish someone would.  I had a devil of a time with mplayer but I got it working & I love it.  I don't know what I did to get it working and I wish someone would give a guide to the rest of us.

---

### Post by Ruud on 2005-07-05
haha... tnx for reply..

I consider myself to be a really pacient guy, but soon I'm going to go bananas.  ](*,) 

It's the hard life of a newbie I guess...  :roll:

---

### Post by Ruud on 2005-07-05
UPDATE: It's working!!!! :D

but sadly, I have NO IDEA why...  :lol: 

I was just playing with how to get my Soundblaster Live! 24bit USB to work, and issued the command
```

echo "options snd_intel8x0 index=-2" | sudo tee -a /etc/modprobe.d/alsa-base

```
found somewhere on this forum, turned off soundserver, and everything suddenly works!!!! strange... Was it a soundproblem?  :roll: I will propably never find out..

Posting the relevant info from my xorg.conf and mplayer.conf, if anyone can find it useful:
mplayer.conf:
```

vo = xv
or
vo = x11
(they both worked for me...)

zoom = yes

```

xorg.conf:
```

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 9600 XT (RV350 AR)"
	Driver		"fglrx"
	BusID		"PCI:2:0:0"
	Option "UseInternalAGPGART" "no"
	Option "VideoOverlay" "on"
	Option "OpenGLOverlay" "off"
	Option "XaaNoOffscreenPixmaps"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

fglrxinfo returns:
```

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 XT Generic
OpenGL version string: 1.3.4769 (X4.3.0-8.8.25)

```

---

### Post by locutus42 on 2005-07-09
Sorry I didn't find your post earlier but I have to pass mplayer "-vo gl and -ao esd" to get it all working with ATI based Ubuntu 5.04 installation. I then created a little mplayer launcher( $HOME/bin/mplayer ) so that my version is launched instead of the default.


#!/bin/bash
#---------------- simple mplayer launcher ----------
/usr/bin/mplayer -vo gl -ao esd $1

I use the "gl" video output device since the ATI fglrx driver is pretty good at OpenGL support( 2D and 3D ).

I have had other problems with sound not working. For instance, TuxRacer doesn't play sound. Oh well, eventually I'll figure that one out. It's probably and OSS issue.

---

