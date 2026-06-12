---
title: "Mplayer 32bit 1.0rc1"
date: 2006-11-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by Krakatos on 2006-11-01
I am in need of installing Mplayer 1.0rc1 32bit on my Ubuntu 64bit, due to my intensive use of files encoded with h264 video. I did read, in fact, that much progress has been made in the release candidate. At the same time, I need the windows codecs, hence the 32bit version. I did try to compile it myself in 32bit, but it seems like it's a little beyond my current skills....

So, I'd like to ask if someone can provide by chance a link to a working package, as well as any eventual instruction needed for installation. Thanks in advance to anyone who will help me.

---

### Post by kleeman on 2006-11-01
The rc version is much improved on the 64bit side I understand. I tried wmv 9 files successfully at least. If you want to try that I have compiled it and there is a deb here:

[http://www.yourfilelink.com/get.php?fid=203462](http://www.yourfilelink.com/get.php?fid=203462)

---

### Post by Krakatos on 2006-11-01
> **kleeman said:**
> The rc version is much improved on the 64bit side I understand. I tried wmv 9 files successfully at least. If you want to try that I have compiled it and there is a deb here:

[http://www.yourfilelink.com/get.php?fid=203462](http://www.yourfilelink.com/get.php?fid=203462)

I installed it but when I click try to open it, either from the menu or on a file with right-click->Open with, it won't start. Hmm.. Any ideas? Thanks again anyway.

EDIT: this is the error output from terminal 
CPU: AMD Athlon(tm) 64 Processor 3200+ (Family: 15, Model: 4, Stepping: 8)
3DNow supported but disabled
3DNowExt supported but disabled
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2
Xlib:  extension "XFree86-VidModeExtension" missing on display ":1.0".
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
Xlib:  extension "XFree86-VidModeExtension" missing on display ":1.0".
[skin] file ( /usr/local/share/mplayer/skins/default/skin ) not found.
Skin not found (default).

Using Xgl + Beryl, if that helps

---

### Post by kleeman on 2006-11-01
Looks like some kind of X issue from your error messages. I have an nvidia card with beryl extensions installed which perhaps my compile sucked up. Does the regular mplayer from the edgy repo work at all?

---

### Post by Krakatos on 2006-11-01
> **kleeman said:**
> Looks like some kind of X issue from your error messages. I have an nvidia card with beryl extensions installed which perhaps my compile sucked up. Does the regular mplayer from the edgy repo work at all?

Errm... it did work before... now I reinstalled from the official repos and it says 
Requested audio codec family [mp3] (afm=mp3lib) not available. Enable at compilation

---

### Post by kleeman on 2006-11-01
Have a look at this thread it seems relevant to your problem:

[http://forums.fedoraforum.org/forum/showthread.php?t=126758](http://forums.fedoraforum.org/forum/showthread.php?t=126758)

---

### Post by kuja on 2006-11-01
The problem is right under your noses:
> Skin not found (default).

There is no skin installed.

---

### Post by Krakatos on 2006-11-01
> **kuja said:**
> The problem is right under your noses:


There is no skin installed.

Well, I did have the mplayer-skin package from the repos installed. If I need a particular one .. I'm quite confused now... And I mean... something must have gone bad, cause after reinstalling the one from the repos It's not working well anymore, as I said. Before it did..

---

### Post by kleeman on 2006-11-01
Well I don't get that error with that package installed. Maybe something is screwed in your config file. Checkout one of the mplayer howtos on the forum. I remember one told you how to fix skins....

---

### Post by RAOF on 2006-11-02
There's a 64bit build of mplayer 1.0rc1 in my repository, section multimedia.  Check out the sig :)

---

### Post by Krakatos on 2006-11-02
> **RAOF said:**
> There's a 64bit build of mplayer 1.0rc1 in my repository, section multimedia.  Check out the sig :)

My thanks! Installing from your repos everything works fine :)
Now I'm off for some serious testing :)

---

### Post by Fedcer on 2006-11-19
Hi, I'm trying to install mplayer from RAOF's repository but I'm getting this error:
```

Unpacking libavutil (from .../libavutil_3%3asvn-r6847-0raof1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libavutil_3%3asvn-r6847-0raof1_amd64.deb (--unpack):
 trying to overwrite `/usr/lib/libavutil.so.49', which is also in package libavcodec
Unpacking mplayer-skin-blue (from .../mplayer-skin-blue_1.5-0.5_all.deb) ...
dpkg: error processing /var/cache/apt/archives/mplayer-skin-blue_1.5-0.5_all.deb (--unpack):
 trying to overwrite `/usr/share/mplayer/Skin', which is also in package mplayer-skins

```

any idea ?

thanks,

Fedcer

---

### Post by RAOF on 2006-11-19
> **Fedcer said:**
> Hi, I'm trying to install mplayer from RAOF's repository but I'm getting this error:
```

Unpacking libavutil (from .../libavutil_3%3asvn-r6847-0raof1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libavutil_3%3asvn-r6847-0raof1_amd64.deb (--unpack):
 trying to overwrite `/usr/lib/libavutil.so.49', which is also in package libavcodec
Unpacking mplayer-skin-blue (from .../mplayer-skin-blue_1.5-0.5_all.deb) ...
dpkg: error processing /var/cache/apt/archives/mplayer-skin-blue_1.5-0.5_all.deb (--unpack):
 trying to overwrite `/usr/share/mplayer/Skin', which is also in package mplayer-skins

```

thanks,

Fedcer

Ok, I thought I'd fixed the second one.  Basically, you should be able to fix the second one by removing "mplayer-skins" first (but I thought I'd added it to the "conflicts" list.)

The first (libavcodec) problem.  Hmmm.  Where did you get that libavcodec package?  As far as I can tell, the one in my repository shouldn't give you that message (it doesn't contain libavutil.so.*), and it **should** have a higher version number, and hence automatically replace any other version on your system.  What does "aptitude show libavcodec" tell you?

---

### Post by RAOF on 2006-11-20
Ok, try it again now.  I think that should have fixed everything.

---

### Post by Fedcer on 2006-11-20
Thanks, now ffmpeg and it's dependencies install fine, but I'm gettins this when trying to install mplayer:
```

Get:1 http://ubuntu.systemadministrator.org edgy/all mplayer-skin-blue 1.5-0.5 [224kB]
Get:2 http://ubuntu.systemadministrator.org edgy/all mplayer 2:1.0-rc1-0.0raof1 [4541kB]
Fetched 4765kB in 43s (111kB/s)
Failed to fetch http://ubuntu.systemadministrator.org/pool/edgy/multimedia/mplayer-skin-blue_1.5-0.5_all.deb  Size mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```
I tried running apt-get update again but it still throws that error.

---

### Post by RAOF on 2006-11-20
Ok.  I'll just need to regenerate the repository.  Should be fixed soon.

---

### Post by Fedcer on 2006-11-20
Thank you! Everything works fine now.

---

### Post by benrboone on 2006-11-22
I have install mplayer 32bit 1.0rc1 and i can play file by using terminal and the path and or file name but it dosn't show up in any menus and right clicking on a file give me the option to use mplayer but a window flashes open and then closes before i can read the message here are the errors given me when i play the file using mplayer in terminal

ben@ben:~$ mplayer ts.wmv
MPlayer 1.0rc1-4.1.2 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ (Family: 15, Model: 43, Stepping: 1)
3DNow supported but disabled
3DNowExt supported but disabled
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing ts.wmv.
ASF file format detected.
VIDEO:  [WMV3]  300x200  24bpp  29.970 fps    0.0 kbps ( 0.0 kbyte/s)
Clip info:
 name: 
 author: 
 copyright: 
 comments: 
Xlib:  extension "XFree86-VidModeExtension" missing on display ":0.0".
==========================================================================
Requested video codec family [wmv9dmo] (vfm=dmo) not available.
Enable it at compilation.
Requested video codec family [wmvdmo] (vfm=dmo) not available.
Enable it at compilation.
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffwmv3] vfm: ffmpeg (FFmpeg M$ WMV3/WMV9)
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 64.0 kbit/4.17% (ratio: 8004->192000)
Selected audio codec: [ffwmav2] afm: ffmpeg (DivX audio v2 (FFmpeg))
==========================================================================
[AO OSS] audio_setup: Can't open audio device /dev/dsp: Device or resource busy
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 300 x 200 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 300x200 => 300x200 Planar YV12 
New_Face failed. Maybe the font path is wrong.
Please supply the text font file (~/.mplayer/subfont.ttf).
subtitle font: load_sub_face failed.
No bind found for key 'MOUSE_BTN2'.                         0.4% 0 0 
No bind found for key 'MOUSE_BTN2'.                         0.4% 0 0 
No bind found for key 'MOUSE_BTN2'.                         0.4% 0 0 
No bind found for key 'MOUSE_BTN0'.                         0.4% 0 0 
A: 165.9 V: 165.9 A-V:  0.007 ct: -0.043 4336/4336  3%  0%  0.4% 0 0 

Exiting... (End of file)
ben@ben:~$ 
](*,)

---

### Post by RAOF on 2006-11-22
None of those appear to actually be errors.  mplayer seems to think it's playing the file correctly all the way through, then exiting.  Can you try playing the file in some other player (which will probably have to be on Windows, sadly)?  Is the file itself OK?

---

### Post by benrboone on 2006-11-22
The file does play all the way through my real problem is that i can't play files by right clicking and selecting mplayer it refuses to play that way although a small screen flashes open for a tenth of a second and then closes with out anything else happening

---

### Post by benrboone on 2006-11-23
Thanks for all your help have finally figured it out! Mplayer is working great:)

---

### Post by RAOF on 2006-11-23
Could you post what the actual solution was, just incase someone else has the same problem?

---

### Post by Krakatos on 2006-11-25
I think there might be a small problem with your repo.
The following packages have unmet dependencies:
  mplayer: Depends: mplayer-skin
E: Broken packages

Note that  I did install mplayer-skins

Could this be an error due to naming? Like.. a missing s?

---

### Post by RAOF on 2006-11-25
A temporary solution would be to install the **mplayer-blue** package, which provides **mplayer-skin**.

For a better fix, I'll need to fix up the packages :(.

---

### Post by gratefulfrog on 2006-11-29
Another choice is to download the sources from here:
[http://www.mplayerhq.hu/design7/news.html]("http://www.mplayerhq.hu/design7/news.html")

Then build it yourself for amd64 target. If you do this, be careful to set the options to configure properly, in particular the paths to librairies and codecs, and to scan the default options to see if they're right for your system, enable the gui (gmplayer) for example.

This will build perfectly on amd64 if you have all the librairies. If you don't it will complain and you can get them via synaptic at the ubuntu reps.

Use of "checkinstall" will create a .deb package which you can document and which will be removable just like any other one (synaptic, or dpkg -r).

It's EXTREMELY easy to build and install mplayer from source.

Good luck,
GF.

---

### Post by benrboone on 2006-12-01
I had not setup any gui to use mplayer.  I already had kplayer install so i just enabled mplayer in it.:)

---

