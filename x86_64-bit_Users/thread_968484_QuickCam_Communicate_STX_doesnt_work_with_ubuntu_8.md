---
title: "QuickCam Communicate STX doesnt work with ubuntu 8.10 (64bits)"
date: 2008-11-02
forum: x86 64-bit Users
---

### Post by Prisma on 2008-11-02
I have a QuickCam Communicate STX, it was working perfectly with Ubuntu 8.04. Now that I have upgraded to 8.10 it does not work anymore either with Egika, skype or amsn. I am using the 64bits version of Intrepid Ibex. The wierd thing is that I also did an upgrade on my wife's laptop form 8.04 to 8.10 (32 bits) version but on her computer her webcam which is another logitech works perfectly.

Is this a known bug in the 64bits version of Ibex? does anyone knows a work around? :confused:  

Thank you guys.

---

### Post by ShelJ on 2008-11-02
I'm having the same problem here, along with Skype and aMSN, mine was also working with Gyachi, but now isn't.  I'm using Quickcam Sphere.

---

### Post by loell on 2008-11-02
i think the driver needs to be compatible with libv4l, now that it has become the common API to be used for all the webcam apps.

---

### Post by Yellow Pasque on 2008-11-03
Check to see if the kernel module is loaded with:
```
lsmod | grep spca
```

This site might help you:
[http://www.quickcamteam.net/](http://www.quickcamteam.net/)

---

### Post by Prisma on 2008-11-04
Thank you guys for your help. Temüjin, after running the command this is what i get:

```
gspca_zc3xx            59520  0 
gspca_main             33536  1 gspca_zc3xx
compat_ioctl32         18176  1 gspca_main
videodev               46720  2 gspca_main,compat_ioctl32
usbcore               175376  11 usb_storage,usblp,libusual,snd_usb_audio,snd_usb_lib,gspca_zc3xx,gspca_main,usbhid,ehci_hcd,ohci_hcd

```

---

### Post by Yellow Pasque on 2008-11-04
The proper kernel module is loaded. It looks like you may be affected by the bug reported here:
[https://bugs.launchpad.net/ubuntu/+source/gspca/+bug/291723](https://bugs.launchpad.net/ubuntu/+source/gspca/+bug/291723)

---

