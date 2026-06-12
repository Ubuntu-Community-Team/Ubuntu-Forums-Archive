---
title: "Network Booting on an iMac through Firmware..."
date: 2006-03-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by SectionThree on 2006-03-16
I just inherited a 400 MHz iMac (slot-loading, 1999-2000) with 256 MB RAM, but the DVD-ROM drive is shot and the hard drive (which was running OS 9) won't boot. I hooked it up to my LAN and tried to boot it up from my working 266 MHz iMac (the one I'm using now) to no avail. I think this is possible, and I acknowledge my lack of experience with Open Firmware. Does anyone have any idea how to do this, or will I have to spring for a new drive? Also, if I have my Breezy install CD in my working iMac, can I boot up the "nonworking" one over the network from the CD (I don't care a lick about the data on the 10GB hard drive on the "new" machine, it can be wiped for all I care)...

I want to use this for an "anything goes" ppc Linux machine where I'm free to do anything I want without fear of serious crashes because I can wipe it and start anew... that kind of thing...

---

### Post by spangemonkee on 2006-03-18
you could try plugging your (A)working mac into the (B)non-working mac via firewire.

Start the A mac (OSX) and let it load all the way. Then start the B mac while holding down the T key. This will put a firewire icon on the B mac screen. The drive will popup on the desktop of OSX. This may not help. Don't know. But it is a cool feature of macs.

T key allows you to boot the mac from firewire mode.

You also just might want to troubleshoot the OS9 problem.

I by no means a mac expert but I know enough to get in trouble. :)

[Mac Boot Key Combos]("http://davespicks.com/writing/programming/mackeys.html")

---

### Post by jdp on 2006-03-18
I thought that when I first read the OP, but the good Mac is a 266, ie trayloader, and doesn't have FireWire.  Could try putting a FW or USB CD-ROM on the DV 400 to boot from.  It'd have to be a supported CD drive to boot, IIRC.  It might be best to either transplant the HDD to another machine, or replace the DVD-ROM if you don;t have any externals to try.

---

### Post by AlexMorin on 2006-03-20
Booting from an external Firewire drive might help troubleshooting the non-working, firewire-enabled Mac. Or formating and resinstalling. Is the hard drive shot?

To boot it from network (Netbooting in Apple parlance), you need Mac OS X server (which could be installed on the working Mac). Then, all you would have to do is start with the option/alt key pressed, or set it to netboot all the time through system preferences, which would give you a foolproof thin client. But it means you know a bit about Mac servers.

It could also be possible to boot using PXE/Etherboot from a Linux server, but I'm stretching here. The same technologies seem to be used in both cases (Apple and Linux), but I have no real clue how to go about it.

---

### Post by bodyguard on 2006-03-24
this might help
[http://ubuntuforums.org/showpost.php?p=859109&postcount=5](http://ubuntuforums.org/showpost.php?p=859109&postcount=5)

---

### Post by AlexMorin on 2006-03-27
Wow, so I was right in assuming Macs can Netboot *NIX style! Sweet!

---

### Post by SectionThree on 2006-03-31
Thanks everyone. I'll try all these suggestions (sans the firewire ones, I've no firewire devices, alas) and learn much. But in the end, I'll probably spring for the new drive and then it's down to the garage with me, the computer, and a few screwdrivers 8)

---

