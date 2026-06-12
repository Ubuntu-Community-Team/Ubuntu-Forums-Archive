---
title: "Live CD, NForce4 ATI PCIe =&gt; PC freezes at X"
date: 2005-07-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by Beto on 2005-07-07
Hi all,

I read some other peple had this problem, but all of them seem to be in the install version. I have the Live CD version and I don't know how to workaround this problem. Here are the facts:

PC:
- Processor: AMD64 3000+ Core Venice
- Main Board: Chaintech Nvidia chipset NFORCE4, w/Realtek Sound, Network, PCIe capabilities.
- Video: ATI PCIe X600Pro
- Memory: 512Mb RAM, Dual channel.
- NEC DVD Burner.
- HD: Hitachi SATA2 82.3Gb. (Only 1 partition of 20Gb in use up to date with Windows XP Pro working flawlessly. I plan to create another 20Gb partition to install Linux and leave 40 Gb as a data partition. Please note I'm a total newbie with Linux!)

I  think that is all that matters from the HW point of view.

The booting starts fine, but when Xwindows starts, the PC freezes. I saw another posts with similar behaviour which were solved by switching to console once X starts (Ctrl+Alt+F1), changing the driver from "ati" to "vesa" in xconf.org, going back to Xwindows and restart it with Ctrl+Alt+Backspace.
I tried this, but once I come back to Xwindows to restart it, I can't because the PC freezes inmediatly.

Is there any workaround for my case?

Regards,
-- 
Beto

---

### Post by FluffyElmo on 2005-07-07
I'm not sure if you can change xorg.conf on the fly from a LiveCD. People have been having X issues with the latest Breezy CD and the only solution has been to burn an updated copy.  

For what it's worth, you should have no (or few;)) problem getting a Hoary install working with NForce4 and the VESA driver. Many people in the forums have this configuration. I'd just install Hoary to the 20Gb partition as planned and work from there, time spent getting the LiveCD working probably isn't worth it in the long term IMHO.

---

### Post by Jet2k5 on 2005-07-07
For a second this thread scared me very bad.  That is almost the same exact parts that I'm getting on my new system.  Good thing that it is with the video card, because I'm getting an Nvidia not an ATI :)

---

### Post by FluffyElmo on 2005-07-07
ATI Linux drivers have been developing a bit of a reputaion lately, but they're getting better. When in doubt, the VESA drivers will work with just about anything.

Either way, relax, have fun and welcome to Ubuntu! And If you have problems, we're here to help :)

---

### Post by Beto on 2005-07-08
[QUOTE=FluffyElmo]... I'd just install Hoary to the 20Gb partition as planned and work from there, time spent getting the LiveCD working probably isn't worth it in the long term IMHO.[/QUOTE]

Thanks for your insight. I plan to see which distro I will use by trying them out. I'm already downloading Fedora Core 4, but want to give a try to the latest Ubuntu. Is there any problem in installing and uninstalling each one of them? Can Both be installed in the same Hard Disk for testing puroposes? can they conflict between each other?

Regards,
--  
Beto

---

### Post by FluffyElmo on 2005-07-08
Generally they are both a quick install compared to windows you should be up and running with a functional system in ~30min or so. There also shouldn't be any problem having them both on the same disk in separate partitions.

One thing to watch for is the boot sector. If you install Ubuntu after Windows it will install grub to the boot sector in a dual-boot config. I'm not sure if it will pick up other copies of Linux though, so if you go that way you might want to know a bit about grub.

For testing you may actually want to leave the boot sector untouched and create boot floppies during the install instead. Boot from one floppy for Ubuntu and another for Fedora. Then when you make your choice you can install grub.

Also, note that for Linux you'll need an install partition and a swap partition (~1gb). You should be able to have both Linux OSs use the same swap partition. They won't be running at the same time so it shouldn't be an issue.

---

### Post by Beto on 2005-07-08
[QUOTE=FluffyElmo]
For testing you may actually want to leave the boot sector untouched and create boot floppies during the install instead. Boot from one floppy for Ubuntu and another for Fedora. Then when you make your choice you can install grub.
[/QUOTE]

Oops, not feasible because I didn't buy a Floppy Disk Reader for this PC. I think they are ancient history :)

I'll try to use grub, because I'm not dumb :) and I think I will be able to edit it to handle my configuration.

Thanks for your help!
--
Beto

---

### Post by rfreidel on 2005-09-28
I have a similar setup, the hardware is a little different though
Asus A8N-E, X2 3800+, 80g SATA, Asus X700, etc.
When I installed from the cd and rebooted X crashed right away, all I did was to edit /etc/apt/sources.list, removed the comments from universe, then updated then installed the ati driver. It works fairly good, I get really good performance with UT2004.

---

