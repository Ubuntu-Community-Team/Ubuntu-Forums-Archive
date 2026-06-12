---
title: "xdtv or MythTV and breezy"
date: 2006-04-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by Tink on 2006-04-28
Hi Guys,

Anyone got tvrecording going with either of these apps in 
kubuntu 64bit?

I've seen several "howtos" for myth that had incomplete info
on how to build it yourself (didn't help me mutch) and the multiverse
packages are broken (bits and pieces of three different versions
of myth that don't work together).

I used to be able to compile and run xdtv before I tried the dapper
upgrade, and after a clean reinstall of breezy I can't get xdtv to play
anymore, it craps out with weird error messages (v2.2  that is, the 
one I had on the machine previously, and 2.3.1), and 2.3.2 won't compile.
The output for 2.2 and 2.3.1 is pretty much the same:

```

This is xdtv 2.3.1 running on Linux/x86_64 (2.6.16.9).
scandir: No such file or directory
filename = /home/ailsa/.xdtv/xdtvrc
/home/ailsa/.xdtv/xdtvrc:25: invalid value for fullscreen_mode: noswitch
X Error of failed request:  XF86DGANoDirectVideoMode
  Major opcode of failed request:  136 (XFree86-DGA)
  Minor opcode of failed request:  1 (XF86DGAGetVideoLL)
  Serial number of failed request:  13
  Current serial number in output stream:  13
xdtv_v4l-conf had some trouble, trying to continue anyway
Warning: Missing charsets in String to FontSet conversion
Warning: Cannot convert string "star" to type Pixmap
wmhooks: netwm detected
wmhooks: netwm state above supported
wmhooks: netwm fullscreen supported
wmhooks: nothing found...
DGA: server=2.0, include=2.0
Selected XvImage adaptor with yuyv support: NV17 Video Texture on port 270 (grab
display)
Selected XvImage adaptor with yuyv support: NV05 Video Blitter on port 271 (grab
display)
No XvVideo port available.
Warning: Cannot convert string "none" to type relief
Warning: Cannot convert string "black" to type Pixmap
*** AUDIO DEVICE TYPE = alsa
ioctl VIDIOC_G_FBUF: Invalid argument
classical overlay is disabled*** GRABBER DEVICE TYPE = v4l2
xdtv: simple.c:1787: snd_mixer_selem_get_capture_switch: Assertion `elem' failed
.
```

And here's 2.3.2s compiler error.
```

gcc -O3 -Wall -Wno-switch -DHAVE_AV_CONFIG_H -I.. -I'../'/libavutil -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_GNU_SOURCE -c -o xvid_rc.o xvid_rc.c 
xvid_rc.c: In function `ff_xvid_rate_control_init': 
xvid_rc.c:67: error: structure has no member named `vbv_size' 
xvid_rc.c:68: error: structure has no member named `vbv_maxrate' 
xvid_rc.c:69: error: structure has no member named `vbv_initial' 
make[2]: *** [xvid_rc.o] Error 1 
make[2]: Leaving directory `/root/download/xdtv-2.3.2/libavcodec' 
make[1]: *** [all-recursive] Error 1 
make[1]: Leaving directory `/root/download/xdtv-2.3.2' 
make: *** [all] Error 2 
 
```


Cheers,
Tink

---

