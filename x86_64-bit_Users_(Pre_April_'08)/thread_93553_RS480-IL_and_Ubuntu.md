---
title: "RS480-IL and Ubuntu"
date: 2005-11-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by yelloguy on 2005-11-22
Posted this on the Kubuntu forums but they get less traffic so I am trying it here.  For those of you who have seen it there, sorry for the double post.

I built this computer back in March 2005 with an MSI RS480-IL mATX mother board. I am using the on board ATI X200 video chip and the on board sound (RealTek) for now. I have the Logitech MX500 duo USB wireless keyboard and mouse combo and a D-Link (DWL 610?) PCI wireless card. I have an old Hauppauge tuner card (WinTV Go) in another PCI slot. Finally, I have 512 MB memory (I forget which brand) which is shared (32 MB) with the integrated video.

The problem is, I have NEVER been able to install Linux on this rig. I used to have Mandrake 10.1 and Suse 9.2 (both 32 bit) on my previous computer but for this one, I downloaded the 64 bit versions of these distros but neither of them would install. The installation hangs while detecting hardware. I have tried the various switches that Mandrake installation offers (-noacpi, etc etc). I also tried the old 32-bit editions for Mandrake and Suse but had the same problems. I gave up and forgot all about it all until someone suggested Ubuntu recently. So I downloaded the 64-bit version of Kubuntu (since I prefer KDE) and gave it a spin. But I am having similar problems again. The installation proceeds to a point and then hangs. It shows me a message saying it is starting system log daemon and hangs there for 6-7 minutes.

> Starting system log daemon: syslogd, klogd

Then I rebooted and tried pci=noacpi option and it hanged at exactly the same place.

Next, I tried the debian-installer/probe/usb=false option and this time it went further.  It made me choose my location and language and then showed a blue screen with grey bar at the bottom but it hanged there.

BTW, I also get these weird messages which may have some bearing on what is going on:

> Unlink after no-IRQ? Controller is probably using wrong IRQ

and before that, I get a bunch of 

> new high speed USB device using ehci_hcd and address 4
[it fails then tries the next number]
> new high speed USB device using ehci_hcd and address 5
> new high speed USB device using ehci_hcd and address 6
> new high speed USB device using ehci_hcd and address 7
> new low speed USB device using ohci_hcd and address 2
[this one, I guess succeeds]


Any pointers on what is going on?

---

### Post by victor_c26 on 2005-11-23
I'm also having trouble running the 64-bit live cd on my RS480M2-IL Motherboard. Are the ATi linux drivers really *that bad*?

I still can't manage to run Ubuntu at all yet. It always gives me an error saying it's the graphics chip that "Wasn't set correctly".

---

### Post by aschlapsi on 2005-11-23
Have you tried to change some BIOS settings? E.g. with "Advanced->Plug and Play OS" and "Advanced->USB Legacy Mode Support" I had different results booting Linux. Note that when disabling "USB Legacy Mode Support" you won't be able to use a USB keyboard.

---

### Post by eph on 2005-11-23
what version of ubuntu did you use?

i used 5.10 and it installed smoothly

---

### Post by gmz on 2005-11-23
I had to disable Legacy USB Support on my HP a1130n which uses the same mobo. I was not aware of the keyboard issue mentioned by aschlapsi but other USB devices work fine (trackball, digital camera, iPod, etc.)

Greg Zenitsky
Lee's Summit, MO

---

### Post by yelloguy on 2005-11-23
I have not made any changes to the BIOS but will try disabling the USB legacy support first.  If that does not help, I will try changing the PNP OS setting in the BIOS.  Re: the version, I have downloaded the latest this weekend which I believe is 5.10.

Victor, I think I read somewhere that you are supposed to use generic Vesa driver and not ATI ones, but that is not what this thread is about. I am having trouble installing Ubuntu.

---

### Post by korakde on 2005-11-26
Hi all. I also am having the same problem on my computer.\
My config
AMD 64 939pin 3000+
MSI RS482 IL with ATI Xpress 200 integfrated graphics.
Whenever I try to load the Live CD everything seems to go OK till a stage where I get a fatal error XServer could not load.
I get a similar messasge to that of Nella89 on [http://ubuntuforums.org/showthread.php?t=85295](http://ubuntuforums.org/showthread.php?t=85295)
I am an absolute newbie to Linux and would do with some help.
Can I write these messages on the prompt that I get while spinning the Live CD:
sudo apt-get reinstall xserver-xorg

sudp dpkg-reconfigure xserver-xorg

Regards

---

