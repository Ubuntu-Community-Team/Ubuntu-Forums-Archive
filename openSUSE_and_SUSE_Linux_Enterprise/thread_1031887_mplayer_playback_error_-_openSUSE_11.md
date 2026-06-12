---
title: "mplayer playback error - openSUSE 11"
date: 2009-01-05
forum: openSUSE and SUSE Linux Enterprise
---

### Post by fitlad on 2009-01-05
I run mplayer via gnome terminal, w32codec-all is installed already, and tried to playback realmedia file but the result was sound only. I adjusted the mplayer preference to playback real video codecs but the problem is still exist. checks the following error message pls:

```
fitlad@shell:~> gmplayer
MPlayer dev-SVN-r27637-4.3-openSUSE Linux 11.0 (i686)-Packman (C) 2000-2008 MPlayer Team
CPU: Intel(R) Celeron(R) M CPU        440  @ 1.86GHz (Family: 6, Model: 14, Stepping: 12)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/fitlad/Documents/Multimedia/badboys2.rm
REAL file format detected.
Stream description: Audio Stream
Stream mimetype: audio/x-pn-realaudio
[real] Audio stream found, -aid 0
Stream description: Video Stream
Stream mimetype: video/x-pn-realvideo
[real] Video stream found, -vid 1
Stream mimetype: logical-fileinfo
VIDEO:  [RV40]  320x240  24bpp  30.000 fps    0.0 kbps ( 0.0 kbyte/s)
Clip info:
 comment: 
==========================================================================
Trying to force video codec driver family realvid...
Opening video decoder: [realvid] RealVideo decoder
Error: /usr/lib/RealPlayer10/codecs/drvc.so: cannot open shared object file: No such file or directory
Win32 LoadLibrary failed to load: drvc.so, /usr/lib/codecs/drvc.so, /usr/lib/win32/drvc.so, /usr/local/lib/win32/drvc.so
Error loading dll
ERROR: Could not open required DirectShow codec drvc.so.
Read the RealVideo section of the DOCS!
VDecoder init failed :(
Opening video decoder: [realvid] RealVideo decoder
Win32 LoadLibrary failed to load: drvc.dll, /usr/lib/codecs/drvc.dll, /usr/lib/win32/drvc.dll, /usr/local/lib/win32/drvc.dll
Error loading dll
ERROR: Could not open required DirectShow codec drvc.dll.
Read the RealVideo section of the DOCS!
VDecoder init failed :(
Opening video decoder: [realvid] RealVideo decoder
Error: /usr/lib/RealPlayer10/codecs/drv4.so.6.0: cannot open shared object file: No such file or directory
Win32 LoadLibrary failed to load: drv4.so.6.0, /usr/lib/codecs/drv4.so.6.0, /usr/lib/win32/drv4.so.6.0, /usr/local/lib/win32/drv4.so.6.0
Error loading dll
ERROR: Could not open required DirectShow codec drv4.so.6.0.
Read the RealVideo section of the DOCS!
VDecoder init failed :(
Opening video decoder: [realvid] RealVideo decoder
Win32 LoadLibrary failed to load: drv43260.dll, /usr/lib/codecs/drv43260.dll, /usr/lib/win32/drv43260.dll, /usr/local/lib/win32/drv43260.dll
Error loading dll
ERROR: Could not open required DirectShow codec drv43260.dll.
Read the RealVideo section of the DOCS!
VDecoder init failed :(
Opening video decoder: [realvid] RealVideo decoder
Error: /usr/lib/RealPlayer10/codecs/drvc.bundle/Contents/MacOS/drvc: cannot open shared object file: No such file or directory
Win32 LoadLibrary failed to load: drvc.bundle/Contents/MacOS/drvc, /usr/lib/codecs/drvc.bundle/Contents/MacOS/drvc, /usr/lib/win32/drvc.bundle/Contents/MacOS/drvc, /usr/local/lib/win32/drvc.bundle/Contents/MacOS/drvc
Error loading dll
ERROR: Could not open required DirectShow codec drvc.bundle/Contents/MacOS/drvc.
Read the RealVideo section of the DOCS!
VDecoder init failed :(
Cannot find codec matching selected -vo and video format 0x30345652.
Read DOCS/HTML/en/codecs.html!
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 1 ch, s16le, 20.7 kbit/2.93% (ratio: 2583->88200)
Selected audio codec: [ffcook] afm: ffmpeg (FFmpeg COOK audio decoder)
==========================================================================
AO: [oss] 44100Hz 1ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:   4.9 (04.9) of 4906.0 ( 1:21:46.0)  0.4%                                    

Exiting... (Exit)
fitlad@shell:~> 

```

I appreciate your support to rectify this issue :)

---

### Post by Growbag on 2009-01-08
Not the solution to the problem directly, but maybe install "Realplayer" and see if that works.

It might be the "intentionally crippled by default" build of mplayer too, I've always been told to switch to the packman versions of ALL media players.

Add the packman repo in yast and if you then select the view by repo feature, you can switch to the pacman version for full functionality.

If you still have no joy, maybe consider posting on the opensuse forums ([http://forums.opensuse.org](http://forums.opensuse.org)) instead, you will have a bigger audience than here :).

---

### Post by naiph on 2009-01-21
Hi,

For what it's worth, I fixed the same problem on Fedora Core 9 by installing compat-libstdc++-33 and compat-libstdc++-296.

naiph

---

