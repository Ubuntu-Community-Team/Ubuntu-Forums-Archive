---
title: "how to restart a usb device like you unplugged it?"
date: 2009-11-02
forum: x86 64-bit Users
---

### Post by outleradam on 2009-11-02
I need to restart a USB device after I come out of standby.  For some reason it is not doing it correctly.  My device works fine if I unplug it and plug it back in.  Is there a way I can make the device reinitialize?

---

### Post by bigbroantonio on 2009-11-03
I remember using

[B]sudo rmmod rt73usb
sudo modprobe rt73usb[/B]

to get my wifi usb to work after standby in 9.04.  I made a link to this little script and added it to my main panel.  After installing Karmic this was no longer necessary.

It should be just a matter of working out which module you should remove and then reactivate... I think...

Hope this helps!

---

