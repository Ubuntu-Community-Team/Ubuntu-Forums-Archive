---
title: "no reference in xorg.conf section device"
date: 2007-01-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by gostview on 2007-01-07
Hi all, I've just installed a GeForce 6 series on my ubuntu amd64, the kernel in use is the 2.6.17-10-generic. 
and I use the command  sudo sh NVIDIA-Linux-x86_64-1.0-8776-pkg2.run -n -s --x-prefix=/usr/lib64/xorg/ --kernel-source-path=/usr/src/linux-headers-`uname -r` for install it.

So, the question is:
why the Device section doesn't reference the GeForce 6200 explicitely, in xorg.conf Section Device?
=======================================================
Section "Device"
    Identifier     "NVIDIA Corporation NV40? [Unknown nVidia Card]"
    Driver         "nvidia"
EndSection
=======================================================

if the answer is that the GPUs are enumerated by the NVIDIA Linux kernel module, could a 2.6.17-10 kernel give this kind of problem? is that unstable?

again, someone tells to me that the NVIDIA X driver will use the first of those GPUs if there's a single Device section without an explicit BusID.
There's a method to say to GPUs how to recognize this BusID? or isn't that a problem for a good functionality of the graphic card?

Thanks for any advise.

](*,)

---

### Post by kuja on 2007-01-07
So long as it works and performs as expected, don't worry about what it calls itself.

---

