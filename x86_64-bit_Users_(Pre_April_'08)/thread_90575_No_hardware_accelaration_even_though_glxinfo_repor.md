---
title: "No hardware accelaration even though glxinfo reports so"
date: 2005-11-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by nidhikv on 2005-11-15
Hi,
    I am having a weird problem with getting hardware acceleration to work. I have the MSI RS480 motherboard with onboard graphics. I recently installed the AMD64 breezy badger release. I have installed the ati drivers using 
    sudo apt-get install xorg-driver-fglrx

    I now have working X, but no 3D acceleration.

Now, when I do a fglrxinfo, I get:
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS 200 Series SW TCL Generic
OpenGL version string: 1.3.5272 (X4.3.0-8.16.20)

When I do a glxinfo | grep direct, I get
direct rendering: Yes

But when I do, glxgears, the frame rate is hopelessly poor.
quake3 again complains of not able to load the open gl subsystem.

I don't know what's wrong with the config. Can anybody please help me?

---

### Post by RAOF on 2005-11-15
I would trust fglrxinfo & glxinfo over the output of glxgears.  I would suspect you **do** have 3D acceleration.

However, Quake 3 doesn't work...  Is this a 32bit version of quake3?  It's possible that the 32bit OpenGL libraries haven't been installed correctly by the driver, so quake can't find them.  I wouldn't know how to fix this - I don't have an ATI card to test, but there are any number of ATI-wielding 64bit users here, maybe they can help.

---

### Post by DRF on 2005-11-16
There is a known problem that appeared shortly before breezy was released that seems to have effected many of the AMD64 ATI computers.

There is a fix at this location:
[http://ati.cchtml.com/show_bug.cgi?id=198](http://ati.cchtml.com/show_bug.cgi?id=198)

Go to post number 4 and download the libdri.a file (the link is called: "Created an attachment (id=182)" which is quite confusing but I think thats the corrrect download.) there are the install instructions there also. This should help to sort out your problem. (this fix should be made easier to find really)

If you have any further problems feel free to ask, I suspect though that this might solve your problem.

Daniel

---

