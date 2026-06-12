---
title: "Another hardware Question."
date: 2005-08-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by carpinus on 2005-08-13
I am looking at MSI K8N Neo Platinum mobo, or the Neo4, also the ATI Radeon X300SE 128mb DDR card, also  living where I do I still need a USR PCI Modem, will all these work.?
Or should I use that which I am reading about on the forum ie. Asus  A8V Deluxe with a 64 bit chip. a Nividia video card.?

---

### Post by Jet2k5 on 2005-08-13
[QUOTE=carpinus]I am looking at MSI K8N Neo Platinum mobo, or the Neo4, also the ATI Radeon X300SE 128mb DDR card, also  living where I do I still need a USR PCI Modem, will all these work.?
Or should I use that which I am reading about on the forum ie. Asus  A8V Deluxe with a 64 bit chip. a Nividia video card.?[/QUOTE]

From what I hear MSI K8N Neo Platinum boards don't seem to work on Linux too well.  I don't know what the reason might be but I just know that they have some issues.  I would go with something else if you can , maybe an ASUS or DFI ( which I'm getting a few days ).  Also I would try to get an nVIDIA based card.  I know that ATIs support for Linux has increased, it still isn't as good as nVIDIAs.

As for your modem I don't know, some google might help.  I don't use dial-up so I don't know the first thing about dial-up access and Linux.  Hope this helps.

---

### Post by Corbelius on 2005-08-14
[QUOTE=Jet2k5]From what I hear MSI K8N Neo Platinum boards don't seem to work on Linux too well.  I don't know what the reason might be but I just know that they have some issues.  I would go with something else if you can , maybe an ASUS or DFI ( which I'm getting a few days ).  Also I would try to get an nVIDIA based card.  I know that ATIs support for Linux has increased, it still isn't as good as nVIDIAs.

As for your modem I don't know, some google might help.  I don't use dial-up so I don't know the first thing about dial-up access and Linux.  Hope this helps.[/QUOTE]

I have a MSI K8N Neo4 Platinum and work perfectly -_-, but i have a modem ethernet (controlled by ehernet card on motherboard, Marvell Yukon Gigabit) and an Nvidia GeForce 6600GT PCI-E, a Western Digital HD SATA controlled by nForce 4 Ultra on MoBo (Silicon Image chip SATA disabled in bios), and i use sound card nforce ck804 on motherboard, all it works without no problem.

---

### Post by Jet2k5 on 2005-08-14
[QUOTE=Corbelius]I have a MSI K8N Neo4 Platinum and work perfectly -_-, but i have a modem ethernet (controlled by ehernet card on motherboard, Marvell Yukon Gigabit) and an Nvidia GeForce 6600GT PCI-E, a Western Digital HD SATA controlled by nForce 4 Ultra on MoBo (Silicon Image chip SATA disabled in bios), and i use sound card nforce ck804 on motherboard, all it works without no problem.[/QUOTE]

I have a couple of friends that have an MSI K8N Neo4 and they can't install Linux on it.  One of the major reasons was sound ( for the one that got past the Hoary install ).  Another couldn't get his hdd detected ( SATA II I believe ).  And the other friend just nothing would happen.  It would just sit there.

But if you pick a  mobo that just has a standard set up, I don't see any sort of problem.

---

### Post by Steve1961 on 2005-08-15
I installed the 32 bit version of hoary on an MSI Neo4 Platinum and I've just upgraded to the 64 bit version. No problems with either, although the install didn't recognise the Marvell LAN port or the SIL Raid card.  I disabled both of these in the bios as I don't use Raid and I'm using the onboard Nforce4 Lan.  A few problems getting sound working to start off with, but now working fine.

---

### Post by Corbelius on 2005-08-15
[QUOTE=Steve1961]I installed the 32 bit version of hoary on an MSI Neo4 Platinum and I've just upgraded to the 64 bit version. No problems with either, although the install didn't recognise the Marvell LAN port or the SIL Raid card.  I disabled both of these in the bios as I don't use Raid and I'm using the onboard Nforce4 Lan.  A few problems getting sound working to start off with, but now working fine.[/QUOTE]

[http://www.syskonnect.com/syskonnect/support/driver/htm/sk9elin.htm](http://www.syskonnect.com/syskonnect/support/driver/htm/sk9elin.htm)

Install these driver on your motherboard ethernet card and work :D

---

### Post by DancingSun on 2005-08-15
Stay away from ATI, until they can provide more stable Linux drivers.

---

