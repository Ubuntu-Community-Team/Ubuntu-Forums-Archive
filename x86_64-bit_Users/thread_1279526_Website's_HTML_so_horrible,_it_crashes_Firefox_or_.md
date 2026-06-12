---
title: "Website's HTML so horrible, it crashes Firefox or Xorg"
date: 2009-09-30
forum: x86 64-bit Users
---

### Post by Youresorock on 2009-09-30
[COLOR="Red"]CAUTION! READ BEFORE CLICKING[/COLOR]

[http://preciouspawsenterprises.com/AvailableKittensPage.html](http://preciouspawsenterprises.com/AvailableKittensPage.html)

This website uses the <big> tag so many times that it crashed Firefox on my work computer (Ubuntu 9.04 x64) and on my home system (Almost identical setup, but fresher install) it crashed Xorg!

This is intense.  The crash happens for me when I scroll down the page slowly.  Make sure you save your work in whatever just in case.  It doesn't crash windows or mac Firefox.

Here's the error in my messages file:
```
kernel: [15260.703412] Xorg[2727]: segfault at fffff ip 00007f0eed028e57 sp 00007ffffa596c28 error 4 in nvidia_drv.so[7f0eecd1e000+39a000]
```

:lolflag:

---

### Post by steve161 on 2009-09-30
Just tried it with FF on PCLinuxOS and nothing odd happened. My cpu and memory monitor did not really change that much from the forum page.

---

### Post by Youresorock on 2009-10-01
> **steve161 said:**
> Just tried it with FF on PCLinuxOS and nothing odd happened. My cpu and memory monitor did not really change that much from the forum page.

Do you have an nVidia video card?  Looks like it was the nvidia driver that actually caused the segfault.

---

### Post by bawig1 on 2009-10-01
Hey,

I'm using the nVidia driver with my laptop's GeForce 9650m GT adapter and got the same result and similar message as the O.P.

---

### Post by steve161 on 2009-10-01
> Do you have an nVidia video card?  Looks like it was the nvidia driver that actually caused the segfault. 	

No I do not.  I also noticed that the page does not render completely in Opera

---

### Post by dcstar on 2009-10-03
> **Youresorock said:**
> [COLOR="Red"]CAUTION! READ BEFORE CLICKING[/COLOR]

[http://preciouspawsenterprises.com/AvailableKittensPage.html](http://preciouspawsenterprises.com/AvailableKittensPage.html)

This website uses the <big> tag so many times that it crashed Firefox on my work computer (Ubuntu 9.04 x64) and on my home system (Almost identical setup, but fresher install) it crashed Xorg!
.........

Didn't do much to my system using FF 3.0.14, although the rendering of the massive fonts does hit the CPU a bit - some people who make websites like this should be shot - twice!    :evil:

---

### Post by akakingess on 2009-10-03
> **dcstar said:**
> Didn't do much to my system using FF 3.0.14, although the rendering of the massive fonts does hit the CPU a bit - some people who make websites like this should be shot - twice!    :evil:

+1, that may sound crude, but I read and learn and practice before I do anything, and someone with something like that online is just atrocious!!!

---

### Post by NoaHall on 2009-10-03
I'm using nvidia cards, on 64 bit, works fine for me, no problems.

---

### Post by dearingj on 2009-10-03
Just tried viewing that page. I've scrolled about half way down so far, and it hasn't crashed my browser or kernel. I do notice that my CPU usage jumps significantly when I scroll down (On my dual-core processor, core 1 goes from just above 0% to about 70% and the other core is generally unaffected; I'm guessing that Firefox has been assigned to core 1 and everything else is using the other). It may be relevant to note that I am running Firefox with the NoScript extension. NoScript blocked a script from preciouspawsenterprises.com but did allow a script from yimg.com.

Possibly relevant system info:
OS running: Ubuntu 9.10 64-bit beta with all available updates
Firefox version as reported by Synaptic: 3.5.3+build1+nobinonly-0ubuntu3
RAM: 4 GB (3.9 GiB reported by System Monitor)
Swap: 7.6 GiB reported by System Monitor
Processor: Intel Core 2 Duo
Graphics card: Don't remember, but I'm using the Nvidia restricted driver.

---

### Post by erilidon on 2009-10-03
I'm running ubuntu 9.04 x64, didn't crash me either, but did take out pandora and the rendering was really slow.

---

### Post by falconindy on 2009-10-04
Crashed my xorg on Firefox 3.0 with 64 bit Jaunty and an nvidia card (only 256mb). Not going to try it again with Chromium.

I need to bookmark this page as a prank...

---

### Post by Arup on 2009-10-05
nvidia driver 185.36, Opera 10.10 latest beta, nothing extraordinary, no CPU spikes or crashes here.

---

### Post by sloggerkhan on 2009-10-05
nvidia card + firefox, no problems, though one hideous website.

---

### Post by jefelex on 2009-10-05
Ya - pretty weird, but I didn't have any problem with it!  ATI graphics card with FGLRX driver

John

---

### Post by theZoid on 2009-10-06
didn't crash here either, Nvidia drivers.  Ran the cpu up a little, and mem usages went up a lot :)  I had 3 other tabs open.  What a ridiculous page design!  :)

---

### Post by rodh on 2009-10-06
I tried it in FF3.0 on Ubuntu 9.04 work ok there but it did crash me running FF3.0 on XP

---

### Post by brntoki on 2009-10-06
> **dcstar said:**
> Didn't do much to my system using FF 3.0.14, although the rendering of the massive fonts does hit the CPU a bit - some people who make websites like this should be shot - twice!    :evil:

C'mon. . . twice isn't *nearly* enough!

In fact, that page is so ugly I *wish* it would crash my system so I wouldn't have to look at it. Wow!

---

