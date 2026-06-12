---
title: "260 64 bit graphics card drivers"
date: 2008-08-16
forum: x86 64-bit Users
---

### Post by crhis on 2008-08-16
Hi, I just built my first computer ( evga 780i motherboard, q6600, and a bfg grx 260 graphics card.

I am wondering where I can download the drivers for the video card. When I try and select it from NVidia's page, it says that the page is not found. 

I am running the 64 bit of Hardy Heron, xp, and vista tri-booted.

I downloaded envy, but I do not think that it is supported. I have read online that it is supported. If anyone can please tell me if it is possible to install the drivers and how it would be greatly appreciated.

---

### Post by tamoneya on 2008-08-16
have you looked in system-> administration -> hardware drivers?

---

### Post by crhis on 2008-08-16
yes i have, it does not show up and i have enabled them in the rep

---

### Post by IanW on 2008-08-17
Try this:-

In Synaptic, select envyng-gtk (which will select envyng-core as a dependancy).
This will install EnvyNG into the System Tools section of your menu.

In EnvyNG, select Nvidia and click "Apply".
This will then download and install the latest graphics drivers from Nvidia (which is what you'll need for a GTX260).
Once finished it will ask you to reboot your PC.
That's it - you're done.

---

### Post by crhis on 2008-08-17
It said that it has not found any driver compatible with my graphics card. I am wondering if my graphics card is even supported. I thought that I read in multiple different places that it was. Can someone please tell me if drivers have been written, or if there is another way of having the full 1680 * 1050 resolution of my monitor.

---

### Post by IanW on 2008-08-18
It looks like the current 177.14.12 driver does not support your card.
The earlier 177.13 beta driver does, however EnvyNG won't use beta drivers. You'll have to compile & install it yourself

[Get it here.]("http://www.nvidia.com/object/linux_display_amd64_177.13.html")

---

### Post by crhis on 2008-08-18
Thank you soooo much. It worked. I have been trying to do this for a while.

---

### Post by cocokiwi on 2008-08-19
> **crhis said:**
> Hi, I just built my first computer ( evga 780i motherboard, q6600, and a bfg grx 260 graphics card.

I am wondering where I can download the drivers for the video card. When I try and select it from NVidia's page, it says that the page is not found. 

I am running the 64 bit of Hardy Heron, xp, and vista tri-booted.

I downloaded envy, but I do not think that it is supported. I have read online that it is supported. If anyone can please tell me if it is possible to install the drivers and how it would be greatly appreciated.

Hmmm! I,ve just downloaded it,no problem!(grin)  I just got a EVGA GTX 280

That was fun! first! I called EVGA and asked if my NEW 700w power supply will work! OH yes they said..you have 56 amps! BEEEP.BIP.BIP BIP goes my MB
Error,error! green LED then RED! POWER SUPPLY >Argggg! oh well I trott down to FRY,s give puppy face and plead to exchange supply(week over mth)
OK! sayith Fry,s..Found a Antec 850 watt for the SAME price(open box)
Installed same and it worked! well! I,m getting ahead of myself here!
So I,ve got the power supply in and plugged as far as the internals go! and I go to put the VIDEO LCD displays back in and notice sparks coming off the plug as I plugged it in! well I turned on the computer and turned around and noticed the LED on the display was not on!well! it had died!
plugged in my other one Thank god I had it,SAME display 19" 1440 x 900
older model,one that died was 2 years newer.anyway! here I is,trying to get a newer DRIVER for the new card! my problem right now is HOW one turns off the X server (grin) and to THINK you have problems(GRIN):lolflag:

Ok ! since you have a new setup! should work..get the 64bit Hardy DVD version ISO..google Ubuntu 64bit DVD iso should get you the file!
I have the AMD version,,just get the one your MB will handle! dual core is fine! I running mine as I type on it! I aso have VISTA 64bit and XP 64bit on the same computer..works fine!
load the DVD and let it boot..it will! then you can install via the desktop!once up you can goto Ubuntu.com and find the Nvidia update link and it will take you to the Nvidia site where it will allow you to download it! download dumps it to Desktop,so if you can find it,change it so it goes somewhere else.kill x server then open terminal cd /media/linuxfiles
that where I opened new file linuxfiles and put the file in there!
ok! asuming you got x shut down before..type sh filename with run on end
hit enter! AT this point you are on your own as this is where I am(grin):confused: one thing! GRUB,the boot file has a thing where it croaks and displays error 17 after you run ubuntu for a while and you cannot get into it,the problem is the partition location the file sits in, it seems that it skips between two locations, newer drives in auto mode set it at 38309 Cyls in Large mode it,s 2553 on a 80 gig drive, the darn thing looses track of where the file is and displays the error 17,switching from one mode to the other usualy fixes the problem,why! I have no idea!

Hope this helps Dennis):P

---

### Post by soxs on 2008-08-19
Get the latest driver: NVIDIA 177.67 Display Driver (binary one)
Read the readme and install the required tools with ```
sudo apt-get install <tool-name>
```
Any older binary bet driver won't have support for the GTX260/GTX280 (or only waky beta support)

Get it from the nvidie download page: [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

---

