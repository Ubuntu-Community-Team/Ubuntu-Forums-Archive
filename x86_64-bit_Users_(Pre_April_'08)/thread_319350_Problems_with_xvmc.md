---
title: "Problems with xvmc"
date: 2006-12-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by sablar_ocksa on 2006-12-15
Hello!

I recently installed edgy-64bit on my desktop/mediacenter PC (Athlon AM2 3500+, geforce 7600GS). I use this PC to play videos on my 720p projector, so naturally video performance is very important to me. 

I followed the edgy guide and installed the codecs [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Codecs](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Codecs)

and followed the same guide to install the nvidia-glx drivers _and xvmc_

however executing
xine -V xxmc filename.ts

results in a drop in CPU usage from 60% to 20% (which is good and shows that xvmc is working) but the performance is terrible and lot's of frames are droped, it's not watchable...

i compiled mplayer so it would have xvmc support following this guide: [http://www.penlug.org/twiki/bin/view/Main/LinuxHardwareInfoNvidia5200](http://www.penlug.org/twiki/bin/view/Main/LinuxHardwareInfoNvidia5200)

however running
mplayer -vo xvmc -vc ffmpeg12mc filename.ts

results in:

AVI file format detected.
VIDEO:  [XVID]  624x352  12bpp  23.976 fps  942.8 kbps (115.1 kbyte/s)
Clip info:
Software: VirtualDub
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
vo_xvmc: X-Video extension 2.2
vo_xvmc: X-Video MotionCompensation Extension version 1.1
==========================================================================
Forced video codec: ffmpeg12mc
Cannot find codec matching selected -vo and video format 0x44495658.
Read DOCS/HTML/en/codecs.html!
==========================================================================
AO: [oss] 48000Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A: 307.2 (05:07.2) of 22595.4 ( 6:16:35.3)  2.6%                               

MPlayer interrupted by signal 2 in module: play_audio
johannes@johannes:~/MPlayer-1.0pre8$ 35.3)  2.6%

i later installed automatix2 thinking that i might be missing some codec but it did not change anything.

And finally is there anyhing in linux similar to nvidia's pure video? I mean in terms of videoquality

I'm running out of ideas on how to have GPU support for my videoplayback. Any help would be hugely appreciated

J

---

### Post by sablar_ocksa on 2006-12-15
some further googling gave me the answer that only mpeg1 and mpeg2 has xvmc support. Although it seems that "people know people" that play mpeg4 with xvmc. Anybody that can shed some light on this? Most videos i play arn't mpeg2 :/

---

### Post by JackDog on 2006-12-27
I noticed something similar as well. 

I have an nvidia card so I enabled the nvidia xvmc extensions and xine works great. Noticeable difference when tuning ATCS as in it doesn't jitter at all. However mythtv uses mplayer so I either need to recompile mplayer or swap xine in for mplayer in myth. Neither sound fun.

---

