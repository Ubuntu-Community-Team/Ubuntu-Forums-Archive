---
title: "Multi seat arrangement"
date: 2009-08-21
forum: x86 64-bit Users
---

### Post by fazillatheef on 2009-08-21
Is there any way to do multiseat configuration in Ubuntu

I have to use 4 sets of monitor/pc/keyboard with a single CPU...

so I have 2 graphics cards and connect 2 monitors on 1 graphics card .
 
I got some lead at [http://netpatia.blogspot.com/2009/06/multiseat-in-ubuntu-904.html](http://netpatia.blogspot.com/2009/06/multiseat-in-ubuntu-904.html)
 
And was able to configure just 2 devices but need to do it for 4.

Is it possible?

---

### Post by markbuntu on 2009-08-23
At this time randr is not capable of handling mulitple gpus. You will need to disable randr and use xinerama instead. Other than that, the tutorial looks pretty good for setting up multiseat.

---

### Post by fazillatheef on 2009-08-25
How do I enable xinerama instead of xrandr.

---

### Post by MattiJ on 2009-09-05
I had multiset working pretty well on my 64bit Janty dual Nvidia cards, GeForce 9500 GT + GeForce 9400 GT dual display and 9500 and hd tv on 9400 runing XBMC I even coluld get digital sound on hdmi(tV) and analog for the other user intel on ASUS P5B.

But yes the is a very big BUT it gave me some very nasty crashes and the last one killed my system partion, I manged to save  some files but most was lost. I cant understand how this could happen OK if I have to run fsck it but whole partion??? it's ext4.

I duno if I dare to test it again but I realize there is many things that can be the reason for the crash, PSU is 750W and CPU is E6600 that at the time was clocked at about 2,9GHZ from 2,4 (I had it so long that I forget about it) also box had 10 HDD's could it be to little power? The crashes came mostly on heavy CPU load.

The setup was mostly from here [http://www.linuxtoys.org/multiubuntu/multiubuntu.html](http://www.linuxtoys.org/multiubuntu/multiubuntu.html)
 
I'm also pretty sure that Option "Xinerama" "0" was in xorg.config.

Maybe I should try MDM instead? anyone tested it on Jaunty?

Any thoughts?

---

