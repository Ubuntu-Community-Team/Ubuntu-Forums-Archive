---
title: "Streaming Videos in Firefox"
date: 2007-04-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by dominicd on 2007-04-20
I can't play WMV files in totem or stream WMV in firefox, tho I can play them fine in VLC I get sound but no video in totem.

Streaming quicktime in firefox works fine so I'm guessing the mplayer plugin works fine but I am missing the appropriate codecs for gstreamer ?

I installed firefox and plugins with this script
[http://ubuntuforums.org/showthread.php?p=1174435](http://ubuntuforums.org/showthread.php?p=1174435)
(which also installs the "essential-20061022" codecs)

I also installed these codecs:
```

sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui

```

It couldn't find gstreamer0.10-pitfdll, the others installed fine.

I'm quite desperate to get it to work so any ideas are welcome!

---

### Post by ronocdh on 2007-04-21
[See here.]("http://ubuntuforums.org/showthread.php?t=371093")

---

### Post by dominicd on 2007-04-21
> **ronocdh said:**
> [See here.]("http://ubuntuforums.org/showthread.php?t=371093")

I already had it unchecked =\

And it's not just the streaming I can't play WMVs in totem 'offline' either, for some reason they run fine in VLC.

---

### Post by dominicd on 2007-04-21
I have some more info that I hope may help solve the problems:


When I run a video in mplayer
```

Opening video decoder: [dmo] DMO video codecs
Creating new registry
DMO dll supports VO Optimizations 0 1
DMO dll might use previous sample when requested
GetOutput r=0x0   size:921600  align:1
StreamCount r=0x0  1  1
Decoder supports the following formats: YV12 YUY2 UYVY YVYU RGB8 RGB555 RGB565 RGB24 RGB32 
Decoder is capable of YUV output (flags 0x1b)
VDec: vo config request - 640 x 480 (preferred colorspace: Packed YUY2)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [dmo] DMO video codecs
DMO dll supports VO Optimizations 0 1
DMO dll might use previous sample when requested
GetOutput r=0x0   size:921600  align:1
StreamCount r=0x0  1  1
Decoder supports the following formats: YV12 YUY2 UYVY YVYU RGB8 RGB555 RGB565 RGB24 RGB32 
Decoder is capable of YUV output (flags 0x1b)
VDec: vo config request - 640 x 480 (preferred colorspace: Packed YUY2)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Cannot find codec matching selected -vo and video format 0x33564D57.
Read DOCS/HTML/en/codecs.html!

```

Installed video output drivers for mplayer
```

Available video output drivers:
        xmga    Matrox G200/G4x0/G550 overlay in X11 window (using /dev/mga_vid)
        mga     Matrox G200/G4x0/G550 overlay (/dev/mga_vid)
        tdfxfb  3Dfx Banshee/Voodoo3/Voodoo5
        3dfx    3dfx (/dev/3dfx)
        xvmc    XVideo Motion Compensation
        xv      X11/Xv
        x11     X11 ( XImage/Shm )
        xover   General X11 driver for overlay capable video output drivers
        gl      X11 (OpenGL)
        gl2     X11 (OpenGL) - multiple textures version
        dga     DGA ( Direct Graphic Access V2.0 )
        sdl     SDL YUV/RGB/BGR renderer (SDL v1.1.7+ only!)
        ggi     General Graphics Interface (GGI) output
        fbdev   Framebuffer Device
        fbdev2  Framebuffer Device
        aa      AAlib
        caca    libcaca
        dxr3    DXR3/H+ video out
        xvidix  X11 (VIDIX)
        cvidix  console VIDIX
        null    Null video output
        mpegpes Mpeg-PES to DVB card
        yuv4mpeg        yuv4mpeg output for mjpegtools
        png     PNG file
        jpeg    JPEG file
        gif89a  animated GIF output
        tga     Targa output
        pnm     PPM/PGM/PGMYUV file
        md5sum  md5sum of each frame

```


When I run a video in totem
```

dominic@dominic-desktop:~$ totem

** Message: don't know how to handle video/x-wmv, wmvversion=(int)3, framerate=(fraction)25/1, width=(int)300, height=(int)168, codec_data=(buffer)4ff90a11

(totem:3638): GLib-GObject-CRITICAL **: g_value_get_uint: assertion `G_VALUE_HOLDS_UINT (value)' failed

(totem:3638): GLib-GObject-CRITICAL **: g_value_get_uint: assertion `G_VALUE_HOLDS_UINT (value)' failed

(totem:3638): GLib-GObject-CRITICAL **: g_value_get_uint: assertion `G_VALUE_HOLDS_UINT (value)' failed

(totem:3638): GLib-GObject-CRITICAL **: g_value_get_uint: assertion `G_VALUE_HOLDS_UINT (value)' failed

(totem:3638): GLib-GObject-CRITICAL **: g_value_get_uint: assertion `G_VALUE_HOLDS_UINT (value)' failed

** (totem:3638): CRITICAL **: totem_lang_table_parse_start_tag: assertion `strlen (*attr_values) == 3' failed

```

---

### Post by dominicd on 2007-04-22
Anyone? Please?

---

### Post by ronocdh on 2007-04-22
> **dominicd said:**
> Anyone? Please?
Unfortunately I never use Totem; I find VLC's functionality much greater, as it comes with all the codecs I could ever need (such as WMV). As I explained above, to play WMVs in Firefox (I tested with CNN.com video streams), I remove all mozilla plugins (even VLC--that one wasn't working, either) and just installed the MPlayer one, along with the basic MPlayer package, of course. 

This has worked for me. When the video is loading, I see an MPlayer "connecting to stream [address]... buffering..." in the video pane, so I know it's working.

Much luck to you sir, and please let us know when you finally get it resolved.

---

### Post by pkeegan on 2007-04-22
> **ronocdh said:**
> Unfortunately I never use Totem; I find VLC's functionality much greater, as it comes with all the codecs I could ever need (such as WMV). As I explained above, to play WMVs in Firefox (I tested with CNN.com video streams), I remove all mozilla plugins (even VLC--that one wasn't working, either) and just installed the MPlayer one, along with the basic MPlayer package, of course. 

This has worked for me. When the video is loading, I see an MPlayer "connecting to stream [address]... buffering..." in the video pane, so I know it's working.

Much luck to you sir, and please let us know when you finally get it resolved.

I see MPlayer "connecting to stream [address]... buffering..." in the video pane  then it seems to change IP addresses,BUT I never see any video. I tried getting just a small 40sec video with the same result. 

I have also tried uninstalling MPlayer & it's mozilla-plugin and installing VLC along with a firefox plugin "media player connectivity" to select VLC. At CNN it detects no video plugin which doesn't allow it to continue to the streaming website.

---

### Post by Kilz on 2007-04-22
> **pkeegan said:**
> I see MPlayer "connecting to stream [address]... buffering..." in the video pane  then it seems to change IP addresses,BUT I never see any video. I tried getting just a small 40sec video with the same result. 

I have also tried uninstalling MPlayer & it's mozilla-plugin and installing VLC along with a firefox plugin "media player connectivity" to select VLC. At CNN it detects no video plugin which doesn't allow it to continue to the streaming website.

Firefox 32 may be an option. I can see the small feeds on cnn in it. Link in my signature.

---

### Post by dominicd on 2007-04-25
I DID IT!!!!!! I don't know how but it works!!! I'll try to figure out what in the end got it to work in case other people have similar problems.

---

### Post by dominicd on 2007-04-25
I'm pretty positive that what fixed it in the end was selecting X11 for video output for mplayer32 in firefox32. Removing mozilla-mplayer also seems necessary. For the rest I just have the latest mplayer codecs in the /usr/lib/win32/ folder and have no mplayer whatsoever installed other than mplayer32 (mplayer32_20070130-1_amd64) and the mplayer plugin through the script I linked higher.

---

