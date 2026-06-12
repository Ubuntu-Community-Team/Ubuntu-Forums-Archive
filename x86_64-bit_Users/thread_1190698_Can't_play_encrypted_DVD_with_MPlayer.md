---
title: "Can't play encrypted DVD with MPlayer"
date: 2009-06-18
forum: x86 64-bit Users
---

### Post by tom17 on 2009-06-18
Hi,

I have searched for this on the forums and all I can find is posts telling people to install libdvdcss etc and then it works for them. This is not the case for me...

Info:
Jaunty 64bit
/etc/apt/sources.list.d/medibuntu.list - deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free #Medibuntu - Ubuntu 9.04 "jaunty jackalope"
libdvdcss2 - Version: 1.2.10-0.2medibuntu1
libdvdread4 - Version: 4.1.3-4ubuntu2
mplayer-nogui - Version: 2:1.0~rc2-0ubuntu19+medibuntu1 (Same result with gmplayer)

When playing a non-encrypted DVD title, it works fine. When playing an encrypted title, it hangs...

```
$ /usr/bin/mplayer dvd://1
MPlayer 1.0rc2-4.3.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 CPU          6420  @ 2.13GHz (Family: 6, Model: 15, Stepping: 6)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing dvd://1.
There are 47 titles on this DVD.
There are 8 chapters in this DVD title.
There are 1 angles in this DVD title.
audio stream: 0 format: ac3 (stereo) language: en aid: 128.
audio stream: 1 format: ac3 (stereo) language: fr aid: 129.
audio stream: 2 format: ac3 (stereo) language: es aid: 130.
number of audio channels on disk: 3.
number of subtitles on disk: 0
MPEG-PS file format detected.
```
At which point it hangs...

I have another build of mplayer on my system ( I think I compiled it from SVN for AVCHD support, although it does not have the correct video drivers) and this version clearly calls on libdvdread to get the css decryption going.

```
/usr/local/bin/mplayer dvd://1
MPlayer SVN-r28932-4.3.2 (C) 2000-2009 MPlayer Team

Playing dvd://1.
libdvdread: Using libdvdcss version 1.2.10 for DVD access
There are 47 titles on this DVD.
There are 1 angles in this DVD title.

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x000001c0
libdvdread: Elapsed time 0

<snip>

libdvdread: Get key for /VIDEO_TS/VTS_34_1.VOB at 0x0017cc7f
libdvdread: Elapsed time 0
libdvdread: Found 34 VTS's
libdvdread: Elapsed time 0
audio stream: 0 format: ac3 (stereo) language: en aid: 128.
audio stream: 1 format: ac3 (stereo) language: fr aid: 129.
audio stream: 2 format: ac3 (stereo) language: es aid: 130.
number of audio channels on disk: 3.
number of subtitles on disk: 0
MPEG-PS file format detected.


MPlayer interrupted by signal 2 in module: demux_open
MPEG: No audio stream found -> no sound.
VIDEO:  MPEG2  720x480  (aspect 2)  29.970 fps  9800.0 kbps (1225.0 kbyte/s)
Can't open /dev/fb0: No such file or directory
[fbdev2] Can't open /dev/fb0: No such file or directory
```
etc...

I have tried re-installing libcss, libdvdread and mplayer in various orders to try to get the official mplayer to pick up libdvdread but it just doesn't seem to. Am I meant to do something to get mplayer to call to libdvdread?

libdvdread and libdvdcss are functioning correctly as I the title can be read by VLC, xine, transcode etc.

Help :)

Tom...

---

### Post by philinux on 2009-06-18
All I did on my rig was to follow the medibuntu instructions and install ubuntu-restricted-extras. 

Even totem will play commercial dvd's. I'm at a loss to suggest a way forward. In the past I've only used vlc but totem now even has the menus sorted.

---

