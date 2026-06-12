---
title: "making usb active in vmware"
date: 2007-05-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by rustybutt on 2007-05-28
I'm running 64 bit Feisty on an AMD 64 machine w/2 gig of RAM.  I partitioned the hard disk with some extra partitions for use with vmware server.  I've installed Windows XP Pro in a VM using one of these partitions.  It fires up and seems to work.

What I can't seem to get it to do is to recognize any usb device.  In particular, I want it to recognize a couple of usb printers I have, and to provide print spooling services for them.   The .vmx file for this VM is set with the following:

usb.present = "TRUE"
usb.generic.autoconnect = "FALSE"

When I go to the VM server pull down menu to:  VM -> Removable Devices -> USB Devices, it shows it as being empty.

I have two USB printers and my Palm Treo 680 plugged into the USB bus, so I'd expect *something* to show up, but there's nothing there.

One of the printers is an EPSON ink jet, and /var/log/messages shows that the system sees it when it gets plugged in:

May 27 08:51:51 localhost kernel: [2993683.214207] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 6 if 0 alt 0 proto 2 vid 0x04B8 pid 0x0005

I've been reading through the man page for udev and figure I could put in a custom rule for the printer, but I have no clue as to what it should be to accomdate the VM.

At this point I'm stumped.  Suggestions?

rustybutt

---

### Post by factor on 2007-05-28
i'm very interested on that too, same thing happens to me.

---

### Post by factor on 2007-05-28
look here: [http://www.crn.com/white-box/197004927?pgno=3](http://www.crn.com/white-box/197004927?pgno=3)

---

### Post by rustybutt on 2007-05-28
I took a look at the article.  I've already done the "add usb device" bit, but Windows doesn't see any of the USB devices.  That's the problem.  It's as if the host OS is either conflicting with the VM, or is not passing the devices on to the VM.

I'm thinking that there might be something I could do in udev, but I can't find any documentation on vmware that would tell me what to do.  udev manages devices and gives them whatever device name you want, as well as setting ownership and permissions.  But seeing as how vmware server insists on running as root anyway, that shouldn't be an issue.

I suspect that either Ubuntu is claiming ownership of the devices and not passing it on to the VM, or that this being the 64 bit version of Feisty, that there's something missing.  I may have to roll back to the 32 bit version of Feisty.

rustybutt

---

### Post by mateusz.dobrowolny on 2007-06-06
Hi,

I found the following solution, it works on my Kubuntu 7.04 32-bit version with pendrive.
The solution was presented on Polish language forum:
[http://www.linux.com.pl/forum/index.php?t=msg&goto=296720&rid=0&S=652e725345fffe59edf9295c16a9abba](http://www.linux.com.pl/forum/index.php?t=msg&goto=296720&rid=0&S=652e725345fffe59edf9295c16a9abba)

Steps to mount pendrive in VMWare:
1. insert pendrive - it should be mounted automatically.
2, unmount it (I click on it with right mouse button and choose 'Safely Remove')
3. Launch VMWare
4. Turn on your virtual machine (Windows 2000 in my case)
5. From the menu VM --> Removable Devices --> USB Devices --> choose your USB pendrive.

Hope this helps.

---

### Post by dcstar on 2007-12-27
[http://ubuntuforums.org/showthread.php?t=642107](http://ubuntuforums.org/showthread.php?t=642107)

---

