---
title: "Install Ubuntu using external Display on Titanium Powerbook"
date: 2006-03-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by koni2005 on 2006-03-12
Since the internal Display of my Titanium Powerbook (1Ghz, ATI Radeon 9000) is broken, I'm using it as a desktop with an external display and keyboard attached. Wich works fine with OS X.

How can I make Ubuntu use the external monitor instead of the internal display as main display during the installation from CD or the boot process?

Thanks...

---

### Post by BoneKracker on 2006-03-12
I don't know, but since no one else has answered, I'll tell you what my first thoughts would be if I had to figure this out.

During the boot process, when you are initially booting from the OpenFirmware, and before the handoff to the installer CD occurs, you may need to include boot options that instruct Linux to use the external display and where to find it.

There are some guys in here that know a lot about this stuff and may jump in and help you.  But I'd start by researching OpenFirmware, its boot process, and how to pass parameters manually during the boot process.

I hope I'm not steering you wrong.  I just hate to see anybody waiting for an answer in here longer than a day.

---

### Post by koni2005 on 2006-03-13
Thanx a lot BoneKracker!

I'll look into the OpenFirmware options. Sounds viable to me - maybe I'll get it to work this way. Although I'm not too optimistic, as I'm no real expert with apples OpenFirmware mode...

Anyways, if there is someone out there who knows exactly what to do to make the external display the main display - even just mirroring the laptops internal display - during the boot process of Ubuntu, I'd very much appreciate a hint...

Thanks!

---

### Post by koni2005 on 2006-03-15
As nobody seems to have an answer I guess I will be stuck with OS X until I buy another computer before I can move back to Ubuntu. Too bad!!! Basically I don't mind using OS X too much though (It is a great Operation System and works flawlessly, but it is not as cool as a good linux distrib like ubuntu - and I'd like to support the Open Source community)

---

### Post by ssam on 2006-03-15
hi.

sorry this is a tricky question.

a common way of installing onto headless machines is to use a serial console. i dont know the exact details (or whether ubuntu can be installed using a serial console). you would probably need a usb-serial adapter  (which i believe are well supported) and another computer.

another possibility would be to find a similar powerbook (it would probably need to have the same graphics card), install ubuntu on that, set up the display to the external monitor and then image the partition. then you use mac os x to put the image onto a partition and reboot. it may still be tricky to set up the bootloader, though if you can see the openfirmware it should be possible.

---

