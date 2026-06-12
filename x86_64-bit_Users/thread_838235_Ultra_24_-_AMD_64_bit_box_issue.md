---
title: "Ultra 24 - AMD 64 bit box issue"
date: 2008-06-23
forum: x86 64-bit Users
---

### Post by jonwh25 on 2008-06-23
Anyone out there have a Sun Ultra 24 box? 

It's pretty much an AMD chipset / 64 bit.

I have Hardy running on it (64 AMD) and it runs fine,

However my issue is that when I go to run Virtual Box I can't get the mouse to be "captured" I can manually set the USB portion since its a Sun Optical USB mouse. However when I go to press the host key It won't release the mouse. Once I shutdown the virtual box, the mouse never comes back. The only way I can get the mouse back is to boot the whole box. Very strange issue. 

Anyone know how to resolve this one?

---

### Post by pixel :-) on 2008-06-26
I'm understanding,that you connected your mouse as an usb device to virtuallbox.If the extra stuff are loaded in the guest os,then you have to "machine-->disable mouse integration".Normally it's just "right ctrl button(left will not work)+right mouse button".You mouse must be treated as the mouse of the host,not as a device.

Try this forum for more on virtualization [http://ubuntuforums.org/forumdisplay.php?f=308]("http://ubuntuforums.org/forumdisplay.php?f=308")

If the above problem persist,mouse doesn't comme bask,try removing,reinserting your mouse,try "ctl+alt back space" restarts X.

---

