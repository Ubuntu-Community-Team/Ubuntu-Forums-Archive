---
title: "Audio Sync"
date: 2006-01-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by DaveHope on 2006-01-20
Hello all,

I re-encode all my DVDs into avi files so as to prevent having to dig out the DVD whenever I want to watch a film (noisy DVD drive).

I previously used Gentoo and had no problems playing these back (I don't recall having problems back in Debian before that either). Anyway, in Ubuntu audio for some films is out of sync. Usually by a fraction of a second, but that's enough to get really annoying (seeing gunshots before you hear them. I know light travels faster than sound, but the effect isn't that great over a few meters :P)

These files seem to play fine on my laptop (which doesn't have a dvd drive, shame, it's a nice laptop otherwise).

Does anybody have any ideas as to how I can solve this ? I realise I can tweak the sound offset manually, but the audio is fine in the file. It just plays back out of sync in Xine and mplayer. I doubt this is going to help, as it seems fairly normal, but here's my mplayer output:

> MPlayer dev-CVS--4.0.2 (C) 2000-2005 MPlayer Team
CPU: Advanced Micro Devices  (Family: 8, Stepping: 0)
Detected cache-line size is 64 bytes
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 3DNow 3DNowEx SSE SSE2

86 audio & 200 video codecs
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0 : No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing /mnt/DVD/eXistenZ.avi.
AVI file format detected.
VIDEO:  [DX50]  512x276  24bpp  25.000 fps  669.4 kbps (81.7 kbyte/s)
==========================================================================
Trying to force audio codec driver family libmad...
Opening audio decoder: [liba52] AC3 decoding with liba52
No accelerated IMDCT transform found
AC3: 5.1 (3f+2r+lfe)  48000 Hz  384.0 kbit/s
No accelerated resampler found
AUDIO: 48000 Hz, 2 ch, s16le, 384.0 kbit/25.00% (ratio: 48000->192000)
Selected audio codec: [a52] afm:liba52 (AC3-liba52)
==========================================================================
vo: X11 running at 1280x1024 with depth 24 and 32 bpp (":0.0" => local display)
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm:ffmpeg (FFmpeg MPEG-4)
==========================================================================
Building audio filter chain for 48000Hz/2ch/s16le -> 0Hz/0ch/??...
alsa-init: 1 soundcard found, using: default
alsa: 48000 Hz/2 channels/4 bpf/65536 bytes buffer/Signed 16 bit Little Endian
AO: [alsa] 48000Hz 2ch s16le (2 bps)
Building audio filter chain for 48000Hz/2ch/s16le -> 48000Hz/2ch/s16le...
Starting playback...
VDec: vo config request - 512 x 276 (preferred csp: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.86:1 - prescaling to correct movie aspect.
VO: [x11] 512x276 => 512x276 Planar YV12
SwScaler: using unscaled Planar YV12 -> BGRA special converter
New_Face failed. Maybe the font path is wrong. 2 ??% ??% ??,?% 0 0 96%
Please supply the text font file (~/.mplayer/subfont.ttf).
subtitle font: load_sub_face failed.
alsa-uninit: pcm closed 0.001 ct:  0.002  29/ 29  7%  4%  0.9% 0 0 88%

Any suggestions would be greatly appreciated. Having to walk upstairs and find the DVD on the shelf is really starting to get annoying. Not to mention the noise from my cheapo DVD player :(

---

### Post by FluffyElmo on 2006-01-20
Try changing your default audio sink? *System->Preferences->Multimedia Systems Selector* 

I had some games audio problems that were fixed by switching to ESD. You might also try installing VLC, but it's probably not a player issue.

---

### Post by DaveHope on 2006-01-21
Alas no. Still out of sync.

---

