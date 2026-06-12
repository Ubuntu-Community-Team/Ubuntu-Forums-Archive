---
title: "how to install xorg-server, xproto, fontsproto?"
date: 2009-01-19
forum: x86 64-bit Users
---

### Post by suncoolsu on 2009-01-19
How do I install xorg-server xproto and fontsproto on Hardy Heron.

I googled and found how to download xorg-server. This is what I did.
> 
sudo apt-get source xorg-server 

It worked and I was able to download xorg-server1.4.1. I wanted to install this but ./configure didn't work. I get the error that **PIXMAN** is not installed. Following is the error.

> checking for PIXMAN... configure: error: Package requirements (pixman-1 >= 0.9.5) were not met:

No package 'pixman-1' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PIXMAN_CFLAGS
and PIXMAN_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

Then I opened Synaptic to see if PIXMAN was available. Surprisingly it shows that libpixman1-1-0 (ver 0.10.0) is already installed :confused:
Can anyone help? Pls!

I could find **x11proto-core-dev** on Synaptics, which I think is the **xproto** I want.

I dont see anything for fontsproto :-(

Pls get me out of this darkness my fellow enlightened ubuntu users!

thx

---

### Post by cariboo on 2009-01-19
It would help if you told us what it is that you are trying to do, there are several xservers installed by default.

Jim

---

### Post by suncoolsu on 2009-01-20
thanks a lot for the encouraging reply !! i appreciate it!

this is my problem - 

I have a 1535 dell studio with AUO LCD. There was a bug in xserver-xorg-video-intel which resulted in WSoD if i set driver as "intel" in xorg.conf file. I have been using Vesa driver.

Well! the good news is that it has been solved and the patch has been released. Following is the patch link - 
[http://launchpadlibrarian.net/21219729/104_i830-vbt-timing-hack.patch](http://launchpadlibrarian.net/21219729/104_i830-vbt-timing-hack.patch)

this is the bug link: 
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/297245](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/297245)
> 
diff -Nurp patched/src/i830_bios.c working/src/i830_bios.c
--- patched/src/i830_bios.c 2009-01-14 12:36:59.000000000 -0800
+++ working/src/i830_bios.c 2009-01-14 12:40:10.000000000 -0800
@@ -221,13 +221,13 @@ i830_bios_get_panel_mode(ScrnInfoPtr pSc
_H_SYNC_OFF(timing_ptr);
fixed_mode->HSyncEnd = fixed_mode->HSyncStart +
_H_SYNC_WIDTH(timing_ptr);
- fixed_mode->HTotal = fixed_mode->HDisplay +
+ fixed_mode->HTotal = fixed_mode->HSyncEnd +
_H_BLANK(timing_ptr);
fixed_mode->VSyncStart = fixed_mode->VDisplay +
_V_SYNC_OFF(timing_ptr);
fixed_mode->VSyncEnd = fixed_mode->VSyncStart +
_V_SYNC_WIDTH(timing_ptr);
- fixed_mode->VTotal = fixed_mode->VDisplay +
+ fixed_mode->VTotal = fixed_mode->VSyncEnd +
_V_BLANK(timing_ptr);
fixed_mode->Clock = _PIXEL_CLOCK(timing_ptr) / 1000;
fixed_mode->type = M_T_PREFERRED;


I can understand that - means remove and + means add the lines to the file i830_bias.c file in /src/ directory. But i dont know where to see the SRC directory. (find -name command doesn't work for me ). I asked for help but no one responded - So i dont know how to fix the patch on my hardy.

So I followed the other way - I wanted to solve this bug in the way it was solved originally at freedesktop.org see this link [http://bugs.freedesktop.org/attachment.cgi?id=21911](http://bugs.freedesktop.org/attachment.cgi?id=21911)

and the bug link is this -
[http://bugs.freedesktop.org/show_bug.cgi?id=18342](http://bugs.freedesktop.org/show_bug.cgi?id=18342)

I downloaded the fresh xf86-video-intel-2.6.0 (2008Q4 release) from the [www.intellinuxgraphics.org](www.intellinuxgraphics.org). I could see the i830_bios.c file in the src folder after i extracted the tar file. **I was happy as I could locate the file i830_bios.c here** So i wanted to install this Intel driver manually. I think presently hardy has the 2.4.* version of intel drivers. **The most important thing is that i830_bios.c is already updated form my AUO LCD**

In order to install xf86-video-intel 2.6.0 (Q4 2008 - Latest release) i did all these things and got these errors :-(. 

If you can suggest a way of installing this driver - it would be very helpful. I have installed libdrm 2.4.4 necessary for this driver.

thx
b.

---

### Post by Yellow Pasque on 2009-01-20
You need libpixman-dev, and you'll probably need a lot of other -dev packages. Hopefully, this command will get most of the dependencies:
```
sudo apt-get build-dep xserver-xorg-core
```

---

