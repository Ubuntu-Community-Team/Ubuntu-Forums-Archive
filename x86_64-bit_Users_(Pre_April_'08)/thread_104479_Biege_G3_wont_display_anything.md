---
title: "Biege G3 wont display anything"
date: 2005-12-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by TheMaskedMuchacho on 2005-12-16
I have been trying for the past few days to get Ubuntu 5.10 to install on my biege G3 DT (rev a, 400mhz, 512mb, Radeon 7000 pci). The first stage went ok although i got no display untill the menu appeared asking me to choose language. I copied the kernel and initrd.img to a usb stick then to the required locations for bootx to use but when i try to start using bootx i get the usual welcome to linux screen and then nothing, just sticks at that screen. If i use the no video driver option and the ramdisk copied from the installed system the screen goes black after a few seconds and i can hear it booting but cant see a thing, nothing ever appears on screen. I have tried using video=radeon:1024x768@75 (a few other resolutions too) also tried the onboard rage2 but same thing happens. i have tried all bootx options but nothing works and its driving me crazy :confused: I hope one of u fine people can help me out, im new to this but i never give up. i have searched the forums but cant find anything that helps. :(

My system:

Rev A Beige G3 DT.
400mhz G3 (from B&W)
512mb SDRAM
Radeon 7000 PCI 32mb (bought on ebay, expect its a modified PC card)
10gb seagate HDD master on internal IDE (1.5gb for OS9.22 rest for linux)
18gb Fujitsu SCSI HDD on Adaptec 1940UW (dedicated to OSX 10.4.3)
Via chipset USB2.0 pci card (doesnt work in os9)
LG DVD/CDrw combo.

---

### Post by TheMaskedMuchacho on 2005-12-16
:(  Anybody?

---

### Post by nkbj on 2005-12-17
I have the exact same problem with my G3 (Beige rev. A 300MHz MT). The only difference is that my graphics card is a IMS tt128mb8 PCI. :(

---

### Post by teripittman on 2005-12-24
I've gotten the onboard video card to work on two older G3s. An separate PCI video card would not work. There are drivers floating around that might help, but it didn't seem worth the effort to me.

---

### Post by nkbj on 2006-01-10
[QUOTE=teripittman]I've gotten the onboard video card to work on two older G3s. An separate PCI video card would not work. There are drivers floating around that might help, but it didn't seem worth the effort to me.[/QUOTE]

I've managed to install Breezy on the G3 using the onboard video card and a Mac-to-VGA adapter. It works perfect except for a lot of screen flicker at the framebuffer during bootup and shutdown. Gnome is rock solid though.

Regards,
Niels Kristian

---

