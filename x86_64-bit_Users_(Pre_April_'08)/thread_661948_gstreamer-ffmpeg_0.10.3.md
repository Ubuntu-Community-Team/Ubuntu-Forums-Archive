---
title: "gstreamer-ffmpeg 0.10.3"
date: 2008-01-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by Major_Kong on 2008-01-08
I backported it from the hardy package. If anyone is interested: [http://rapidshare.com/files/82276275/gstreamer0.10-ffmpeg_0.10.3-0mk_amd64.deb.html](http://rapidshare.com/files/82276275/gstreamer0.10-ffmpeg_0.10.3-0mk_amd64.deb.html)

Here are the release notes:

> Features of this release

    * Memory usage fixes
    * Playback and seeking fixes
    * Improved QOS support
    * Parallel installability with 0.8.x series
    * Threadsafe design and API

Bugs fixed in this release

    * 474845 : ffmux_mp4 does not encode metadata
    * 433245 : Non-mutex-protected calls to avcodec_open/_close
    * 153263 : no decoder available for real proprietary codecs
    * 334990 : Crash with a .rm file
    * 341736 : [patch] H.263/QDesign Music v.2 movie has great playback ...
    * 342962 : [ffdec_h264] jerky playback of h264 in matroska and quick...
    * 363363 : Please permit building against an external ffmpeg
    * 364139 : [ffdec_h264] regression: artefacts with 'climates' quickt...
    * 375534 : FLV demuxer produces bad framerate, durations
    * 392359 : [ffmpegenc] potential crash in dispose due to double-free
    * 393187 : ffenc_mpeg4 does not set codec_data on caps
    * 394075 : ffdemux disregards FlowReturn result of downstream pushing
    * 403168 : [ffmux_flv] crash on buffer after returning FLOW_ERROR pr...
    * 403739 : ffenc_mpeg1/2video segfaults
    * 407779 : Add more explanations when building against external ffmpeg
    * 435742 : gst-ffmpeg installation fails during make
    * 440253 : no shared lib created and installed (MinGW)
    * 453135 : broken ffenc_*
    * 460274 : FFmpeg buffer duration issues
    * 466221 : Doesn't play " video/sp5x " videos
    * 485033 : Wrong return type for gst_ffmpegdec_setcaps
    * 492419 : Build issues on Windows/MSVC
    * 398875 : [ffdec_camtasia] requires " bits_per_sample " to be set or ...
    * 394071 : ffmpeg now uses YUV4MPEG version 2, caps still indicate v...
    * 399108 : ffmpeg's yuv4mpegpipe demuxer not activated for auto-plug...
    * 444332 : missing unref for videoscale after gst_pad_get_parent
    * 444384 : ffmux_asf could support more input capabilities
    * 482946 : warning in demuxer when receiving GST_EVENT_LATENCY


---

### Post by 6568912 on 2008-01-08
em whats the point of it? :confused:

---

### Post by Major_Kong on 2008-01-08
For me it's just one:

Bugfixes:
(...)
* 342962 : [ffdec_h264] jerky playback of h264 in matroska and quick...
(...)

---

### Post by kwaanens on 2008-01-08
I'm assuming you mean Hardy Heron, not Hoary, which is getting ancient?

---

### Post by Major_Kong on 2008-01-08
> **kwaanens said:**
> I'm assuming you mean Hardy Heron, not Hoary, which is getting ancient?

Sorry, i mixed them up.

---

