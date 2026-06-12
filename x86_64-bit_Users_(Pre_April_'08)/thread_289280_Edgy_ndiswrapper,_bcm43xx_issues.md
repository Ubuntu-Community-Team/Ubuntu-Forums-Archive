---
title: "Edgy ndiswrapper, bcm43xx issues"
date: 2006-10-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by mickeysden on 2006-10-30
Hi Guys
I know this has been asked before, but I didnt get a really solid answer. Ndiswrapper and broadcom 43xx was working great with Dapper, but as soon as I installed Edgy, it stopped. I checked Synaptic and installed ndiswrapper-utils 1.18 
configuring doesnt give me any errors, but nothing happens, and wireless doesnt work?
anyone got it running?

---

### Post by darkshadow on 2006-10-31
I got them working finally
first boot with these boot paramaters added (both modules require this)

pci=assign-busses pci=routeirq irqpoll

then for bcm43xx which I got working stable but slow (11M) use bcm43xx-fwcutter of wl_apsta.o which you can find links for on these forums. I forget one that is for 64bit but make sure you get a 64bit version. after those the module worked awesome except for the slow speed

then for ndiswrapper purge all things related to it from your computer including deleting /lib/module/`uname -r`/kernel/drivers/net/ndiswrapper/ndiswrapper.ko
then install build-essential and get the newest version 1.28 as of this writing and "make && make install" it. install your windows firmware and use it like normal

---

### Post by kcallis on 2006-12-07
> **darkshadow said:**
> I got them working finally
first boot with these boot paramaters added (both modules require this)

pci=assign-busses pci=routeirq irqpoll

then for bcm43xx which I got working stable but slow (11M) use bcm43xx-fwcutter of wl_apsta.o which you can find links for on these forums. I forget one that is for 64bit but make sure you get a 64bit version. after those the module worked awesome except for the slow speed

then for ndiswrapper purge all things related to it from your computer including deleting /lib/module/`uname -r`/kernel/drivers/net/ndiswrapper/ndiswrapper.ko
then install build-essential and get the newest version 1.28 as of this writing and "make && make install" it. install your windows firmware and use it like normal
Well, I finally bumped my Ubuntu kicking and screaming up to Edgy, and then for grins and giggle, I rebuild the kernel to 2.6.19. The good news is that it is still booting... But I am having issues with getting my BCM4318 working. The noticed in the rebuilt kernel that there was a driver for the BCM43xx, so I removed that out of the kernel.

Does any one have some other pointer on getting ndiswrapper working correctly under Edgy?

---

### Post by tetralis on 2007-01-24
Hi,
I was tired of the native driver getting the keyboard freezing and the connection at 11 Mbps.

I switched to ndiswrapper and so far so good, just  got it running. At least the connection is at 54 Mbps! I am using 64 bit ubuntu 6.10.

Follow this link: 
[http://www.ubuntuforums.org/showthread.php?t=31859](http://www.ubuntuforums.org/showthread.php?t=31859)
More exact [http://www.ubuntuforums.org/showpost.php?p=159310&postcount=3](http://www.ubuntuforums.org/showpost.php?p=159310&postcount=3)

I didn't issue the "sudo ndiswrapper -m" and be aware if you have eth*or wlan0. I have eth1 with the native driver and after reboot it became wlan0 with ndiswrapper.

Don't forget to add ndiswrapper to your /etc/modules file and comment any presence of bcm43xx
You may also want to add bcm43xx to /etc/modprobe.d/blacklist if you have already removed it.

---

