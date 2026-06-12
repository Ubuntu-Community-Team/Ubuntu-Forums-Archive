---
title: "Need help with GeForce 8200"
date: 2008-12-06
forum: x86 64-bit Users
---

### Post by marcelkoopman on 2008-12-06
Hi,

I've got my brand-new Acer Aspire X3200 which has a AMD Phenom Quad Core.

Nice and all, but I cant seem to get the nvidia-glx-177 to work.

I've tried it with the enable restricted drivers, and manually installing.
It loads ok as a module, but X says no device found.

Do I need to enable/disable SLI? Or anything else?

Any tips would be great, thanks!

---

### Post by marcelkoopman on 2008-12-07
I've solved it.

What was missing is the BusID in my xorg.conf.

Here's how you can:

lspci | grep VGA

My output was:
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8200 (rev a2)
03:00.0 VGA compatible controller: nVidia Corporation Device 06e0 (rev a1)

Then add to xorg.conf:

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    **BusID          "03:00:0"**
    VendorName     "NVIDIA Corporation"
EndSection

---

### Post by BlackDex on 2009-01-12
Thx for the tip.
I'm going to try this when i am home.
Would be nice if this can be fixed by default.

---

