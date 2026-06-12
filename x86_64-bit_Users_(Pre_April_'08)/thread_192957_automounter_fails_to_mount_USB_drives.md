---
title: "automounter fails to mount USB drives"
date: 2006-06-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by jdh on 2006-06-09
I am running Dapper Drake live CD  to test out 64 bit on my new :
Athlon64 3500+
MSI K8N
4Gig DDR333
nvidia 7600GS

When plugging in a USB mass storage device, HDD or flash, it will not automount. Other USB devices work, scanner, printer, and RS232 adapters.
I need a solution prior to taking the plunge and installing Dapper on my system or will installing it fix the problem.? Do I need to switch to 32 bit Dapper/other distro?
Although not 64 bit Knoppix 4 DVD works using same ports and devices, so I think it is not a hardware problem. 

dmesg reports:
> 
[ 1578.017727] usb 1-5: new high speed USB device using ehci_hcd and address 3
[ 1583.130129] usb 1-5: unable to read config index 0 descriptor/start
[ 1583.130135] usb 1-5: can't read configurations, error -110
[ 1583.232013] usb 1-5: new high speed USB device using ehci_hcd and address 4
[ 1588.345425] usb 1-5: unable to read config index 0 descriptor/start
[ 1588.345431] usb 1-5: can't read configurations, error -110
[ 1588.449299] usb 1-5: new high speed USB device using ehci_hcd and address 5
[ 1593.461737] usb 1-5: unable to read config index 0 descriptor/start
[ 1593.461743] usb 1-5: can't read configurations, error -110
[ 1593.563604] usb 1-5: new high speed USB device using ehci_hcd and address 6
[ 1598.575050] usb 1-5: unable to read config index 0 descriptor/start
[ 1598.575056] usb 1-5: can't read configurations, error -110


---

### Post by Apostata on 2006-08-15
I'm having a similar problem here. 

Dapper-64 recognized my USB keychain, but it could only mount as root. Even when I got it to mount in fstab it still doesn't allow me (as user) to copy to the drive (although i can copy files *from* it). 

In short, it's never been this hard compared to previous versions of Ubuntu. If I can find an FAQ somewhere, I'll post it.

---

### Post by Apostata on 2006-08-15
I did some research and found this solution ([HOWTO Fix Mounting USB Flash Drive Problem in KDE 3]("http://doc.gwos.org/index.php/USB_Flash_Drive_KDE_3.5")), but it didn't work for me. Still can't write to the drive.

---

### Post by jdh on 2006-08-17
Yes it sounds like yours is working the same as mine. I got tired of playing around with it so I fixed it by sending the 64 bit version to the bit bucket and loading the 32 bit version. I did not notice any speed difference between the versions. It works as expected, automounts all my usb media with and icon on the desktop and open file browser window, it even mounts 2 identical USB sticks at the same time, XP locks when you try it. It is read/write by the user. Something must be broken in the 64 bit version.

---

### Post by Apostata on 2006-08-17
You must be right, as I've spent two days trying to sort it out (on my vacation no less :mad:). Someone tried working it out with me [[COLOR="Orange"]here[/COLOR]]("http://www.justlinux.com/forum/showthread.php?p=853100#post853100"), but still no luck.

It's either something in the general config, or perhaps the kernel (?)

Sad if true. I noticed a slight speed increase when I upgraded to 64-bit, but it's crucial that I be able to write to USB drives. We'll see.

---

### Post by sweettea on 2006-08-30
I'm experiencing a similiar problem, and wonder if anyone has a solution?

After upgrading to Dapper I plug my USB datastick into the machine, and a little icon pops up on the desktop "RAmosTek RunDisk".

I click to mount the USB, and get this message:

Unable to mount the selected volume.

error: This program needs to be installed suid root.
error: Could not execute pmount.


So...I'm stuck, need to get a file off the machine? Suggestions?

---

### Post by teepark on 2006-08-30
I am having the same problem. Here's my relevant dmesg output:
```
[  294.908854] usb 2-6: new high speed USB device using ehci_hcd and address 10
[  301.034224] usb 2-6: device descriptor read/all, error -110
[  301.146076] usb 2-6: new high speed USB device using ehci_hcd and address 11
[  308.270408] usb 2-6: device descriptor read/all, error -110
[  308.382204] usb 2-6: new high speed USB device using ehci_hcd and address 12
[  313.396783] usb 2-6: device descriptor read/8, error -110
[  318.511296] usb 2-6: device descriptor read/8, error -110
[  318.726955] usb 2-6: new high speed USB device using ehci_hcd and address 13
[  323.741554] usb 2-6: device descriptor read/8, error -110
[  328.856069] usb 2-6: device descriptor read/8, error -110

```
I've been on 64bit dapper for a few months now, and the USB plug and play never worked, but then one time last week when I rebooted it did work. When I unplugged the USB stick and plugged it in again, it worked again. When I rebooted, it stopped working. I saw in an old ubuntu forum (Hoary) that when similar problems were encountered in the past, some people could get it to work by plugging in their USB stick while the machine was booting up. 

I probably did that without realizing it, and since I read that thread I've been trying to replicate it to get my data back! I'm beginning to feel a little ridiculous now, and would really appreciate it if somebody could figure what's up with dapper64.

---

### Post by Apostata on 2006-09-04
I've filed this as a [bug report]("https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/56769"). It's already been upgraded to 'Medium' by bug-staff, but it waits for confirmation.

I must say, I have no reason to suggest to anyone that they use the AMD-64 version if issues like this can't be resolved.

---

