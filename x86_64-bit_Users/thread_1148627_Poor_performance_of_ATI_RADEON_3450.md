---
title: "Poor performance of ATI RADEON 3450 ?"
date: 2009-05-04
forum: x86 64-bit Users
---

### Post by Tilex on 2009-05-04
Hi folks,

I recently did a ```
glxgears
``` on my Jaunty 64-bit system and here are the results :
```
unknown chip id 0x95c5, can't guess.
2842 frames in 5.0 seconds = 568.348 FPS
3141 frames in 5.0 seconds = 628.066 FPS
3023 frames in 5.0 seconds = 604.493 FPS
3178 frames in 5.0 seconds = 635.594 FPS
2751 frames in 5.0 seconds = 550.170 FPS
3266 frames in 5.0 seconds = 653.062 FPS
3022 frames in 5.0 seconds = 604.389 FPS
2980 frames in 5.0 seconds = 595.951 FPS
3244 frames in 5.0 seconds = 648.776 FPS
3260 frames in 5.0 seconds = 651.808 FPS

```

I've got an ATI Radeon 3450 on a 3.0Ghz Dual-core Intel with 4gig of RAM.  Am I right to think that these results are quite low ?

```
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Mobility Radeon HD 3450 [1002:95c5]

```

On my laptop, I've got FPS in the 2000's !

I just followed the tutorial at this address :
> [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
 and the FPS did not improve.

Is it because I've got a 1920x1600 resolution on a 23'' monitor ?

Any thought guys ?  For those with a similar video card (try lspci -nn | grep VGA), do you get similar results ?

---

### Post by thedaemon on 2009-05-04
Weak video card means weak scores. I'm not 100% on ATI's cards as I always use Nvidia, but it seems to me with the $40 price tag after a quick google search, you shouldn't be expecting much. I run 1920x1200 on a Nvidia 9800GTX. I can post my scores later, but I doubt it will do anything but make you sad. :\ Maybe you can get a new card?

---

### Post by Fir3chi3f on 2009-05-04
(I've been told at least) 

glx gears isn't a good benchmarking tool, just a glx rendering test. 

Ati drivers have never been that good under linux, it will be a while but hopefully they will get better with AMD releasing the source.

---

