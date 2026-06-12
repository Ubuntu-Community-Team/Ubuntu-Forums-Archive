---
title: "can't boot from usb stick !!!! help!!!!"
date: 2008-09-02
forum: x86 64-bit Users
---

### Post by x_error on 2008-09-02
hey everyone I'm  a new Linux user and I'm satisfied with Ubuntu and its features and the easy management of repositories and the stuff , so i downloaded the Ubuntu iso image and using "unetbootin" (which burns the image to the usb) i made my usb stick bootable and i have an DG965RY intel motherboard which allows usb stick boot but after i completed everything and rebooted my computer i got a message saying  "boot error " why !!! it is supposed to boot ubuntu live cd package ? is there a problem with "unetbootin" ?if yes is there other software to boot from usb ? please i need to boot from my usb stick because iam now a new Linux user and I'm downloading too much linux distributions so i cant every now and then  burn a cd and boot it, also booting from a usb stick is a better idea please i need your help  !!!

---

### Post by trobn76 on 2008-09-02
x_error I can't help you much with your specific problem, but I can tell you what I've done to boot from a USB drive.

I downloaded Ubuntu 8.04 (64bit ver.) and then I burned it to a CD so I could boot from the CD. 

Then I turned off my computer and unplugged all my hard drives and plugged in a regular USB stick (Kingston data traveler 4GB). 

I booted up from the Live CD and cliicked on the install option from the CD and did a guided install on my USB drive (the only drive available). It took a while and then, when I was done I restarted and entered the setup for my Motherboard (BIOS) and I made sure the boot device priority to be floppy 1st and then I selected my USB drive as the second boot device and my CD/DVD drive as my third boot device.
I have an Asus P5K and that is specific to my BIOS but you should have something similar.

The caveat to you probably is that if you mobo can't recognize your USB drive at POST, you'll have a much harder time booting from a USB. Mine shows up when I enter BIOS setup and I have no trouble starting up from my USB drive.

As soon as I had installed on my USB drive and reset my BIOS boot priority then I started up just like a normal computer with Ubuntu installed.

Hope this helps

---

