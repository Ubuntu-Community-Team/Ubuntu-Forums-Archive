---
title: "Intel Graphics Driver Problem in 8.10 amd64"
date: 2009-04-10
forum: x86 64-bit Users
---

### Post by _khAttAm_ on 2009-04-10
I have the following configuration:
Gigabyte G31M-S2l with onboard Intel 3100 graphics (00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)
).
Intel C2D E6550

I'm using Ubuntu Intrepid Ibex x86_64 with the latest updates.

When I try to enable certain compiz features, the system just logs out. Compositing works fine unless options like 3d windows are enabled. I know 3d windows used to work but I don't know when it stopped.

Anyways, thats not an issue. I don't need the 3d Windows. What I'm concerned about is Games not running in wine. I tried to run Street Bike Fury, a flash based game, and it just logs out. I also tried Nfs Hot Pursuit and still the same.

I read that it is a Graphics related problem. Has anyone resolved the problem? Will upgrading to the latest driver from intel site do any good? Will I able to compile it in my 64-bit machine?

Any response will be highly appreciated.

---

### Post by Arup on 2009-04-11
Hi, 

I had to live with it on my PC, even Google Earth doesn't work on G31. You can't really compile your own driver, its quite a daunting task and the kernel has to be patched in that case. You just have to wait for the newer kernel release or switch to a nvidia card.

---

### Post by _khAttAm_ on 2009-04-13
^thanks for the response.

yes.. google earth has problems when compositing enabled. the GMA 3100 is poor with linux. However, I do not plan to use my PC for gaming, just want some old games to run. And yes they are compatible with wine. But I want the intel gfx not to crash at times.

And BTW, how do I compile the intel graphics driver for x86? any ideas?

---

### Post by Arup on 2009-04-13
> **_khAttAm_ said:**
> ^thanks for the response.

yes.. google earth has problems when compositing enabled. the GMA 3100 is poor with linux. However, I do not plan to use my PC for gaming, just want some old games to run. And yes they are compatible with wine. But I want the intel gfx not to crash at times.

And BTW, how do I compile the intel graphics driver for x86? any ideas?

The driver included with Ubuntu is actually the newer one and therefore compiling the older driver won't really help you at all. In my case, Google Earth doesn't work even with compiz turned off.

In case you are interested, here are the instructions. [http://intellinuxgraphics.org/install.html](http://intellinuxgraphics.org/install.html)
[http://wiki.x.org/wiki/Development/git](http://wiki.x.org/wiki/Development/git)

---

### Post by Thelasko on 2009-04-13
I remember a question about this a while back.  

First, be warned, that the Intel driver for 8.10 [has a regression]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/320893"), and may not be as good as the driver for 8.04. I don't know all of the details for this issue.

Second, check the "virtual" line in xorg.conf.  The values have to be less than 2048 by 2048 for direct rendering to work.

Run
```
glxgears
```
to see if your direct rendering is working.

---

### Post by Thelasko on 2009-04-13
[Here is an on going discussion on this topic.]("http://ubuntuforums.org/showthread.php?t=1076014")

---

### Post by _khAttAm_ on 2009-04-17
> **Thelasko said:**
> I remember a question about this a while back.  

First, be warned, that the Intel driver for 8.10 [has a regression]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/320893"), and may not be as good as the driver for 8.04. I don't know all of the details for this issue.

Second, check the "virtual" line in xorg.conf.  The values have to be less than 2048 by 2048 for direct rendering to work.

Run
```
glxgears
```
to see if your direct rendering is working.

I see the gears. Does it mean that direct rendering is working?

> **Thelasko said:**
> [Here is an on going discussion on this topic.]("http://ubuntuforums.org/showthread.php?t=1076014")
This is about Jaunty Jackalope and X3100. I have Intrepid and 3100. 

Hope the issue is fixed in the Final Jaunty Release.

Thanks for your response.

---

### Post by Thelasko on 2009-04-17
> **_khAttAm_ said:**
> This is about Jaunty Jackalope and X3100. I have Intrepid and 3100.

Yes, but the very first sentence of the first post says:
> I had to revert from Intrepid to Hardy on my new laptop due to VERY poor video performance with the Graphics Media Accelerator X3100.


---

### Post by Arup on 2009-04-20
Just out of curiosity I reverted back to Hardy 8.04LTS and guess what, Google Earth works, the log out and re login issue of screen going blank is gone, something seriously went wrong with the Intel driver in Intrepid and hopefully Jaunty fixes that or else I would have to stick to LTS for now, thankfully its LTS:D

This is of course for my nephew's PC with Intel G31 graphics. On my PC with ATI 4850 dual GPU there is no issues with Intrepid.

---

