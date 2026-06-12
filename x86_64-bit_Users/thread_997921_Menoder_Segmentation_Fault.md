---
title: "Menoder Segmentation Fault"
date: 2008-11-30
forum: x86 64-bit Users
---

### Post by hocmin on 2008-11-30
I was trying to follow [this post]("http://ubuntuforums.org/showthread.php?t=820865") to play around with stop animation but keep getting the following error:

> mencoder "mf://*.jpg" -ovc lavc -fps 20 -o x.avi
MEncoder 2:1.0~rc2-0ubuntu13 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     E8400  @ 3.00GHz (Family: 6, Model: 23, Stepping: 6)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
success: format: 16  data: 0x0 - 0x0
MF file format detected.
[mf] search expr: *.jpg
[mf] number of files: 286 (2288)
[demux_mf] file type was not set! trying 'type=jpg'...
VIDEO:  [IJPG]  0x0  24bpp  25.000 fps    0.0 kbps ( 0.0 kbyte/s)
[V] filefmt:16  fourcc:0x47504A49  size:0x0  fps:25.00  ftime:=0.0400
Input fps will be interpreted as 20.00 instead.
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffmjpeg] vfm: ffmpeg (FFmpeg MJPEG decoder)
==========================================================================
VDec: vo config request - 3008 x 2000 (preferred colorspace: Planar 422P)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
VDec: using Planar 422P as output csp (no 1)
Movie-Aspect is undefined - no prescaling applied.
SwScaler: reducing / aligning filtersize 1 -> 4
SwScaler: reducing / aligning filtersize 1 -> 4
SwScaler: reducing / aligning filtersize 1 -> 1
SwScaler: reducing / aligning filtersize 9 -> 8
[swscaler @ 0xdd9330]SwScaler: BICUBIC scaler, from yuv422p to yuv420p using MMX2
[swscaler @ 0xdd9330]SwScaler: using 4-tap MMX scaler for horizontal luminance scaling
[swscaler @ 0xdd9330]SwScaler: using 4-tap MMX scaler for horizontal chrominance scaling
[swscaler @ 0xdd9330]SwScaler: using 1-tap MMX "scaler" for vertical scaling (YV12 like)
[swscaler @ 0xdd9330]SwScaler: 3008x2000 -> 3008x2000
videocodec: libavcodec (3008x2000 fourcc=34504d46 [FMP4])
Segmentation fault

Can anyone tell me why this is happening?  Am I not specifying the right command line arguments or is there something improperly configured on my system?

Thanks for any help.

---

### Post by lukyluke on 2009-05-01
It looks like the driver does not support the size of your pictures.
You should resize them before trying to mount them on a movie for example to 800x600
Regards

---

