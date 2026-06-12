---
title: "Ubuntu 9.10 - Failed to boot from IDE hdd if SATA hdd enabled."
date: 2009-11-15
forum: x86 64-bit Users
---

### Post by leoremons on 2009-11-15
Hi,

I am having [HP DX2255]("https://h10057.www1.hp.com/ecomcat/hpcatalog/specs/provisioner/05/RL028AV.htm") Business PC.

I am having Windows XP on a Western Digital SATA HDD.
I am having Ubuntu 64 9.10 on a Samsung PATA HDD.

When I started installation from ubuntu-9.10-desktop-amd64.iso (CD). The installation could only detect my SATA HDD.

So I disabled the SATA Controller, and started the installation again. Now my PATA HDD was detected. And installation completed successfully.

After installation I enabled the SATA controller once again in the BIOS. after that I tried to boot from my PATA HDD, it fails and I am dropped into initramfs shell. Saying it couldnot found a UUID-50XXXXXXXXXXXXXXXXX

In the initramfs shell I tried to list the HDD's that have been detected there was only the Western Digital SATA HDD. 

My Sansung PATA is not detected.

So I went back and disabled the SATA HDD in BIOS, and rebooted, now ubuntu is working properly.

What could be the problem? How can I fix this, I have backups of my old Ubuntu 8.04 on my Windows HDD (SATA). Please help me.

Thanks.

Leo

----------------------

[SOLVED] --- (21-nov-2009)

This was due to some bad settings in BIOS.

I am having Award Modular BIOS v6.00PG (what is this Bios V1.11, This is shown inside CMOS setup)

I changed the following:

SATA IDE mode select : Native Mode
PATA IDE mode select : Compatible Mode

Then saved the settings and gave a reboot.

Ubuntu worked like a magic! Also Windows is fine.
Earlier the bios setting were the opposite (sata was having compatible mode and pata with native mode).

This is not a UBUNTU bug, but was my bios setting!

Cheers!!

---


leoremons

---

### Post by pepilinux on 2009-11-15
Hi. I'm new here and i have the same problem: I think there's an option to pass to the kernel at boottime, but i don't remember wich (ide=nosata... nosataide..:()
Someone can help us?

---

### Post by drdos2006 on 2009-11-16
My suggestion is to leave the BIOS seetings as the defaults settings, but change the boot to the IDE HDD, open the computer and remove the SATA power supply, or Serial connection  and install. Once installed and running, reconnect supply and alter /etc/fstab to add the UUID.
regards

---

### Post by pietro_spina on 2009-11-16
> **leoremons said:**
> Hi,

I am having [HP DX2255]("https://h10057.www1.hp.com/ecomcat/hpcatalog/specs/provisioner/05/RL028AV.htm") Business PC.

I am having Windows XP on a Western Digital SATA HDD.
I am having Ubuntu 64 9.10 on a Samsung PATA HDD.


I have 2 PATA and 2 SATA drives in my computer and use an MSI 770-C45 Motherboard. 

The PATA drives have an old installation of Ubuntu and the SATA drives have 9.10. 

In order to boot from the PATA drives I have to change a couple of BIOS settings and then change them back to the SATA friendly ones when I am done with the PATA drives. 

This isn't a problem for me because I have saved the special settings in the BIOS 'user memory' slots... so I just use option one for PATA and number 4 for my SATA setup. Also I don't do this that much.

Maybe your BIOS has similar settings.
Good luck,
P

For what it's worth, When I boot to my SATA drives I can let the HW see the PATA drives but when I boot to the PATA drives the SATA drives have to be off or crash.

---

### Post by drdos2006 on 2009-11-17
leoremons
When you first installed Ubuntu, Ubuntu wrote information to your SATA drive, either as part of the Master Boot Record or elsewhere in the HDD memory.
You need to reinstall without the SATA drive connected, not disconnected in BIOS.
Remove the SATA power or data connection.
I also had this problem that you are having.
My problem is now resolved.
regards

---

