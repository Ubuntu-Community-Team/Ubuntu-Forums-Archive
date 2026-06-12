---
title: "Mplayer Error Message for RMVB"
date: 2009-03-17
forum: x86 64-bit Users
---

### Post by lqbdxx on 2009-03-17
I was using mplayer to play a RMVB file.  But the image can not fully ocuppy the player output interface.  And the termial return the following information:
***********************
REAL file format detected.
Stream description: Audio Stream
Stream mimetype: audio/x-pn-realaudio
[real] Audio stream found, -aid 0
Stream description: Video Stream
Stream mimetype: video/x-pn-realvideo
[real] Video stream found, -vid 1
Stream mimetype: logical-fileinfo
VIDEO:  [RV40]  576x324  24bpp  29.000 fps    0.0 kbps ( 0.0 kbyte/s)
Clip info:
 name: &#65533;&#65533;&#1636;
 author: &#65533;&#65533;&#65533;&#65533;&#65533;&#764;
 copyright: &#65533;&#65533;&#65533;&#65533;&#65533;&#764;
 comment: 
===================================================
Opening video decoder: [realvid] RealVideo decoder
ERROR: Could not open required DirectShow codec drvc.dll.
Read the RealVideo section of the DOCS!
VDecoder init failed :(
Opening video decoder: [realvid] RealVideo decoder
ERROR: Could not open required DirectShow codec drv43260.dll.
Read the RealVideo section of the DOCS!
VDecoder init failed :(
Opening video decoder: [realvid] RealVideo decoder
Error: /usr/lib/codecs/drvc.bundle/Contents/MacOS/drvc: cannot open shared object file: No such file or directory
ERROR: Could not open required DirectShow codec drvc.bundle/Contents/MacOS/drvc.
Read the RealVideo section of the DOCS!
VDecoder init failed :(
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffrv40] vfm: ffmpeg (FFmpeg RV40)
==========================================================================
==============================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 22050 Hz, 2 ch, s16le, 44.1 kbit/6.25% (ratio: 5512->88200)
Selected audio codec: [ffcook] afm: ffmpeg (FFmpeg COOK audio)
==============================================================
AO: [oss] 22050Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 576 x 324 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 576x324 => 576x324 Planar YV12 
A: 278.7 V: 278.7 A-V:  0.000 ct: -0.083 8181/8181 14%  1%  0.9% 5 0 
******************
Can anyone help?  Thank you in advance.

---

