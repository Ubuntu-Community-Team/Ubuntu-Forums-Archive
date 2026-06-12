---
title: "Marvell 88SE6121"
date: 2009-01-22
forum: x86 64-bit Users
---

### Post by ZeeClone on 2009-01-22
Hi everyone.

So, one last barrier stands between me and a complete implementation of kubuntu and the problem lies with this controller.

I've googled and read, then googled and read some more but no one appears to have dealt with something truly akin to my set up. Or at least if they have, they've not talked about it enough for google to notice.

Here's the details:
Asus P5Q Deluxe motherboard
Intel P45 - Carrying 6 SATA HDDs of various sizes. System currently installed as a dual boot with XP on a 500gig WD

Marvell 88SE6121 carrying 2 SATA HDDs and an IDE DVD-RW

Here's the badger:
kubuntu only recognizes one of the two HDDs connected to the ports. Kadence (1 TB Samsung Spinpoint) and Gladys (300 GB Maxtor)

I've added this: options ahci.marvell_enable=1
to my /etc/modprobe.d/options

this identifies Kadence, lshw shows Kadence in it's output connected to the 6121 controller, but it's the only device.

Has anyone else had any success getting both SATA hard disks to identify with an IDE device? 

If more information is desired: please be specific with the commands required to generate it. I've only been using linux for a week.

Thanks very much in advance to anyone helping a newbie out.

Zee

---

