---
title: "VC1 (WVC1) video"
date: 2009-06-19
forum: x86 64-bit Users
---

### Post by Xebec on 2009-06-19
Did not expect I would be asking this question in 9.04, but I really have no player installed that supports VC1 in year 2009! And that freaks me out. I have tried VLC, mplayer, Totem, Dragon - none of them is able to play VC1 video. I have medibuntu repositary installed, w64codecs, gstreamer-bad and gstraemer-ugly. No help. The best result can be seen in VLC - at leats it plays the audiostreams from the video. Video is 100% not corrupt - plays in Windows. What the hell, Ubuntu?

---

### Post by Xebec on 2009-06-19
It seems that VC1 is working fine in WMV, but fails in MKV container. Anybody solved the same problem?

---

### Post by andrew.46 on 2009-06-19
Hi Xebec,

> **Xebec said:**
> Did not expect I would be asking this question in 9.04, but I really have no player installed that supports VC1 in year 2009!

An up to date MPlayer should be able to play these files. There is both an external *32bit *codec for  MPlayer:

```
andrew@skamandros~$ mplayer -vc help | grep VC-1
wmvvc1dmo   dmo       working   Windows Media Video (VC-1) Advanced Profile  [**[COLOR="Purple"]wvc1dmod.dll[/COLOR]**]
```

as well as the results from one of the Google Summer of Code projects which is available for *64bit* as well, unlike the codec which is 32bit only:

```
andrew@skamandros~$ mplayer -vc help | grep VC1
**[COLOR="Purple"]ffvc1[/COLOR]**       ffmpeg    problems  FFmpeg WVC1  [vc1]
**[COLOR="Purple"]ffvc1vdpau[/COLOR]**  ffmpeg    problems  FFmpeg WVC1 (VDPAU)  [vc1_vdpau]
```

Yes, I saw the 'problems' section as well so I took the time to download a sample file:

```
wget http://samples.mplayerhq.hu/V-codecs/WVC1/Test_1440x576_WVC1_6Mbps.wmv
```

and tested this with both (ffvc1vdpau is no good to me as I do not use vdpau). The windows codec played well enough:

```

andrew@skamandros~/Desktop$ mplayer Test_1440x576_WVC1_6Mbps.wmv 
MPlayer SVN-r29371-4.2.4 (C) 2000-2009 MPlayer Team

Playing Test_1440x576_WVC1_6Mbps.wmv.
ASF file format detected.
[asfheader] Video stream found, -vid 1
VIDEO:  [WVC1]  1440x576  24bpp  1000.000 fps  6000.0 kbps (732.4 kbyte/s)
==========================================================================
Opening video decoder: [dmo] DMO video codecs
DMO dll supports VO Optimizations 0 1
DMO dll might use previous sample when requested
Decoder supports the following formats: YV12 YUY2 UYVY YVYU RGB8 RGB555 RGB565 RGB24 RGB32 
Decoder is capable of YUV output (flags 0x1b)
VDec: vo config request - 1440 x 576 (preferred colorspace: Packed YUY2)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 2.50:1 - prescaling to correct movie aspect.
VO: [xv] 1440x576 => 1440x576 Planar YV12 
**[COLOR="Purple"]Selected video codec: [wmvvc1dmo] vfm: dmo (Windows Media Video (VC-1) Advanced Profile)[/COLOR]**
==========================================================================
Audio: no sound
Starting playback...
V:  63.0 1450/1450 32%  4%  0.0% 0 0 

Exiting... (End of file)

```

but I guess this will not be available to you with a 64bit installation. I tried also with the SOC offering:

```

andrew@skamandros~/Desktop$ mplayer **[COLOR="Purple"]-vc ffvc1[/COLOR]** Test_1440x576_WVC1_6Mbps.wmv 
MPlayer SVN-r29371-4.2.4 (C) 2000-2009 MPlayer Team

Playing Test_1440x576_WVC1_6Mbps.wmv.
ASF file format detected.
[asfheader] Video stream found, -vid 1
VIDEO:  [WVC1]  1440x576  24bpp  1000.000 fps  6000.0 kbps (732.4 kbyte/s)
==========================================================================
[B][COLOR="Purple"]Forced video codec: ffvc1
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffvc1] vfm: ffmpeg (FFmpeg WVC1)[/COLOR][/B]
==========================================================================
Audio: no sound
Starting playback...
VDec: vo config request - 1440 x 576 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 2.50:1 - prescaling to correct movie aspect.
VO: [xv] 1440x576 => 1440x576 Planar YV12 
V:  63.0 1450/1450 28%  4%  0.0% 0 0 

Exiting... (End of file)

```

and this worked perfectly as well, although I have a suspicion that windows codec played it a little better and this pains me a little to say :-). Just to prove I have no life I used FFmpeg to place the VC1 video in a Matroska container and this played back with no problems:

```

andrew@skamandros~/Desktop$ **[COLOR="Purple"]mplayer -vc ffvc1 test.mkv [/COLOR]**
MPlayer SVN-r29371-4.2.4 (C) 2000-2009 MPlayer Team

Playing test.mkv.
[mkv] Track ID 1: video (V_MS/VFW/FOURCC), -vid 0
[mkv] Will play video track 1.
[mkv] No audio track found/wanted.
Matroska file format detected.
VIDEO:  [WVC1]  1440x576  24bpp  25.000 fps    0.0 kbps ( 0.0 kbyte/s)
==========================================================================
Forced video codec: ffvc1
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffvc1] vfm: ffmpeg (FFmpeg WVC1)
==========================================================================
Audio: no sound
Starting playback...
VDec: vo config request - 1440 x 576 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 2.50:1 - prescaling to correct movie aspect.
VO: [xv] 1440x576 => 1440x576 Planar YV12 
V:   0.0   0/  0 ??% ??% ??,?% 0 0 

Exiting... (End of file)

```

although I am not at all certain if a Matroska container would *normally* hold such a file. The answer, as always, seems to be MPlayer :-).

Andrew

---

### Post by Xebec on 2009-06-20
Thank you Andrew. I tried to reproduce your success and here is what I've got so far:

```

$ mplayer -vc help | grep VC1

ffvc1       ffmpeg    problems  FFmpeg WVC1  [vc1]
ffvc1vdpau  ffmpeg    problems  FFmpeg WVC1 (VDPAU)  [vc1_vdpau]

```

The same codecs are listed despite 64-bit system.

Here are my both tries:

```
$ mplayer -vc ffvc1 test.mkv
MPlayer SVN-r29352-4.3.3 (C) 2000-2009 MPlayer Team
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing test.mkv.
[mkv] Track ID 1: video (V_MS/VFW/FOURCC), -vid 0
[mkv] Track ID 2: audio (A_AC3) "AC3 5.1 448 kbps", -aid 0, -alang rus
[mkv] Track ID 3: audio (A_AC3) "AC3 5.1 448 kbps", -aid 1, -alang eng
[mkv] Track ID 4: subtitles (S_TEXT/UTF8), -sid 0, -slang rus
[mkv] Track ID 5: subtitles (S_TEXT/***), -sid 1, -slang eng
[mkv] Will play video track 1.
Matroska file format detected.
VIDEO:  [WVC1]  1920x1080  0bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: No such file or directory.
[VO_3DFX] Unable to open /dev/3dfx.
==========================================================================
Forced video codec: ffvc1
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
[vc1 @ 0xd697c0]Incomplete extradata
Could not open codec.
VDecoder init failed :(
Cannot find codec matching selected -vo and video format 0x31435657.
==========================================================================
==========================================================================
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 448.0 kbit/29.17% (ratio: 56000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
AO: [oss] 48000Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:   5.7 (05.7) of 3070.0 (51:10.0)  0.5% 

MPlayer interrupted by signal 2 in module: play_audio
A:   5.8 (05.7) of 3070.0 (51:10.0)  0.5% 
Exiting... (Quit)

```

```
$ mplayer -vc ffvc1vdpau test.mkv
MPlayer SVN-r29352-4.3.3 (C) 2000-2009 MPlayer Team
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing test.mkv.
[mkv] Track ID 1: video (V_MS/VFW/FOURCC), -vid 0
[mkv] Track ID 2: audio (A_AC3) "AC3 5.1 448 kbps", -aid 0, -alang rus
[mkv] Track ID 3: audio (A_AC3) "AC3 5.1 448 kbps", -aid 1, -alang eng
[mkv] Track ID 4: subtitles (S_TEXT/UTF8), -sid 0, -slang rus
[mkv] Track ID 5: subtitles (S_TEXT/***), -sid 1, -slang eng
[mkv] Will play video track 1.
Matroska file format detected.
VIDEO:  [WVC1]  1920x1080  0bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: No such file or directory.
[VO_3DFX] Unable to open /dev/3dfx.
==========================================================================
Forced video codec: ffvc1vdpau
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
[VD_FFMPEG] Trying pixfmt=0.
Unsupported PixelFormat -1
VDec: vo config request - 1920 x 1080 (preferred colorspace: VC1 VDPAU acceleration)
VDec: using VC1 VDPAU acceleration as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [vdpau] 1920x1080 => 1920x1080 VC1 VDPAU acceleration 
[VD_FFMPEG] XVMC-accelerated MPEG-2.
[VD_FFMPEG] Trying pixfmt=0.
[VD_FFMPEG] XVMC-accelerated MPEG-2.
[vc1_vdpau @ 0xd697c0]Incomplete extradata
Could not open codec.
VDecoder init failed :(
Cannot find codec matching selected -vo and video format 0x31435657.
==========================================================================
==========================================================================
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 448.0 kbit/29.17% (ratio: 56000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
AO: [oss] 48000Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:   3.6 (03.5) of 3070.0 (51:10.0)  0.5% 

MPlayer interrupted by signal 2 in module: play_audio
A:   3.6 (03.6) of 3070.0 (51:10.0)  0.5% 
Exiting... (Quit)

```

Both ffvc1 and ffvc1vdpau work perfectly with WVC1 in WMV, and I see the difference in CPU loads between them (around 75% vs around 25% on the same test video), so they are indeed different decoders. Can I have your successfully working MKV video?

Once again thank you very much for your willing to help!

---

### Post by andrew.46 on 2009-06-20
Hi Xebec,

> **Xebec said:**
> Both ffvc1 and ffvc1vdpau work perfectly with WVC1 in WMV, and I see the difference in CPU loads between them (around 75% vs around 25% on the same test video), so they are indeed different decoders. Can I have your successfully working MKV video?

One of these days I must join the vdpau revolution :-). I have recreated the VC1 conversion of that [same test video]("http://samples.mplayerhq.hu/V-codecs/WVC1/Test_1440x576_WVC1_6Mbps.wmv") using the following syntax:

```
ffmpeg -i Test_1440x576_WVC1_6Mbps.wmv -vcodec copy -sameq vc1_matroska.mkv
```

Playback in MPlayer *only* seems possible, vlc 1.0 rc3 could not play it, which lends support to the idea that this type of video does not *really* belong in a Matroska container. Anyway I have loaded the file onto my website and you can see the results at:

```
wget http://www.andrews-corner.org/samples/vc1_matroska.mkv
```

I note as well that the latest mkvmerge (2.9.5) could not produce a playable matroska file with this VC1 video.

All the best,

Andrew

---

### Post by tenmoi on 2009-06-21
Hi Andrew.

I downloaded your vc1_matroska.mkv and played it with XBMC compiled from svn, but it played with no sound and asked me to play the video file with bla:P from 3dtv.at.

May I ask you if this video is with sound?

Tx.

---

### Post by andrew.46 on 2009-06-21
Hi tenmoi,

> **tenmoi said:**
> I downloaded your vc1_matroska.mkv and played it with XBMC compiled from svn, but it played with no sound and asked me to play the video file with bla:P from 3dtv.at.

May I ask you if this video is with sound?

The video in fact had no sound just the vc1 video stream.

Andrew

---

### Post by tenmoi on 2009-06-22
Tx.

But Why doesn't Xebec try other players? Even mplayer is playing this file (of yours) fine on my Jaunty 64bit. What is this VC1 he's talking about?

---

### Post by andrew.46 on 2009-06-22
Hi tenmoi,

> **tenmoi said:**
>  What is this VC1 he's talking about?

I had not really come across vc1 before but I gather it is yet another Microsoft codec:

VC-1
[http://en.wikipedia.org/wiki/VC-1](http://en.wikipedia.org/wiki/VC-1)

Some implications there for x-box and blue-ray I believe.

Andrew

---

### Post by mc4man on 2009-06-24
I don't think it's an issue of vc1 (wvc1) in mkv, but more how it was done.
for instance here's a sample that plays fine in both vlc and mplayer (though I'd give the edge to a 32 bit mplayer, which uses the dmo by default, vlc uses avcodec,

[http://www.techpowerup.com/downloads/530/HD-DVD_Demo_1080p_VC-1_DDPlus_5.1.html](http://www.techpowerup.com/downloads/530/HD-DVD_Demo_1080p_VC-1_DDPlus_5.1.html)

---

### Post by andrew.46 on 2009-06-24
Hi mc4man,

> **mc4man said:**
>  here's a sample that plays fine in both vlc and mplayer (though I'd give the edge to a 32 bit mplayer, which uses the dmo by default, vlc uses avcodec,

I have not downloaded this sample yet as I seem to have exceeded my download limit for the month but can you see much difference when using *-vc ffvc1* to play these videos rather than the default *wmvvc1dmo*? I have looked at the sample mentioned before a few times and I will confess that I am not entirely sure which gives better playback :-).

All the best,

Andrew

---

### Post by mc4man on 2009-06-25
> can you see much difference when using -vc ffvc1 to play these videos rather than the default wmvvc1dmo? 
Also can't see much diff. in mplayer, the ffvc1 starts with a green screen for a few secs, otherwise can't really say.

also noting that the machine I trying on (laptop) doesn't display full Hd res. so not really a great test. (or opinion

Mplayer does seem to handle better than vlc though starting vlc from the file improved things greatly (r. click on file - open w/ vlc vs. opening the file from vlc

What was interesting was vlc handled this file better than mplayer, though again on the laptop because my desktop (p4) can't handle
[http://www.microsoft.com/downloads/details.aspx?FamilyID=270AEF06-4CA5-4E0C-A116-F7FA721BD6BE&displaylang=en](http://www.microsoft.com/downloads/details.aspx?FamilyID=270AEF06-4CA5-4E0C-A116-F7FA721BD6BE&displaylang=en)

For 64 bit the above type would prove problematic unless decoding of wma3 was switched to avcodec as mentioned in the wmapro  thread. (and possibly for 32 bit in 1.0.0, for next weeks release the odds are the dmo loader will remain half broken

Doing some comparisons of same video in multiple formats makes me think that unless ones display was rather large there's not much to be gained from vc1 (AP) (the mpeg4 hd looks great and plays even on a p4
[http://www.elephantsdream.org/download/](http://www.elephantsdream.org/download/)

(to bad about the dl limits, I tend to forget about that

---

### Post by Arup on 2009-06-25
If I am not mistaken, vc-1 vdpau according to nvidia is only supported by certain 9x series card and 2xx cards, none of the 8 series work for vc-1 vdpau.

---

### Post by AndrewD5554 on 2009-10-05
I had this same issue and found the source of the problem in ffmpeg. I've just submitted a simple patch that allows broken mkv files generated by eac3to to be played in mplayer, or I guess anything else that uses ffmpeg. I can now play my files with both ffvc1vdpau and ffvc1.

---

