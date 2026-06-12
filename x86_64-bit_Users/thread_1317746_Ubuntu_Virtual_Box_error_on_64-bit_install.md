---
title: "Ubuntu Virtual Box error on 64-bit install"
date: 2009-11-07
forum: x86 64-bit Users
---

### Post by mplsgrl on 2009-11-07
Hello everyone, 

I have been trying to install Ubuntu 9.10 on vm created with virtual box. I Created the vm just fine, downloaded the iso to hard-drive went to start the vm and then I received this message. 

[B]Virtual Box Error Message
VT-x/AMD-V hardware acceleration has been enabled, but is not operational. Your 64-bit guest will fail to detect a 64-bit CPU and will not be able to boot. 

Please ensure the you have enabled VT-x/AMD-V properly in the BIOS of your host computer. [/B]

I am new to Ubuntu this will be my first install and I was told to install it on a VM machine first and I do not know how to "enable VT-x/AMD-V properly in the BIOS of my host computer"

Any assistance will be so greatly appreciated. 

Thank you all in advance.

---

### Post by aurelieng on 2009-11-07
Well, if you just want to give Ubuntu a try, why not installing the 32bit version ? The major advantage of the x86_64 over the x86 is its ability to manage more that 4Go of RAM, which will probably not be the case since you are working in a virtual machine.

Then, if you like it, you can perform a real installation of Ubuntu x86_64, either by partitioning your disks, or using Wubi.

---

### Post by mick55 on 2009-11-07
hi mplsgrl

It means VT-x/AMD-V hardware acceleration has been enabled in Virtualbox,
but it is not enabled in your computers BIOS.

To enable in your PC's BIOS you need to reboot your PC and enter setup.
There should be a brief message when you boot asking you to press
del or F1 or F10 or some other key combination to enter setup.

But, instead of installing in a virtual machine you could burn the ISO
to Cd and boot to it and run the live CD.
If you can't run Ubuntu as a live CD on your PC,
there's no point in installing it.

Live CD really is the way to go if you want a real world test.

Virtualbox uses virtual drivers so it will not accurately reflect the 
performance you will have.

If you do decide to install it as a dual boot system, make sure 
you create/shrink the new partition with Vista's built in tool.

good luck
mick

---

