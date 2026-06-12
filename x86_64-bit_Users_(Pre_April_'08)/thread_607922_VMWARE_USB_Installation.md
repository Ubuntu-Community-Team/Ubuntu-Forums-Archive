---
title: "VMWARE USB Installation"
date: 2007-11-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by iamcowdrunk on 2007-11-09
I have extracted the ISO for vista and a few other OS's onto a USB drive because i have no cd drive on my computer. But VMWare will not boot from USB. I have enabled 'USB controller' for the Virtual Machine but there are no usb drives listen under VM > Removable Devices. Please help. Thank you.

---

### Post by iamcowdrunk on 2007-11-09
bump

---

### Post by fjgaude on 2007-11-10
Okay, I think your issue is that some lines need to be uncommented:

```
gksudo gedit /etc/init.d/mountdevsubfs.sh
```

Go down to line 42 through 45 and uncomment them. Save file.

Then

```
sudo /etc/init.d/mountdevsubfs.sh restart
```

That should permit the USB devices to show in VMware.

Let us know how things go.

---

### Post by warp99 on 2007-11-11
Unrelated to your answer about booting from the USB,  but you know that you can boot from an ISO file direct in VMware by assigning  the ISO as a physical CD Drive. 

So you could mount the USB like you would normally, then boot from an ISO image on the USB. This would save you a step since you wouldn't need to extract the ISO image in the first place. :)

Edit: Or just boot from the ISO on your hard drive and skip the USB all together.

---

### Post by dustooff on 2007-11-11
I had a similar prob caused when upgrading from Fiesty to Gutsy, nothing under /proc/bus/usb therefore vmware could not find any usb devices.

figaude's edit fixed it.
thanks

---

### Post by iamcowdrunk on 2007-11-12
I followed figaude's post but got an error after sending the second line..

'Error: argument 'restart' not supported'

So i restarted the computer normally. USB doesnt mount automatically now, but still nothing in VMWare even after a virtual machine is installed and running.

warp99: I did see the ISO feature in vmware but i don't have an ISO for any of my flash drives.. I did create an ISO from one of the drives and it installed fine that way but i dont want to have to do it for the other 5..

---

### Post by sporto on 2007-11-13
> **iamcowdrunk said:**
> I followed figaude's post but got an error after sending the second line..

'Error: argument 'restart' not supported'

So i restarted the computer normally. USB doesnt mount automatically now, but still nothing in VMWare even after a virtual machine is installed and running.

warp99: I did see the ISO feature in vmware but i don't have an ISO for any of my flash drives.. I did create an ISO from one of the drives and it installed fine that way but i dont want to have to do it for the other 5..

valid switches to mountdevsubfs.sh are start and stop, so just send a stop and a start instead.

go to the VM menu, removable devices, usb devices. Are the devices listed there? If so, just click their entry in this list to pass control of them from Linux to Windows.

If there is nothing in the list do 'ls /proc/bus/usb' , anything there?

---

### Post by chauster on 2007-11-13
I also had this problem.  Uncommenting those lines fixed the issue of finding the USB drive.  But now after it went thru the whole detect new hardware process, it says my USB is not a USB 2.0 device and then it says it is malfunctioning and is not working properly.

The USB drive doesn't mount properly in the VM.  Anyone know how to fix this?  I've tried 3 different brands and sizes (from 128MB -> 2GB) and they've all seem to fail.

---

### Post by fjgaude on 2007-11-13
Well, I'm the "restart" guy, coming from Red Hat for too long. <smile>

I see that I can't mount a USB drive in my VMware Server either... printers, scanner, UPS, other USB devices attach correctly, but not a drive. I wonder...

Naybody try yet the new version 2.0 of VMware Server Beta just released today?

---

### Post by iamcowdrunk on 2007-11-14
It is half working now...

USB is listed now in VMware menu and i can select it, but it does not come up anywhere in the virtual machine.

I started converting my USB's to ISO for the time being but i would still like to figure it out.

Another question i just got now.... i would like to try to install a VM to its own hard drive but it gives me the error 'Unable to complete wizard: Insufficient permission to access file.'

---

