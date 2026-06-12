---
title: "FYI amd64 users with built-in Intel chip"
date: 2005-12-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by nalmeth on 2005-12-17
For a reason I could not figure out to my fair efforts, the amd64 version of breezy 5.10 did not detect / setup my graphics card, and I could not enable it thereafter. 
I performed *dpkg reconfigure xserver-xorg* and found the default was already set for the correct (i810) driver, and all 3D-components were enabled as requried. OpenGL was supposedly enabled, but froze when queryed, and 3D never worked after 2 reinstalls.

On i386 however, my card and driver were enabled 'out-of-the-box'. 
I must assume that the driver was simply not fully supported for amd64 architecture.

No loss (except time as always) because every thing 32-bit runs just fine on my 64-bit processor.

No one else seemed to run into this, but I post it anyway.

Here is my comp setup:

GA-8I915ME-GL
Intel 915GL / ICH6
P4 Socket775 / Micro ATX
3 GHz Intel Pentium 4 630+


BTW

is there a more appropriate place to post this?

---

