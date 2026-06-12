---
title: "asrock939a8x-m &amp; UbuntuLinux"
date: 2005-09-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by XaRP1Sh87g on 2005-09-08
I recently upgraded my mobo to an asrock939a8x-m (64bit). I have had three problems, sofar.
1. When installing ubuntu64 the installer refuses to detect my on-board network device (Realtek 8201BL). The only way I can 'outwit' this, is by adding a pci ethernet card. Obviously this is no solution.

2. I also have an onboard sata-controller and a single disk connected to it. Now with my 32bit mobo, I used a pci controller card, and the disk worked fine and was fast (dma worked). Now, with my new board, I cannot add the pci controller card. When connected to the onboard controller, the disk 'works', but not very fast (no dma).
I dual boot to windowsxp 64, with which I had exactly the same problem, the disk was there, worked, but way too slow, until I reinstalled windows and added "third party drivers" (from asrock) during setup. How do I achive similar using linux? I am running a custom kernel, so I know that the support is there via modules, should I maybe change this?

3. During bootup,I get the error "cannot access the hardware clock in any known way" or something similar. The time then runs 2hours fast. My hardwareclock (bios) is set to my local time. I have set my timezone correctly within Ubuntu, and also made shure to set 'no utc'. Because the time sync during bootup nearly always failed, I disabled it altogether. My problem lies when I reboot, as it saves the false time to the hardware clock (2hours+) and of course will add 2 more hours on next reboot, if I don't reset the time in the bios... So is there a way, to either enable 'linux' to access my hardware clock, or to prevent it from writing to it (this is a paradox!?) when the system goes down?

ThanX in advance for any help!

---

