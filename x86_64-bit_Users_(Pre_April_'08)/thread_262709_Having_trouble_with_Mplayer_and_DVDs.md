---
title: "Having trouble with Mplayer and DVDs"
date: 2006-09-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by city-17 on 2006-09-22
edit: sudo hdparm -d1 -k1 /dev/dvd solved my problems.
Hi

Today i try to enable playback of encrypted DVDs with Mplayer on Ubuntu 64 with no luck.

I followed the directions of the Restricted Formats wiki [https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats") , installed the packages fakeroot, debhelper, build-essential, then i ran the install-css script with no trouble.

After doing a restart, i tried with 3 different dvds with no success.

This is what i get at console
```
 sudo mplayer dvd://1
MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Intel Pentium 4/Celeron D Prescott; Pentium D/XE Smithfield; Xeon Nocona,Irwindale (Family: 15, Stepping: 4)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.


91 audio & 204 video codecs
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing dvd://1.
libdvdread: Using libdvdcss version 1.2.5 for DVD access
Reading disc structure, please wait...
There are 5 titles on this DVD.
There are 11 chapters in this DVD title.
There are 1 angles in this DVD title.
libdvdread: Invalid title IFO (VTS_01_0.IFO).
Cannot open the IFO file for DVD title 1.
File not found: '1'
Failed to open dvd://1
```

I use sudo to avoid these extra complaints
```
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.

```
The main problem appear to be these two lines right?
```
libdvdread: Invalid title IFO (VTS_01_0.IFO).
Cannot open the IFO file for DVD title 1.
```Any deas?

I installed Mplayer using Synaptic.

---

### Post by city-17 on 2006-09-25
I don't know if it was because of a reboot or because of installing gxine but now i can do mplayer dvd://1 at console and movies seems to start, but extremely slow and buggy. I get at console something like this:
```
Starting playback...
a52: CRC check failed!
a52: error at resampling
a52: CRC check failed!
a52: error at resampling
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 720x480 => 720x540 Planar YV12
a52: CRC check failed!  0.102 ct:  0.003   8/  8 ??% ??% ??,?% 0 0
a52: error at resampling
a52: CRC check failed!  0.083 ct: -0.043  22/ 22  6%  0%  1.0% 0 0
a52: error at resampling
a52: CRC check failed!  0.119 ct: -0.047  23/ 23  6%  0%  0.9% 0 0
a52: error at resampling
a52: CRC check failed!  0.128 ct: -0.063  28/ 28  5%  0%  0.9% 0 0
a52: error at resampling
a52: CRC check failed!  0.049 ct: -0.085 116/116  4%  0%  0.7% 0 0
a52: error at resampling
a52: CRC check failed!  0.124 ct: -0.061 123/123  4%  0%  0.7% 0 0
a52: CRC check failed!  0.026 ct:  0.006 149/149  3%  0%  0.7% 0 0
a52: error at resampling
a52: CRC check failed!  0.017 ct:  0.004 150/150  4%  0%  0.7% 0 0
a52: error at resampling
a52: CRC check failed!  0.012 ct: -0.021 162/162  4%  0%  0.7% 0 0
a52: error at resampling
a52: CRC check failed!  0.057 ct:  0.012 172/172  3%  0%  0.7% 0 0
a52: CRC check failed!  0.003 ct:  0.012 173/173  3%  0%  0.7% 0 0
a52: CRC check failed!  0.007 ct: -0.002 180/180  3%  0%  0.7% 0 0
a52: error at resampling
a52: CRC check failed!  0.072 ct:  0.018 186/186  3%  0%  0.7% 0 0
a52: error at resampling
a52: CRC check failed!
a52: error at resampling
a52: CRC check failed!  0.031 ct:  0.057 198/198  3%  0%  0.7% 0 0
a52: error at resampling

```

Gxine setup wizard shows me that my DVD drive hasn't DMA enabled, any suggestion?

---

### Post by anaconda on 2006-09-25
If you dont have DMA enabled, then reading and writing to DVD will be really slow. And that is propably the reason movies are slow and buggy..

just eneble DMA for your DVD-player..

sudo hdparm -d1 /dev/hdb

(if my memory serves me right..)
if this doesn't work, just search the forums for 
enable DMA

---

### Post by city-17 on 2006-09-26
> **anaconda said:**
> If you dont have DMA enabled, then reading and writing to DVD will be really slow. And that is propably the reason movies are slow and buggy..

just eneble DMA for your DVD-player..

sudo hdparm -d1 /dev/hdb

(if my memory serves me right..)
if this doesn't work, just search the forums for 
enable DMA

Thanks a lot, now Mplayer, gxine and Totem-gstreamer can play DVD's. I'm not sure if it was me who enabled DMA because i only used sudo hdparm /dev/dvd (without the d1 option) just to see the current status of flags and i get surprised when noticed that DMA was already enabled.

---

