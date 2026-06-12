---
title: "visual Effects &quot;Desktop effects could not be enabled&quot;"
date: 2009-10-03
forum: x86 64-bit Users
---

### Post by Gosport on 2009-10-03
I have an integrated ATI Radeon HD 4200 and when I went to enable extra visual effects I got an error telling me that "Desktop effects could not be enabled"  What do I need to do?

---

### Post by river226 on 2009-10-03
You probably need the right drivers. this may help:
[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

---

### Post by Yellow Pasque on 2009-10-03
[http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)

---

### Post by Gosport on 2009-10-04
Us there a simple way to do this without using proprietary drivers?  I'd be happy if I could watch movies that weren't choppy.  (I tryied installing the ATI driver and it installed an ugly watermark in the bottom corner of my scren.)

---

### Post by Yellow Pasque on 2009-10-05
Which version of fglrx/Catalyst did you install (the one that comes with Ubuntu or the latest one from the ATI/AMD site)?

---

### Post by Gosport on 2009-10-05
> **Temüjin said:**
> Which version of fglrx/Catalyst did you install (the one that comes with Ubuntu or the latest one from the ATI/AMD site)?

I installed the driver from [http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

I have since removed it.  Should I just buy an inexpensive video card?

---

### Post by Yellow Pasque on 2009-10-05
The open-source ATI drivers don't support 3D acceleration "out-of-the-box" in current versions of Ubuntu (expect 3D support in Ubuntu 10.04). You can build it yourself, but it's not trivial, especially for n00bs.
[http://ubuntuforums.org/showthread.php?t=1257453](http://ubuntuforums.org/showthread.php?t=1257453)

---

### Post by Gosport on 2009-10-05
> **Temüjin said:**
> The open-source ATI drivers don't support 3D acceleration "out-of-the-box" in current versions of Ubuntu (expect 3D support in Ubuntu 10.04). You can build it yourself, but it's not trivial, especially for n00bs.
[http://ubuntuforums.org/showthread.php?t=1257453](http://ubuntuforums.org/showthread.php?t=1257453)

So if I just wait till the end of April my 3D and choppy DVD playback problems will be solved with a new Ubuntu release?  I can live with that.

---

### Post by EJeanmaire on 2009-10-05
> **Gosport said:**
> So if I just wait till the end of April my 3D and choppy DVD playback problems will be solved with a new Ubuntu release?  I can live with that.

Don't count on that. Instead you should get the 9.8 or 9.9 ATI restricted drivers from the ATI website, or install the xorg.fglrx.* drivers from Synaptic Package Manager.  These should not add any watermark to your background, plus movie playback should be fine.

---

### Post by Yellow Pasque on 2009-10-05
> **EJeanmaire said:**
> Don't count on that.
Yeah, you should count on that. The open-source 3D drivers are already there, but Ubuntu chose not to distribute it in Karmic because it came too late in their release cycle.

> For the Radeon HD 4200 integrated graphics, there is 2D / X-Video acceleration available for this chipset while the initial 3D support in Mesa is not enabled for Ubuntu 9.10 but will be for Ubuntu 10.04 LTS. Using the AMD Catalyst 9.10 driver or later works just fine with Ubuntu 9.10 and this AMD IGP.
[http://www.phoronix.com/scan.php?page=article&item=ecs_785g&num=3](http://www.phoronix.com/scan.php?page=article&item=ecs_785g&num=3)

> Instead you should get the 9.8 or 9.9 ATI restricted drivers from the ATI website, or install the xorg.fglrx.* drivers from Synaptic Package Manager.  These should not add any watermark to your background, plus movie playback should be fine.
Those drivers probably don't support the new 785G/RS880 (RadeonHD 4200 IGP). S/he will need at least Catalyst 9-10 (currently available in Ubuntu 9.10) to go the proprietary route.

---

### Post by EJeanmaire on 2009-10-06
> **Temüjin said:**
> Yeah, you should count on that. The open-source 3D drivers are already there, but Ubuntu chose not to distribute it in Karmic because it came too late in their release cycle.

Cool, can't wait.

---

### Post by MaindotC on 2009-10-16
> **Temüjin said:**
> Yeah, you should count on that. The open-source 3D drivers are already there, but Ubuntu chose not to distribute it in Karmic because it came too late in their release cycle.


[http://www.phoronix.com/scan.php?page=article&item=ecs_785g&num=3](http://www.phoronix.com/scan.php?page=article&item=ecs_785g&num=3)


Those drivers probably don't support the new 785G/RS880 (RadeonHD 4200 IGP). S/he will need at least Catalyst 9-10 (currently available in Ubuntu 9.10) to go the proprietary route.

Are you saying to install the 9.10 driver by using System -> Administration -> Hardware Drivers and THEN installing the 9.8 or 9.9 proprietary driver from ATI's website?  I'm trying to get proper video display in my 9.10 setup as well.

---

### Post by c.goncalves on 2009-10-16
Hi,

I'm a 64bit user and when i installed ubuntu on my Toshiba if i enabled the visual effects they worked but when minimizing/maximizing a window the computer hanged over 2/3 seconds.

So i've been looking a solution for that and i've found these days.

There is as kind of patch to solve that issue. It can be found here:
[https://launchpad.net/~ubuntu-x-swat/+archive/xserver-no-backfill](https://launchpad.net/~ubuntu-x-swat/+archive/xserver-no-backfill)

At least it worked for me.

I hope i've been helpfull. See you soon...

---

### Post by c.goncalves on 2009-10-18
Hi, it's me again...

I forgot to say that i'm using the last ATI proprietary driver, ATI Catalyst 9.9 for x86 and x86_64 systems.
That driver can be downloaded here: [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx)

I installed this driver and then apllyed the patch that i refered in the last post and now my system looks great and can handle with desktop effects with no issues.

---

### Post by nickleus on 2009-10-30
> **c.goncalves said:**
> 
I installed this driver and then apllyed the patch that i refered in the last post and now my system looks great and can handle with desktop effects with no issues.
here's what i did to get desktop effects working in karmic amd64 with my ATI Radeon HD 4650 **WITHOUT** having to run any kind of patch:
[http://nickhumphrey.net/showthread.php?p=3345](http://nickhumphrey.net/showthread.php?p=3345)

---

