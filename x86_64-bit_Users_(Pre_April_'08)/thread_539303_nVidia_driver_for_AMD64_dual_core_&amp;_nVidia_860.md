---
title: "nVidia driver for AMD64 dual core &amp; nVidia 8600"
date: 2007-08-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by CD Baric on 2007-08-31
I have installed Ubuntu 64 bit but am unable to get nVidia driver running for nVidia 8600 chipset.

I am running an AMD 64 dual core 6000+ CPU, 4 gig memory and Asus 8600EN dual DVI output video card. 

Any help appreciated.

Thanks,

CD Baric

---

### Post by gtdaqua on 2007-08-31
there is a command line utility to get the nvidia drivers downloaded

I did something like this on my AMD64 X2 - Nvidia Quadro:

#sudo apt-get nvidia-glx

Sorry I cant remember the exact commands. Try here:

[http://ubuntuforums.org/showthread.php?t=57368]("http://ubuntuforums.org/showthread.php?t=57368")

---

### Post by CD Baric on 2007-08-31
Thank you very much.

That gave me a path to upgrade to the latest nVidia driver.

One thing I had to do was after installing the new driver, I had to remove the earlier drivers from the restricted drivers section of /lib/kernel-version

Thanks again for your help.

CD Baric

---

