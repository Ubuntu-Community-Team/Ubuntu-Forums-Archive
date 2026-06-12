---
title: "Unable to load kernel 2.6.22 in Hardy"
date: 2008-08-04
forum: x86 64-bit Users
---

### Post by Noobuntu-qa on 2008-08-04
I am very new to Ubuntu but I did manage to successfully setup a Mythbuntu box... until a few months ago.  From what I can see, it appears that upgrading from kernel 2.6.22-14-generic to 2.6.24-19-generic broke several things.  As I am located in Taiwan and this Ubuntu box is located in the U.S. I am able to access the computer only via ssh/vnc, thus complicating matters.

MANY segfaults are shown frmo dmesg.  Most are caused by mythfrontend.  I believe this is due to my USB video encoder (Plextor ConvertX PX-TV402U) not being recognized by Ubuntu.  This began after a kernel upgrade.  I have rebuilt the driver for this encoder per the instructions here: [http://nikosapi.org/wiki/index.php/WIS_Go7007_Linux_driver](http://nikosapi.org/wiki/index.php/WIS_Go7007_Linux_driver) but this did not allow the video encoder to be recognized.  From reading many other posts, it appears that the only solution was to revert back to an older kernel.

Because I know the system was working with 2.6.24-19-generic and because this kernel option still appears in my GRUB menu, I attempted to boot from this kernel (by changing boot.lst to make 2.6.22-14 the default boot option, then forcing a reboot).  Despite changing the default boot option and rebooting, Ubuntu still boots into kernel 2.6.24-19.  I even removed the 2.6.24-19 options from boot.lst entirely but Ubuntu still boots into the newer kernel. I do have the following files present:
/boot/initrd.img-2.6.22-14-generic
/boot/System.map-2.6.22-14-generic
/boot/vmlinuz-2.6.22-14-generic

Can anyone tell me why I cannot boot into my older kernel (2.6.22-14)?
I have attempted to attach my dmesg file for reference but I am unable to do so.  I will try this in a second post.

--Greg

---

