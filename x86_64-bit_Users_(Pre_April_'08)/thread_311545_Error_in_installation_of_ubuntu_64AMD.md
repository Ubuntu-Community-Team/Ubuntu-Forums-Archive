---
title: "Error in installation of ubuntu 64AMD"
date: 2006-12-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by blockdude14 on 2006-12-03
I have a problem with installation of Ubuntu AMD64... some how as soon as the desktop setup starts the screen gliches and then freezes. I am a beginner and I don't know what to do next?

**The current state of comp. is: **
**ANTEC 550W TRUEPOWEER TRIO SLI READY**- POWER SUPPLY 
**AMD ATHLON 64 X2 3800 DUAL CORE SOCKET 939**- PROCESSOR 
**ASUS A8N32-SLI DELUXE**- MOTHEROBOARD 
**GEFORCE 7800 GT OC PCI EXPRESS 256MB GDDR3 SLI READY**- GRAPHICS CARD

---

### Post by taurus on 2006-12-03
Move to AMD64 section...

---

### Post by hainesr on 2006-12-04
Have you tried the "alternate" install CD? It doesn't boot to a desktop before installing so might be more suitable.

I have a very similar setup to you (motherboard slightly different - I've got a M2N32-SLI Deluxe - but same graphics card) and the alternate CD worked first time.

Cheers,
Rob

---

### Post by tuxramone on 2006-12-04
My english is not good but i will try to hekp you :)

When start the live cd /installation press F6 (advanced options) and add 

**break=bottom**

wair for initramfs .. the you must type

mv /root/etc/X11/xorg.conf /root/etc/X11/xorg.conf.disabled


NOw you can login with graphical interface to livecd / ubuntu graphical installation..

if yoy want to install permanently Ubuntu now you must to create a temporal working xorg.conf.

the easy way is sudo gedit /etc/X11/xorg.conf.disabled

replace the "nvidia"  for "vesa"  in the screen section (not sure but is easy to find) and write the file as xorg.conf  

now you can install unbutu  with nvidia and pci-express

good luck :)





> **blockdude14 said:**
> I have a problem with installation of Ubuntu AMD64... some how as soon as the desktop setup starts the screen gliches and then freezes. I am a beginner and I don't know what to do next?

**The current state of comp. is: **
**ANTEC 550W TRUEPOWEER TRIO SLI READY**- POWER SUPPLY 
**AMD ATHLON 64 X2 3800 DUAL CORE SOCKET 939**- PROCESSOR 
**ASUS A8N32-SLI DELUXE**- MOTHEROBOARD 
**GEFORCE 7800 GT OC PCI EXPRESS 256MB GDDR3 SLI READY**- GRAPHICS CARD

---

