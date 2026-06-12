---
title: "optimal ubuntu mencoder setup for AMD64"
date: 2006-03-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by danboid on 2006-03-16
I want to be able to use get the best performance possible out of mencoder under Ubuntu.

The problem with mplayer and mencoder is that the w32codecs (which allow you to play and convert divx, windows media etc.) only work with 32-bit libraries and programs and so thats why I've installed Ubuntu breezy i386 as mencoder is one of my main programs, chroot sounds like a hassle and 32-bit linux has more support/programs/drivers etc. Doesn't seem like a whole lot can be gained by going fully 64-bit unless you have more than 4GB RAM!

The problem doesn't end there of course- I need to know what kernel I need to install and what mencoder version. Do I use the i686 or k7 ubuntu kernel or can I even install a k8 kernel (i think this is what I really need to do) from AMD64 breezy? What advantages, as far as video encoding is concerned, does the k8 kernel have over the i686? Anybody here tried installing the k8/AMD64 breezy kernel under i386 breezy? How did you do it? Any problems?

Finally, which mencoder version should i use and how best to install? I would imagine that neither the i586 or k7 mencoder packages in i386 ubuntu are going to make full use of the AMD64 so I presume I'll have to install mplayer/mencoder from source? Again, anyone done this already? What packages should I ensure I have installed if I need to re-compile mencoder and are there any special configure options I'll need to pass to make full use of the A64?

These problems need to addressed in Ubuntu and both Cinelerra and lxdvdrip need to be included in Ubuntu universe/multiverse or ubuntu-plf before Ubuntu become useable for video IMO.

Thanks for your help!

dan

---

### Post by Yagisan on 2006-03-16
[QUOTE=danboid]I want to be able to use get the best performance possible out of mencoder under Ubuntu.[/quote]As a general rule, if you have a faster cpu, it is better. For some codecs, eg h264, if you have dual core it helps. Turning off hyperthreading may help, if you have an Intel CPU.

[QUOTE=danboid]The problem with mplayer and mencoder is that the w32codecs (which allow you to play and convert divx, windows media etc.) only work with 32-bit libraries and programs and so thats why I've installed Ubuntu breezy i386 as mencoder is one of my main programs, chroot sounds like a hassle and 32-bit linux has more support/programs/drivers etc. Doesn't seem like a whole lot can be gained by going fully 64-bit unless you have more than 4GB RAM![/quote]
That is incorrect. There are a few formats that can't be played without w32codecs, IIRC they are current realmedia, and windows media player v3 (WMP9/10 files). mpeg1/2/4 (vcd/dvd/xvid-divx) is all natively supported (but not always faster) on amd64. You will need to install the 64bit amd64 version of ubuntu to run a 64bit mencoder.

[QUOTE=danboid]The problem doesn't end there of course- I need to know what kernel I need to install and what mencoder version. Do I use the i686 or k7 ubuntu kernel or can I even install a k8 kernel (i think this is what I really need to do) from AMD64 breezy? What advantages, as far as video encoding is concerned, does the k8 kernel have over the i686? Anybody here tried installing the k8/AMD64 breezy kernel under i386 breezy? How did you do it? Any problems?[/quote]The Kernel has very little impact on encoding speed (I could not measure it)

[QUOTE=danboid]Finally, which mencoder version should i use and how best to install? I would imagine that neither the i586 or k7 mencoder packages in i386 ubuntu are going to make full use of the AMD64 so I presume I'll have to install mplayer/mencoder from source? Again, anyone done this already? What packages should I ensure I have installed if I need to re-compile mencoder and are there any special configure options I'll need to pass to make full use of the A64?[/quote]if you use 32bit ubuntu, and only offical repos, the -i586 package is the best. If you add the doomsday repo in my signature you'll find updated mencoder packages. In my repo, the -k6 package was changed to only run on an amd64 machine (32bit mode), that would be the fastest choice.

[QUOTE=danboid]These problems need to addressed in Ubuntu and both Cinelerra and lxdvdrip need to be included in Ubuntu universe/multiverse or ubuntu-plf before Ubuntu become useable for video IMO.

Thanks for your help!

dan[/QUOTE]
??? I have been using Ubuntu for video editing for a long time now, and it works rather well. I've also been doing my best to get the current working versions of video tools into Ubuntu, with my fellow members of motumedia.

I'll edit my post with some benchmarks shortly of 64bit mencoder vs 32bit mencoder on a 2GHz athlon64 machine.

--- Edit --- Added benchmarks

Source file:
VIDEO:  [MJPG]  768x576  24bpp  25.000 fps  12390.6 kbps (1512.5 kbyte/s)
AUDIO: 44100 Hz, 1 ch, s16le, 705.6 kbit/100.00% (ratio: 88200->88200)

**64bit xvid + mp3 pass 1**
```
mencoder ic-noads.avi -ovc xvid -xvidencopts pass=1:bitrate=2200:me_quality=6:nopacked:max_bframes=2:closed_gop:quant_type=mpeg:trellis:chroma_me:chroma_opt:hq_ac:vhq=4:bvhq=1 -oac mp3lame -lameopts abr:mode=3:preset=standard -vf hqdn3d,pp=fd/ha/va/dr,scale=704:528 -sws 9 -ss 600 -endpos 60 -o /dev/null
Pos:  60.0s   1513f (24%)  17fps Trem:   4min 174mb  A-V:0.054 [5947:127]

```
**64bit xvid + mp3 pass 2**
```
mencoder ic-noads.avi -ovc xvid -xvidencopts pass=2:bitrate=2200:me_quality=6:nopacked:max_bframes=2:closed_gop:quant_type=mpeg:trellis:chroma_me:chroma_opt:hq_ac:vhq=4:bvhq=1 -oac mp3lame -lameopts abr:mode=3:preset=standard -vf hqdn3d,pp=fd/ha/va/dr,scale=704:528 -sws 9 -ss 600 -endpos 60 -o ic-xvid-2200-deblock-denoise-mpeg.avi
Pos:  60.0s   1513f (24%)   7fps Trem:  10min  61mb  A-V:0.054 [2007:127]
```
**32bit xvid + mp3 pass 1**
```
mencoder ic-noads.avi -ovc xvid -xvidencopts pass=1:bitrate=2200:me_quality=6:nopacked:max_bframes=2:closed_gop:quant_type=mpeg:trellis:chroma_me:chroma_opt:hq_ac:vhq=4:bvhq=1 -oac mp3lame -lameopts abr:mode=3:preset=standard -vf hqdn3d,pp=fd/ha/va/dr,scale=704:528 -sws 9 -ss 600 -endpos 60 -o /dev/null
Pos:  60.0s   1513f (24%)  16fps Trem:   4min 174mb  A-V:0.054 [5947:127]

```
**32bit xvid + mp3 pass 2**
```
mencoder ic-noads.avi -ovc xvid -xvidencopts pass=2:bitrate=2200:me_quality=6:nopacked:max_bframes=2:closed_gop:quant_type=mpeg:trellis:chroma_me:chroma_opt:hq_ac:vhq=4:bvhq=1 -oac mp3lame -lameopts abr:mode=3:preset=standard -vf hqdn3d,pp=fd/ha/va/dr,scale=704:528 -sws 9 -ss 600 -endpos 60 -o ic-xvid-2200-deblock-denoise-mpeg.avi
Pos:  60.0s   1513f (24%)   6fps Trem:  11min  61mb  A-V:0.054 [2007:127]

```

Look at those results, and judge for yourself. It is not a big difference. FYI, I use amd64 in 64bit mode.

---

