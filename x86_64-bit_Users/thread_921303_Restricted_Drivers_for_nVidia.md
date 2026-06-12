---
title: "Restricted Drivers for nVidia"
date: 2008-09-16
forum: x86 64-bit Users
---

### Post by argie on 2008-09-16
The restricted drivers manager doesn't seem to list my nVidia 8400M GS in it. I'm using the LiveCD, I haven't installed Ubuntu because I don't want to use it if the drivers can't be installed. This means installing nvidia-glx or nvidia-glx-new is out of the question.

One more thing, there appears to be a bug with nvidia-glx on the 64-bit version, it keeps trying to remove libGL.so.1 from the libs32 folder somewhere (I can't remember, tried this yesterday) when you try uninstalling it. As a result, nothing can be installed once you install nvidia-glx because removing that will make the package manager exit saying that it failed to remove libGl.so.1.

Will things be different if I install? I really want a hardware accelerated desktop (I loved using Compiz on my older laptop with Intel graphics, surely it should be less taxing on this graphics card).

Thank you.

---

### Post by techstop on 2008-09-16
> **argie said:**
> The restricted drivers manager doesn't seem to list my nVidia 8400M GS in it. I'm using the LiveCD, I haven't installed Ubuntu because I don't want to use it if the drivers can't be installed. This means installing nvidia-glx or nvidia-glx-new is out of the question.

<SNIP>

Will things be different if I install? I really want a hardware accelerated desktop (I loved using Compiz on my older laptop with Intel graphics, surely it should be less taxing on this graphics card).

Thank you.

You can download the latest driver directly from Nvidia here;

[http://www.nvidia.com/object/linux_display_amd64_173.14.12.html](http://www.nvidia.com/object/linux_display_amd64_173.14.12.html)

The 8400GS is supported. You can install it by following my guide here;

[http://techstop.com.au/2008/05/hardy-nvidia-beta-drivers/](http://techstop.com.au/2008/05/hardy-nvidia-beta-drivers/)

It's very easy. I have to use this method rather than ubuntu's driver from the repository for my 9600GT. The only drawback is that you have to (re)install the driver whenever the kernel gets updated. No big deal, takes about 1 minute in total.

Alternatively you could try Envy;

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

Not sure why the 8400GS is not showing in restricted drivers, I thought it was supported. You can definitely install the latest driver directly from Nvidia though (either manually or by using the Envy script).

---

### Post by Doppelgamer on 2008-10-13
> The 8400GS is supported.
It looks like the 8400**M** isn't supported, though. Even under Vista, you're supposed to get the drivers from Dell's website. I just put Ubuntu 8.04.1 on my xps M1330, also with the 8400M GS, and I'm still looking for what to do about drivers.

---

### Post by techstop on 2008-10-14
> **Doppelgamer said:**
> It looks like the 8400**M** isn't supported, though. Even under Vista, you're supposed to get the drivers from Dell's website. I just put Ubuntu 8.04.1 on my xps M1330, also with the 8400M GS, and I'm still looking for what to do about drivers.

The 8400M GS is supported according to this list;

[http://us.download.nvidia.com/XFree86/Linux-x86_64/173.14.12/README/appendix-a.html](http://us.download.nvidia.com/XFree86/Linux-x86_64/173.14.12/README/appendix-a.html)

My previous post still stands. Follow either of those two methods to install the driver.

---

### Post by argie on 2008-12-11
Everything suddenly came together. Apparently, at least for 64-bit, when you use the LiveCD, installing nVidia restricted drivers doesn't work. Installing it on the hard-drive worked.

---

### Post by stchman on 2008-12-11
> **argie said:**
> The restricted drivers manager doesn't seem to list my nVidia 8400M GS in it. I'm using the LiveCD, I haven't installed Ubuntu because I don't want to use it if the drivers can't be installed. This means installing nvidia-glx or nvidia-glx-new is out of the question.

One more thing, there appears to be a bug with nvidia-glx on the 64-bit version, it keeps trying to remove libGL.so.1 from the libs32 folder somewhere (I can't remember, tried this yesterday) when you try uninstalling it. As a result, nothing can be installed once you install nvidia-glx because removing that will make the package manager exit saying that it failed to remove libGl.so.1.

Will things be different if I install? I really want a hardware accelerated desktop (I loved using Compiz on my older laptop with Intel graphics, surely it should be less taxing on this graphics card).

Thank you.

The package nvidia-glx-177 supports the 8400M GS.

[http://packages.ubuntu.com/intrepid/nvidia-glx-177](http://packages.ubuntu.com/intrepid/nvidia-glx-177)

---

### Post by stchman on 2008-12-11
> **argie said:**
> Everything suddenly came together. Apparently, at least for 64-bit, when you use the LiveCD, installing nVidia restricted drivers doesn't work. Installing it on the hard-drive worked.

Yes, the nvidia glx drivers modify the kernel requiring a reboot.  The LiveCD does not support Nvidia cards OOB to my knowledge.

---

