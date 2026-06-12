---
title: "mplayer shows no video"
date: 2007-02-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by benrboone on 2007-02-11
I have just reinstall edgy. I used automatrix2 to install mplayer for firefox.  It was work very well.  However I then decieded to put my home directory on a seprate partition.  That seemed to go well except now mplayer will not work.  It plays sound but no video. here is my mplayer output 

~$ mplayer 1.wmv
MPlayer 2:0.99+1.0pre8-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ (Family: 15, Model: 43, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.


Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.

Playing 1.wmv.
ASF file format detected.
VIDEO:  [WMV3]  400x300  24bpp  1000.000 fps    0.0 kbps ( 0.0 kbyte/s)
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 64.0 kbit/4.17% (ratio: 8004->192000)
Selected audio codec: [ffwmav2] afm: ffmpeg (DivX audio v2 (FFmpeg))
==========================================================================
==========================================================================
Requested video codec family [wmv9dmo] (vfm=dmo) not available.
Enable it at compilation.
Requested video codec family [wmvdmo] (vfm=dmo) not available.
Enable it at compilation.
Cannot find codec matching selected -vo and video format 0x33564D57.
Read DOCS/HTML/en/codecs.html!
==========================================================================
alsa-init: using device default
alsa: 48000 Hz/2 channels/4 bpf/65536 bytes buffer/Signed 16 bit Little Endian
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:  41.1 (41.1) of 42.0 (42.0)  0.4% 
alsa-uninit: pcm closed

Exiting... (End of file)


running on amd 64bit.:confused:

---

### Post by mfdc1969 on 2007-02-11
Hey - i'm a newb having only used Linux for 6 months but after I had a similar problem I  found some answers reading this post:

[http://ubuntuforums.org/showthread.php?t=188974&highlight=mplayer+32bit+libraries](http://ubuntuforums.org/showthread.php?t=188974&highlight=mplayer+32bit+libraries)

Reinstalling the 32bit packages/libraries seemed to solve my issues -- don't ask me how or why please:)  -- maybe it will work for you?

Mike

---

