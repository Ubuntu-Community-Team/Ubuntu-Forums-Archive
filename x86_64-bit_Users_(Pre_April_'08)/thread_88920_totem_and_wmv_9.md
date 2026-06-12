---
title: "totem and wmv 9"
date: 2005-11-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by Snodgrass on 2005-11-11
Could someone help me with the following error message I get from Totem when trying to open a *.wmv file? It's not any wmv file, because there's another in the same series -- shot earlier, I think --  that works fine. 
[B]
Video codec 'Windows Media Video 9' is not handled. You might need to install additional plugins to be able to play some types of movies[/B]

Thanks,

Snod

---

### Post by jon_gunnar on 2005-11-11
[QUOTE=Snodgrass]Could someone help me with the following error message I get from Totem when trying to open a *.wmv file? It's not any wmv file, because there's another in the same series -- shot earlier, I think --  that works fine. 
[B]
Video codec 'Windows Media Video 9' is not handled. You might need to install additional plugins to be able to play some types of movies[/B]

Thanks,

Snod[/QUOTE]
As I understand it, wmv9 files wont run under amd64. Older formats is ok.

---EDIT---
At last I took the time to compile vlc from the source. Fast and painless operation really, and it works flawlessly.

---

### Post by RAOF on 2005-11-12
If you're prepared to build-from-source, it should be possible to follow [these instructions]("http://nanocrew.net/2005/09/01/compiling-vlc/") to build a WMV9-enabled VLC

---

### Post by stfu on 2005-11-13
[QUOTE=RAOF]If you're prepared to build-from-source, it should be possible to follow [these instructions]("http://nanocrew.net/2005/09/01/compiling-vlc/") to build a WMV9-enabled VLC[/QUOTE]
VC1_reference_decoder_release6.zip file is nowhere to be found. Did someone happen to save it? :)

---

### Post by pelle.k on 2005-12-27
I found vc1 [here]("http://multimedia.cx/eggs/?p=129")

I am using xfce, but i dont know if that is why i had to apt-get libxext-dev and gettext to compile though...

Works great :) . no problems viewing wmv video. but i do miss my OpenGL output though :( (every output method except OpenGL pixelates the picture)
suggestions?

---

### Post by bonzodog on 2005-12-27
I'm using mplayers plugin instructions found here:

[http://www.ubuntuforums.org/showthread.php?t=76946](http://www.ubuntuforums.org/showthread.php?t=76946)

Mplayer is good with .wmv on 64 bit, and will install the w32 codecs just by following those instructions.

---

### Post by giamax on 2005-12-28
[QUOTE=Snodgrass]Could someone help me with the following error message I get from Totem when trying to open a *.wmv file? It's not any wmv file, because there's another in the same series -- shot earlier, I think --  that works fine. 
[B]
Video codec 'Windows Media Video 9' is not handled. You might need to install additional plugins to be able to play some types of movies[/B]

Thanks,

Snod[/QUOTE]

To enable playback of .wmv and some other filetypes through Totem, follow these steps:
1. Add ***gstreamer0.8-ffmpeg*** and ***gstreamer0.8-pitfdll*** packages from Universe branch of repository
2. Download "Windows all" codecs package from mplayerhq.hu
3. Put all files from this package to /usr/lib/win32 (I mean really FILES, not the folder that is inside the archive)

NOTE: This will not guarantee the smooth playback of "absolutely any" wmv-file. It will Just allow GStreamer to load windows .dll's to decode the video stream.

---

### Post by DancingSun on 2006-01-10
[QUOTE=bonzodog]I'm using mplayers plugin instructions found here:

[http://www.ubuntuforums.org/showthread.php?t=76946](http://www.ubuntuforums.org/showthread.php?t=76946)

Mplayer is good with .wmv on 64 bit, and will install the w32 codecs just by following those instructions.[/QUOTE]
How did you get it to work?  I tried installing "mplayer" and "mplayer-amd64", both will crash when I play wmv9 files.  I had the windows codecs copied to /usr/lib/win32.

---

### Post by DancingSun on 2006-01-10
[QUOTE=giamax]To enable playback of .wmv and some other filetypes through Totem, follow these steps:
1. Add ***gstreamer0.8-ffmpeg*** and ***gstreamer0.8-pitfdll*** packages from Universe branch of repository
2. Download "Windows all" codecs package from mplayerhq.hu
3. Put all files from this package to /usr/lib/win32 (I mean really FILES, not the folder that is inside the archive)

NOTE: This will not guarantee the smooth playback of "absolutely any" wmv-file. It will Just allow GStreamer to load windows .dll's to decode the video stream.[/QUOTE]
Unfortunately, gstreamer0.8-pitfdll is only available for i386 and not the AMD64 version of Ubuntu.

---

### Post by giamax on 2006-01-11
[QUOTE=DancingSun]Unfortunately, gstreamer0.8-pitfdll is only available for i386 and not the AMD64 version of Ubuntu.[/QUOTE]

Correct. This would be the next task for package developer/maintainer :)

---

### Post by radiobuzzer on 2006-10-23
Hey!!! Any news about AMD64 support on WMV? It's already been a year and I still can't play wmv 9 files.

---

### Post by Kilz on 2006-10-24
> **radiobuzzer said:**
> Hey!!! Any news about AMD64 support on WMV? It's already been a year and I still can't play wmv 9 files.

I suggest always looking at Sticky: [How to get specific programs to run under Dapper Drake 64-bit edition]("http://www.ubuntuforums.org/showthread.php?t=191205") whenever you have a problem. This can be found there.

Mplayer W32codecs - Mplayer works fine, but to use the W32codecs which include WMV9 support, you need to use a 32bit Mplayer with 32bit libraries. A guide how to do this is found in this thread: ['http://www.ubuntuforums.org/showthread.php?t=188974']("http://www.ubuntuforums.org/showthread.php?t=188974")

It will play all wmv 9 files that Linux can play. It wont play every wmv file, the reason is that wmv is a windows codec from Microsoft. They allow drm in some of the files and Linux cant use them.

---

### Post by kuja on 2006-10-24
Mplayer32 works great in Dapper, but it doesn't work in Edgy, however:

The MPlayer Release Candidate (64-bit) works great.
I've been informed that the VLC (64-bit) in the Edgy Universe repository has support for WMV9  & friends too.

It works in the more current MPlayer, Xine, and VLC releases because FFMPEG, upon which all three of them are built, solved the basic problem with using 32-bit codecs in a 64-bit player.

---

### Post by RAOF on 2006-10-25
> **kuja said:**
> ...
It works in the more current MPlayer, Xine, and VLC releases because FFMPEG, upon which all three of them are built, solved the basic problem with using 32-bit codecs in a 64-bit player.

Actually, no.  FFmpeg got a native, open-source VC-1 decoder, because Microsoft published the specs for VC-1 in order to have it accepted as one of the compression formats for next-gen DVDs.  Fortunately, a VC-1 decoder can **also** decode WMV3/Window Media 9 files, so there's now an open-source wmv decoder.

---

### Post by kuja on 2006-10-25
That's what I get for jumping to conclusions/misreading things others say and assuming.
[color=green]****kuja looks around outside for flying pigs****[/color]

---

### Post by radiobuzzer on 2006-10-25
I managed to work with wmv in 64bit by using these instructions:

[http://ubuntuforums.org/showthread.php?t=140565&highlight=wmv+9+amd64](http://ubuntuforums.org/showthread.php?t=140565&highlight=wmv+9+amd64)

---

