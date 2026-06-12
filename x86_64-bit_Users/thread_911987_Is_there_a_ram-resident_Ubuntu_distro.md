---
title: "Is there a ram-resident Ubuntu distro?"
date: 2008-09-06
forum: x86 64-bit Users
---

### Post by chackoc on 2008-09-06
I'm trying to build a completely silent, fast desktop.  With the high memory limits of 64-bit computers I'd like to find an Ubuntu distro that runs entirely from ram, but still provides all of the functionality that I get from a normal Ubuntu distro.  Does anyone know of anything like that? 

My end goal is to run completely diskless.  Have the computer boot off the network via PXE and then from there run entirely in ram.  Since it's running in RAM i assume it would be very fast, and since the machine won't have a disk I could get it down to know moving parts at all.

If no one knows of any distros off-hand, can someone suggest search terms I can use in Google?  I've been using various combinations of "pxe", "diskless", "ram resident", etc. but I haven't had much luck.  Am I even on the right track, or would the correct approach be to somehow modify an existing distro so that it runs completely in memory?

Is what I'm trying to do even doable?  If not I can go the SSD route, but I really like the idea of running everything directly from ram.

Also, I don't need a powerhouse computer.  The biggest load this computer will face is playing back HD video, and that will be with help from the video card.

---

### Post by kjohansen on 2008-09-06
puppy linux can do this.

[http://www.puppylinux.org/home/overview](http://www.puppylinux.org/home/overview)

As a side note:
the cost of steady state drives is decreasing

---

### Post by chackoc on 2008-09-06
Thanks kjohansen.  Do you know how good the package management system in puppy is?  I've grown quite fond of apt and the available ubuntu/debian repositories.  

Is it an Ubuntu variant?  I saw reference to "gslapt.pet" which sounds similar, but not quite the same as apt-get.  

In any case I'll take a more detailed look at it.

---

### Post by kjohansen on 2008-09-06
it is NOT an ubuntu variant

There is a package manager:
[http://www.puppylinux.org/manuals/puppy-40/english/how-install/deinstall-programs/how-install-official-programs](http://www.puppylinux.org/manuals/puppy-40/english/how-install/deinstall-programs/how-install-official-programs)

---

