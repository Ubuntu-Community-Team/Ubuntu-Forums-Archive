---
title: "flash failing after some time after boot"
date: 2008-06-23
forum: x86 64-bit Users
---

### Post by vatavr on 2008-06-23
Hi,

I'm not new to linux, nor to google, but I recently have a problem I cannot solve: after some time after booting my machine, flash (in firefox) stops working. When I boot up, I can watch flash (for example youtube) without problems, then, without doing anything particular, flash stops working - either it shows the first 2 seconds of the video without sound and then stops, or it shows only a gray field with no video at all.

I compared the processes running when flash is working with the ones when flash isn't working and can't really see a difference.

My setup:

Core2Duo processor
4GB RAM
AMD/ATI HD3850

For fglrx to work with Hardy and that setup (4GB of memory), I had to modify /proc/mtrr so it looks like this:

reg00: base=0x00000000 (   0MB), size=2048MB: write-back, count=1
reg01: base=0x80000000 (2048MB), size=1024MB: write-back, count=1
reg02: base=0xc0000000 (3072MB), size= 256MB: write-back, count=1
reg03: base=0x100000000 (4096MB), size= 512MB: write-back, count=1
reg04: base=0x120000000 (4608MB), size= 256MB: write-back, count=1

I know this is by far not enough information about my system for anyone to start with, but it wouldn't make much sense to post *everything* - so please tell me what more information you need and I'll provide it.

---

### Post by markbuntu on 2008-06-23
Flash 9 did that to me so I got flash10b and that fixed it. There are a bunch of posts around these forums about getting it.

Also, if you are using the -16 or -17 kernel you should update to -18 or -19.

If you want some tips on setting up your HD3850 you can go here, they really will make an improvement but you might need to fool around with the TexturedVideo option.


[http://forum.compiz-fusion.org/showthread.php?t=6794](http://forum.compiz-fusion.org/showthread.php?t=6794)

If you want the 8.5 driver you can get it from here:

[http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)

and you can follow these directions to install it, use method2 and be sure and follow the directions precisely:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

It worked for me on both my 386i and amd64 installs (I run them both on separate hard drives)

---

### Post by vatavr on 2008-06-24
Markbuntu, thanks for the quick reply!

My system is up-to-date (-19 kernel), I'm using the fglrx driver from the Ubuntu repository and it's really only for compiz, I don't play games or do any other stuff that requires 3D acceleration (except compiz).

I'll try flash 10 during the weekend and post my results.

---

### Post by vatavr on 2008-07-02
OK...

After nothing helped (flash 10, etc.) and I was just about going to switch to another distribution, I found by mistake how to solve this: just stop Audacious.

I thought sound (software-mixing) isn't a problem anymore since a few years now... Seems I was wrong.

Maybe it's not ALSA, I don't know what really the problem is and am not in the mood to try to find out... :(

---

