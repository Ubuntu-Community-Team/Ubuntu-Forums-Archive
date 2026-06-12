---
title: "Gutsy 64 bit slow &amp; no wobblies!!"
date: 2008-05-13
forum: x86 64-bit Users
---

### Post by Alexis Phoenix on 2008-05-13
Hello all

The machine:
Dell Inspiron 1501 laptop with dual core AMD Turion 64 bit and ATI graphics.

I have recently wiped Feisty 32 bit off this and installed Gutsy 64 bit.  Having had quite a snappy, responsive machine I'm disappointed to find even after my usual custom kernel build, boot time is very slow (something about IRQ 16 is causing the delay, though it says OK when it's done whatever it does), there is an error about not being able to detect the hardware clock and another that the AGP aperture is too small (32MB) even though it's a PCI express machine so there's no AGP slot.  Gnome loads very slowly and I can no longer have wobbly windows and wotnot even though DRI is running and the ATI driver supports it.

Wahhhh! :frown:

Apart from a few niggles, general running of the machine seems okay, but still in general seems slower than I'm used to.

Has anyone else had similar problems?  Can anyone suggest a way to fix this?  I miss my desktop effects and quick boot time!!

---

### Post by philinux on 2008-05-13
How many people use a custom kernel build.

The default is working very snappy here.

---

### Post by Alexis Phoenix on 2008-05-22
Ok, I forgot I needed Xgl to get the wobbly windows and stuff.  So that's working now.

As to things being slow, well I've upgraded to Hardy Heron and things are a little faster.  Home brew kernel is faster than generic, which is why I do it.

Alexis Phoenix

---

### Post by Yellow Pasque on 2008-05-22
I use a custom kernel. I find the CPU utilization to be much better (i.e. not throttling to full speed as often), the size of the kernel to be much smaller (74.0 MB vs. 46.6 MB) and the boot time to be faster (haven't done measurements).

I admit that configuring the kernel can be somewhat tedious, but once you've done it, you can reload the configuration file for subsequent kernels in that series (e.g. 2.6.24). The main changes I make are eliminating hardware drivers I don't need and setting the kernel to optimize for my specific architecture (AMD K8 ).

> Ok, I forgot I needed Xgl to get the wobbly windows and stuff.
You shouldn't need XGL to get desktop effects. XGL is slow, outdated, and often causes problems with accelerated video playback.

---

### Post by Yellow Pasque on 2008-05-22
Ah, I just saw you were running Gutsy. If you're running Gutsy and the included restricted driver, you will need XGL.

I'd recommend trying to install the Catalyst 8-5 (8.49) driver using this guide: [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)
Ignore the download link for Catalyst 8-4 and grab this month's release here: [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/64bit/ati-driver-installer-8-5-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/64bit/ati-driver-installer-8-5-x86.x86_64.run)

You might also consider upgrading to Hardy. It's an awesome release :)

---

### Post by Alexis Phoenix on 2008-05-24
Hmm, okay, that was interesting...
I actually upgraded to Hardy Heron since my last post, but didn't know I didn't need Xgl, so thanks for that.  I'd installed a recent version of the driver from ATI anyway.  So I've just tried removing Xgl and hey presto - everything works.  Edges seem a bit jagged when I move a window now though.  OTOH, the cpu frequency doesn't go shooting up now.

OAN, the kernel which I'd compiled on Gutsy no longer boots on Hardy (it gets stuck at starting the logger) so I've been playing with the config again - so I can't see what kind of improvement I can expect there just yet.  I need to investigate some things it would appear....

Knowledge is power and all that.  Or at least some saved cpu cycles to use for fancy effects anyway...

---

