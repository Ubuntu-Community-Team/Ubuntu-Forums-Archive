---
title: "Ubuntu won't boot after activating a driver??"
date: 2009-11-05
forum: x86 64-bit Users
---

### Post by Luffypsp on 2009-11-05
i just successfully dualbooted windows 7 and ubuntu 9.10 a couple of days ago. Today i got a notifications saying that i have a driver needed to be activated. Its my nvidia graphic card driver. Then i click activate. After finished downloading and installing i was asked to reboot my pc for the changes to take effect. i did and lolz the usual balck screen appears but it keeps on flickering with words(my username and login) non-stop. I cant boot into it anymore. Why is it? Somebody help...i need help ASAP...

I'm using the 64-bit ubuntu 9.10. is it because the driver is incompatible that it appeared to be like that? if so, can i just re-install the 32-bit version over it without messing with my windows 7? if i did, it wont mess my GRUB loader options right?

---

### Post by sadahalli on 2009-11-07
The installation of the video card drivers may not have occured properly.

Login to the recovery mode and do the follwing

sudo dpkg-reconfigure xserver-xorg

(Select default selections)


This will load the default drivers and you should be able to login using GDM.

---

### Post by rallen71366 on 2009-11-07
This happened to me, also. I **tried** to login in recovery mode, but couldn't figure out how. Everything I tried failed. I wound up having to do a complete re-install. Twice.

Right now I'm running the default driver for the on-mobo VIA graphics chip, and 1024X768 looks like poo on a 22" Dell LCD that can do 1680 x 1050.

I'm running an MSI K9VGM-V mobo, with 1.5 GB ram, and AMD 5200+ X2 cpu, with NVIDIA GeForce 6200, 64-bit 9.10 Karmic.

If anyone has a fix, let me know. If this keeps up, my wife and daughter are going to make me downgrade back to 9.04.[-X

Thanks for any help.

---

### Post by sadahalli on 2009-11-07
To login to recovery mode, hold the 'Shift' button down for atleast 10s after the 'GRUB Loading' message shows up.

---

### Post by Luffypsp on 2009-11-10
Well i've reformatted my computer...lol...but didnt get the chance to try your solution.

btw, i didnt install ubuntu yet, so i wanna ask for opinions, should i go with 32-bit or 64-bit?

and 9.10 or 9.04?

---

