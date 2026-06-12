---
title: "ATI Drivers won't install properly"
date: 2008-07-08
forum: x86 64-bit Users
---

### Post by Sed Levis on 2008-07-08
Hey all, 

I'm a super newbie. with that said, here's the issue that i'm having.  I downloaded the ATI driver installer from ATI and ran it.  Now, when I try to open the catalyst control center it tells me that either I don't have the driver installed or it's not functioning properly.

I've tried using the EnvyNG script with no luck.

Here's a little back story:  I'm running ubuntu studio and I also installed compiz.  I've read that compiz uses different drivers or something.  I'm wondering if I can uninstall the drivers that i've tried to install or if I should even try to?

My video card is the Radeon Xpress 200M on a HP zv6000 (amd x64-2ghz-1.1gig ram) Running Hardy.

Thanx!

---

### Post by Kilz on 2008-07-08
> **Sed Levis said:**
> Hey all, 

I'm a super newbie. with that said, here's the issue that i'm having.  I downloaded the ATI driver installer from ATI and ran it.  Now, when I try to open the catalyst control center it tells me that either I don't have the driver installed or it's not functioning properly.

I've tried using the EnvyNG script with no luck.

Here's a little back story:  I'm running ubuntu studio and I also installed compiz.  I've read that compiz uses different drivers or something.  I'm wondering if I can uninstall the drivers that i've tried to install or if I should even try to?

My video card is the Radeon Xpress 200M on a HP zv6000 (amd x64-2ghz-1.1gig ram) Running Hardy.

Thanx!
Did you follow the instructions Soxs gave you [in this thread?]("http://ubuntuforums.org/showthread.php?t=848550")

---

### Post by Sed Levis on 2008-07-08
I did.  I started this thread because I didn't want to Hijack that one... Like I said, i'm really new... sorry if I'm screwing this up.  Anyway, appearently I needed to uninstall the "Mesa Drivers" that compiz was using by uninstalling the xserver-xgl package.  Once I did that and rebooted ATI took over and from what I can tell, It seems to be working.  However, do you know how I can check if 3D and hardware acceleration is working?  I did notice that video played in fullscreen looked much better now that the drivers seem to be working but I don't know what that proves.

Thanx!

---

### Post by Kilz on 2008-07-08
> **Sed Levis said:**
> I did.  I started this thread because I didn't want to Hijack that one... Like I said, i'm really new... sorry if I'm screwing this up.  Anyway, appearently I needed to uninstall the "Mesa Drivers" that compiz was using by uninstalling the xserver-xgl package.  Once I did that and rebooted ATI took over and from what I can tell, It seems to be working.  However, do you know how I can check if 3D and hardware acceleration is working?  I did notice that video played in fullscreen looked much better now that the drivers seem to be working but I don't know what that proves.

Thanx!

Typing fglrxinfo in the terminal should say OpenGL vendor string: ATI Technologies Inc. glxgears in the terminal should bring up a small window with rotating gears.

---

