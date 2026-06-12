---
title: "x64 World of Warcraft general performance (32 bit client vs 64 bit)"
date: 2013-12-11
forum: Wine
---

### Post by b_ice99 on 2013-12-11
My system:
Intel® Core&#8482;2 CPU 6600 @ 2.40GHz × 2 3.0 GiB ram
GPU ATI Radeon HD6770 with proprietary drivers from ubuntu repos
OS Ubuntu 12.04 x64
software: wine1.7.8 and wow.exe newest version as of this week's patch

I play wow on the x64 client and it's almost unplayable, I use the -opengl at launch and the frame rate is awful.  20 at best, usually averaging less than 10 with lowest graphic settings on everything--it would lag so bad sometimes I'd get audio glitches.
I switched to the 32 bit client and noticed a big improvement but still a lot of problems.  My fps is still very low for what I'm used to on this build with an older gpu (an nvidia 8600 gts) on windows xp x64 which ran wow much better, averaging over 80 fps with high graphics, ultra view distance and ultra environment detail but otherwise the high preset level.

I think some of the libraries are not porting over right to wine, but I'm a newb to this stuff.  Should I switch to 12.04 x86 (since it seems they only need half the libraries) or would that not help?  I'd like something easier even if it's not quite simplier.

---

### Post by Tweak42 on 2013-12-18
Sounds like you're being held back by wine's multi-thread problem.  There are some recent wine developements trying to address this. 
[http://bugs.winehq.org/show_bug.cgi?id=11674](http://bugs.winehq.org/show_bug.cgi?id=11674)

Also linux Radeon drivers tend to not as be on a performance parity to windows, so there maybe some issues there.  If you still have your older nvidia card you could try swapping that in and see if things run better under linux.

The biggest issue I notice between wow on linux vs windows is there huge framerate hit you take when there are many objects onscreen, aka raids.  For 5 mans and questing outdoors it's usually fine.

---

### Post by father_ted on 2014-01-04
Im playing wow64 with the amd open source drivers. The performance is generally lower than the propitiatory drivers - but quite playable.

i launch from the command line like this - wine "C:\\Program Files (x86)\\World of Warcraft\\WoW-64.exe"

there is a problem with wine atm whih causes a message to the console - fixme:d3d:resource_check_usage Unhandled usage flags 0x8.

this is causing horrible lag spikes. without this using the mesa amd drivers i can get 60+fps. when this even happens ( which is often ) i drop down to a very low frame rate. please check by running from the command line and see if you also have this problem.

---

### Post by father_ted on 2014-01-09
Just noticed the the xserver update that just came through seems to have reduced the lag spikes a lot.

I am using the directx command stream registry setting.

---

