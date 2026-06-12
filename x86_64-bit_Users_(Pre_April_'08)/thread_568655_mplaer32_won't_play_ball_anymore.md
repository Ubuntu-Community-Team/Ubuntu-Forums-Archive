---
title: "mplaer32 won't play ball anymore"
date: 2007-10-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by Saubazi on 2007-10-06
I have here a avi file from my digicam mplayer plays it ok but mplayer32 says:

MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Advanced Micro Devices Athlon 64 Newcastle,Winchester,San Diego,Venice; Sempron Palermo (Family: 15, Stepping: 0)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.


Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing Documents/Pictures/Mikko/5_Monat/konttausta.avi.
AVI file format detected.
VIDEO:  [MJPG]  352x288  24bpp  25.000 fps  3007.5 kbps (367.1 kbyte/s)
Clip info:
 Software: Lavf0d.50.5.0
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 44100 Hz, 2 ch, s16le, 224.0 kbit/15.87% (ratio: 28000->176400)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
open: No such file or directory
vo_mga: Couldn't open /dev/mga_vid
open: No such file or directory
vo_mga: Couldn't open /dev/mga_vid
tdfxfb: This driver is only supports the 3Dfx Banshee, Voodoo3 and Voodoo 5
Couldn't open /dev/3dfx
vo_xvmc: X-Video extension 2.2
vo_xvmc: X-Video MotionCompensation Extension version 1.1
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffmjpeg] vfm: ffmpeg (FFmpeg MJPEG decoder)
==========================================================================
Building audio filter chain for 44100Hz/2ch/s16le -> 0Hz/0ch/??...
alsa-init: 1 soundcard found, using: default
alsa: 44100 Hz/2 channels/4 bpf/65536 bytes buffer/Signed 16 bit Little Endian
AO: [alsa] 44100Hz 2ch s16le (2 bytes per sample)
Building audio filter chain for 44100Hz/2ch/s16le -> 44100Hz/2ch/s16le...
Starting playback...
VDec: vo config request - 352 x 288 (preferred colorspace: Planar YV12)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDec: vo config request - 352 x 288 (preferred colorspace: Planar YV12)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.

FATAL: Could not initialize video filters (-vf) or video output (-vo).

alsa-uninit: pcm closed

Exiting... (End of file)

somehow this is too hard a nut for me to crack...

---

### Post by Total_Biscuit on 2007-10-06
Does "mplayer32" mean that you are running 32-bit mplayer on a 64-bit system?  Anyway, did you by any chance specify the wrong video output driver in the command line (-vo ...)?  Alternatively, did you switch desktop effects on/off recently?

---

### Post by Saubazi on 2007-10-06
Yes I am running 32bit (or trying) mplayer on 64bit. No I did not specify any options, it used to work and the 64bit one runs ok with the same file. I am not sure what you mean with desktop effects but then on the other hand wouldn't that influence 64bit mplayer too?

---

### Post by Total_Biscuit on 2007-10-08
By desktop effects I meant compiz.  This can affect what video driver will work best in mplayer (xv vs. gl, for example).  A couple of questions:
[LIST=1]
[*]How did you install 32-bit mplayer - in a chroot?
[*]If in a chroot, I'm wondering whether all necessary directories are mounted, particularly /dev, /dev/pts and /dev/shm.
[*]Why do you need to use 32-bit mplayer?
[/LIST]
EDIT.  PS.  I have 32-bit mplayer sitting in a chroot and don't have any problem.

---

### Post by Saubazi on 2007-10-09
1) no not in chroot - there has been quite a few howtos on this very forum including a .deb for it.
2) not the issue
3) Why not? Somehow one has to play windows related stuff (32bit) and until now mplayer was my preferred choice and until late it also worked. Some late updates must have done the dirty deed and all I want is to get it back and running...

---

### Post by Saubazi on 2007-10-09
Aw never mind - uninstalled the package and installed chroot'ed environment and 32bit mplayer there now it works ok...

---

### Post by Kilz on 2007-10-09
> **Saubazi said:**
> Aw never mind - uninstalled the package and installed chroot'ed environment and 32bit mplayer there now it works ok...

Why do you need a 32bit mplayer?

---

### Post by jocko on 2007-10-09
What's the point with running 32bit mplayer on a 64 bit os?
w32codecs? Why not just install w64codecs instead?
You get them from the [medibuntu]("http://medibuntu.sos-sts.com/repository.php") repos.

---

### Post by Kilz on 2007-10-09
> **jocko said:**
> What's the point with running 32bit mplayer on a 64 bit os?
w32codecs? Why not just install w64codecs instead?
You get them from the [medibuntu]("http://medibuntu.sos-sts.com/repository.php") repos.

Those old windows codecs are not needed with the latest mplayer. But some people think they are.

---

### Post by jocko on 2007-10-09
> **Kilz said:**
> Those old windows codecs are not needed with the latest mplayer. But some people think they are.

Now I know better!
I thought w32 or w64 were required for wmw files, but I checked, and I had even set mplayer so that it can not use anything but ffmpeg, and it plays wmw just fine anyway. (getting rid of one more piece of proprietary software)

---

### Post by Saubazi on 2007-10-10
> **jocko said:**
> What's the point with running 32bit mplayer on a 64 bit os?
w32codecs? Why not just install w64codecs instead?
You get them from the [medibuntu]("http://medibuntu.sos-sts.com/repository.php") repos.

Hmmm... w64codecs - I have medibuntu but there is no package like that. (That is in edgy...)
Did not know that 64bit mplayer can nowadays manage without...anyway vlc can do it as well but the issue is more complex than that...
Once you learn to do things one way that works you don't check every now and then whether another way might already work, right?

Principally it starts with 32bit browser since I suppose there is no 64bit flash there, now is there? (or did I miss that too) and I suppose one wants to combine a sort of mplayer with mediaplayer connectivity? (My possibly other misconseption is that for a 32bit browser I also need a 32bit player?)

Don't tell me that totem is also more than useless in 64bit environment and can show more films than errors? :)

---

### Post by Kilz on 2007-10-10
> **Saubazi said:**
> Hmmm... w64codecs - I have medibuntu but there is no package like that. (That is in edgy...)
Did not know that 64bit mplayer can nowadays manage without...anyway vlc can do it as well but the issue is more complex than that...
Once you learn to do things one way that works you don't check every now and then whether another way might already work, right?

Principally it starts with 32bit browser since I suppose there is no 64bit flash there, now is there? (or did I miss that too) and I suppose one wants to combine a sort of mplayer with mediaplayer connectivity? (My possibly other misconseption is that for a 32bit browser I also need a 32bit player?)

Don't tell me that totem is also more than useless in 64bit environment and can show more films than errors? :)

[Flash for your 64bit browser.]("http://http://ubuntuforums.org/showthread.php?t=476924") you can install mozilla-mplayer for embedded media. For totem you have to install libdvdcss.

---

### Post by John.Michael.Kane on 2007-10-10
> **Saubazi said:**
> Hmmm... w64codecs - I have medibuntu but there is no package like that. (That is in edgy...)
Did not know that 64bit mplayer can nowadays manage without...anyway vlc can do it as well but the issue is more complex than that...
Once you learn to do things one way that works you don't check every now and then whether another way might already work, right?
Maybe that works for you,however. learning anything is not a onetime process. 

There will always be new methods to doing anything, and as a end user one must be able to make use of those methods. By doing it the way you have a end user would miss out on new, and possibly easier ways to handle issues that may have plague them in the past.

> **Saubazi said:**
> Principally it starts with 32bit browser since I suppose there is no 64bit flash there, now is there? (or did I miss that too) and I suppose one wants to combine a sort of mplayer with mediaplayer connectivity? (My possibly other misconseption is that for a 32bit browser I also need a 32bit player?)
As for mplayer yes theres a native 64bit version in the Edgy-Gutsy64 repos
[http://packages.ubuntu.com/edgy/graphics/mplayer](http://packages.ubuntu.com/edgy/graphics/mplayer)
And here is the plugin which works with the native firefox included in Edgy-Gutsy64
[http://packages.ubuntu.com/edgy/misc/mozilla-mplayer](http://packages.ubuntu.com/edgy/misc/mozilla-mplayer)

Flash can had under Dapper-Feisty 64bit 
This script will install the nspluginwrapper, and Flash for your 64bit browser for Dapper, Edgy and Feisty.
[http://ubuntuforums.org/showthread.php?t=476924](http://ubuntuforums.org/showthread.php?t=476924)

Note: under Gutsy64 the above script should not be needed.

> **Saubazi said:**
> Don't tell me that totem is also more than useless in 64bit environment and can show more films than errors? :)
No one will argue that totem might need work,however. under most circumstances totem does what is needed. No program is perfect.

That said most uses lean toward mplayer, and vlc

---

