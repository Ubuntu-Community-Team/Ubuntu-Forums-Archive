---
title: "White Moving lines on ATI Radeon HD 3200 !!"
date: 2009-03-20
forum: x86 64-bit Users
---

### Post by PuppetMaster2070 on 2009-03-20
I love ubuntu 64 bit but I have a major problem with my graphical card
ATI HD3200
when I put it's restricted driver it shows me some annoying moving line along the screen

I have an AMD PHENOME X3 8450 AND GIGABYTE GA-MA78GM-US2H
AND SAMSUNG WIDE SCREEN 18.5 INCH 15000:1 dynamic contrast

I'd be very glad if my problem solved

and Thank u in advance

---

### Post by PuppetMaster2070 on 2009-03-20
By the way I'm using ubuntu 8.10
thanks

---

### Post by racerraul on 2009-03-21
What drivers are you using?

I have tried the open source FGLRX & ATI 9.2 and didn't have those issues, but I felt the hardware acceleration sucked so I bought an nvidia card.

Both drivers struggled with Compiz effects and Java 3D apps.  Really disappointed with ATI drivers.

All that said, if an nvidia card is not a possibility...

- Check hardware drivers (jockey) & see if you are running restricted drivers... if you are disable them.  It should default to the open source fglrx drivers, if not, install them via SPM. (xorg-driver-fglrx)

- If you are on the xorg-driver-fglrx, try enabling the restricted drivers via hardware drivers (jockey)

If neither one of those options work (in my experience, they didn't work with games either) then try the latests ATI drivers.

To install them, download them from AMD/ATI.
- Disable restricted drivers in use in Hardware Drivers (Jockey)
	- reboot
	- Download AMD\ATI drivers and the install docs\pdf from [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English)

	- after installation is done in terminal session
	- sudo aticonfg --initial -f
- reboot

If that don't work... buy an nvidia card cause IMO... ATI driver support is bad with Windows, but it is WORSE with Linux :)

Linux vets gimme a break... if the reboots are not needed, show me what to do instead. I'm a Windows admin by trade and some habits are hard to break ;)

---

### Post by PuppetMaster2070 on 2009-03-22
Thanks 4 quick reply but I'm having the same problem 

I hope I find a solution soon

---

### Post by PuppetMaster2070 on 2009-03-22
Thanks 4 quick reply but I'm having the same problem 

I hope I find a solution soon

---

### Post by robpick on 2009-03-24
I'm in the same boat.  I've got an Asus M3A78-EM with the HD 3200as well.  My TV is a SHARP 32".  I haven't tried the proprietary drivers from AMD/ATI yet.  I'll post those results when I get them.  Please post your results if you find a resolution.

---

### Post by zika on 2009-03-24
> **racerraul said:**
> Linux vets gimme a break... if the reboots are not needed, show me what to do instead. I'm a Windows admin by trade and some habits are hard to break ;)
I'm not a vet (at least not Ubuntu one) but this time You were right. reboot is needed. :) this goes to show that *ux and win* can cohabit ... :)

---

