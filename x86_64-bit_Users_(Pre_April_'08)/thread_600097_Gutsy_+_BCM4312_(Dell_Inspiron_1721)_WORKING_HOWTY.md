---
title: "Gutsy + BCM4312 (Dell Inspiron 1721) WORKING: HOWTY"
date: 2007-11-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by lacanadio on 2007-11-01
From [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

To get the firmware, wget [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)
Stick it in a new directory and connect to that directory.

sudo apt-get install bcm43xx-fwcutter

bcm43xx-fwcutter wl_apsta-3.130.20.0.o

sudo cp *.fw /lib/firmware

sudo modprobe -r bcm43xx; sudo modprobe bcm43xx

dmesg

At end, you should see something like:
[ 3141.022996] bcm43xx driver
[ 3141.023117] ACPI: PCI Interrupt 0000:0b:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[ 3141.023128] PCI: Setting latency timer of device 0000:0b:00.0 to 64
[ 3141.153023] ADDRCONF(NETDEV_UP): eth1: link is not ready

I have this running WPA-PSK and am typing over the link.

Have fun...

---

### Post by lacanadio on 2007-11-01
So I can't type...sue me...:)

---

### Post by Cybermax on 2007-11-03
Well.. This does not work for me tho.. I still get the 

bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR in my syslog

I have also tested different kernel options like noirqpoll and noapic .. and so forth without result.

Could you verify what you get when you do a  lspci ?

I get :

Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 02)

Do you have the same? Especially if you have (rev 02), cos i suspect this may be different..

C

---

### Post by lacanadio on 2007-11-04
0b:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)


I think you're probably right about the revisions being different. Sorry...that's a drag.

Bob

---

### Post by Cybermax on 2007-11-05
Yeah.. ive currently given up on it altogether.. Kind of a shame.. But i suppose it may be supported under the 2.6.24 kernel and the "b43" kernel module..

Havent found much info on this b43 module, but it is supposed to support "v4 firmware" wich is the one i can find in the ndiswrapper driver that actually works (using ndiswrapper ofc).

Unless anyone know of a b43 source that can be downloaded? :)

C

---

### Post by drs305 on 2007-11-05
Cybermax,

I have a 4311 rev 2 and got it to work following the solution at:
[http://ubuntuforums.org/showthread.php?t=475963](http://ubuntuforums.org/showthread.php?t=475963)
From that link (which has a poll) click on the link for "BCM43xx HowTo"  and go back to take the poll when you are done. The actions will download and extract the drivers you need.

True to it's subject line, it did take me less than 5 minutes to get it working. It will probably work for the 4312 as well.

Good luck.

---

### Post by Cybermax on 2007-11-13
Well.. ive posted in a different thread i think, that ive already gotten the ndiswrapper to work, so its not a problem getting wireless to work with ubuntu.. the problem is that i want to use the native linux kernel module, and not a windows driver..

Why you say? Well.. i want to do some testing on my wireless network at home, then using kismet and the aircrack-ng package.. And none of theese support ndiswrapper, cos you cannot get that to inject packages sadly.

So.. my problem still stands.. I cant get the native BCM43xx module to work.

I have however seen certain indications that kernel 2.6.24 have some support for newer broadcom chipsets via the B43 module.. This module is not included in the 2.6.22 or 2.6.23 kernelsource, so i either have to compile a vanilla kernelsource on ubuntu and try.. and i havent gotten that far yet.. I also tried some gentoo stuff, where you actually can get some modified 2.6.24 kernelsources, but i ended up stranding on a problem with the livecd kernel not supporting the nVidia lan wired card either.. hehe..

C

---

