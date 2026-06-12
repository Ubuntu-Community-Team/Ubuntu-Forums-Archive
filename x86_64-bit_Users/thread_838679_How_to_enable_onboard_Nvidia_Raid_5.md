---
title: "How to enable onboard Nvidia Raid 5"
date: 2008-06-23
forum: x86 64-bit Users
---

### Post by pepsifx357 on 2008-06-23
I know there are threads that discuss this but i recently made a raid 5 array with 3 500 gig hard drives and have 300 Gigs of information on them. I wanted to know if there was a nondestructive way of being able to see and mount the array in Ubuntu 8.04 64 bit without loosing that information.

Thanks,
Ben

---

### Post by fjgaude on 2008-06-23
Yes there is, using a little program called **dmraid**, which is in the repositories.

You can qoogle it to find out how to use it under Ubuntu.

Let us know how you are doing.

---

### Post by pepsifx357 on 2008-06-23
Thank you for your reply, I tried installing it in synaptic but I didn't know how to run it or where to find the executable.  But before you post again i'll look it up and try again.

Thanks,
Ben

---

### Post by pepsifx357 on 2008-06-23
Ok, I tried with Gparted but I didn't want to do anything because i was scared i might lose data.  I wanted this raid to work with Ubuntu as well as a dual boot windows installation.  can someone help me out with the step by step on how to make it work with both OS's without losing data?

thanks,
Ben

---

### Post by fjgaude on 2008-06-23
Okay, you don't do anything to the drives in the raid array. All you do is at the command line:

```
sudo dmraid -ay
```

There you will see something like /dev/mapper/nvidia_nnnnnnnnn

This piece is what you do to mount the array, and later put a line in your /etc/fstab file so that it comes up when you boot into Ubuntu. It becomes automatic.

If you need more let us know.

---

### Post by pepsifx357 on 2008-06-23
When I put in the code sudo dmraid -ay I get:
/dev/sde: "pdc" and "nvidia" formats discovered (using nvidia)!
RAID set "nvidia_fdcedcbe" already active
RAID set "nvidia_eabbjhdf" already active
RAID set "nvidia_fdcedcbe1" already active
RAID set "nvidia_eabbjhdf1" already active

But the array is still not showing in the browser.

There are Five hard drives in my computer three 500gigs in raid 5 Nvidia port 1,2, and 3, One 260 gig on SATA port 4 and my boot drive located on another controller all together.  The 260gig drive is showing in the browser but won't mount.

I'm still kinda new to linux but I thank you for your help...

thanks,
Ben

---

### Post by fjgaude on 2008-06-23
I don't wish to install dmraid on my present computer and don't dual boot into Windows anymore. What you get from the **-ay** command means something is missing... no **/dev/mapper** there. That's how you mount the array. I'm not sure you can work with raid5, only raid0 and 1, as I recall. Sorry about that, but the lastest kernel may handle it.

Try some study of **man dmraid** and this link:

[http://forums.gentoo.org/viewtopic-t-691559.html](http://forums.gentoo.org/viewtopic-t-691559.html)

What you are doing is very complex, and few do it, AFAIK. But it can be done.

Good luck.

---

### Post by pepsifx357 on 2008-06-23
Thank you for your help fjgaude.

---

### Post by fjgaude on 2008-06-23
We try, and you are welcome!

---

