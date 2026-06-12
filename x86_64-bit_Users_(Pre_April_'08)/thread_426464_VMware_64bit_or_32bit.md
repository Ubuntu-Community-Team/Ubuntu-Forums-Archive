---
title: "VMware 64bit or 32bit"
date: 2007-04-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by scottishnarn on 2007-04-28
I'm running 4 virtual servers on a 64 bit machine (3 linuxes and 1 winXP). It's a server machine so the virtual servers are the only thing running other than openssh. Since, vmware server only runs using 32bit libraries, should I be using the 32 bit or 64 bit version of ubuntu? 

Thanks

---

### Post by Kilz on 2007-04-28
> **scottishnarn said:**
> I'm running 4 virtual servers on a 64 bit machine (3 linuxes and 1 winXP). It's a server machine so the virtual servers are the only thing running other than openssh. Since, vmware server only runs using 32bit libraries, should I be using the 32 bit or 64 bit version of ubuntu? 

Thanks

As an guess, Id say the 64bit version. Because it would allow you to use more ram. Secondly since you are not running any of the so called problem applications like proprietary web browser plugins or media codecs. There is nothing that makes the 64bit setup any harder.

---

### Post by pressureman on 2007-04-29
I can vouch for the stability of VMware server under 64 bit Ubuntu. I work for a company that has been running VMware server on Dapper 64 bit for almost a year now.

One particular box is a dual Opteron (each single core) with 16GB RAM and 3ware SATA RAID. This server runs eight guest VMs (mixture of Debian Linux and Win2K/2K3). It works pretty hard, considering it only has two cores, but it's absolutely rock solid, with an uptime of over 200 days (and one of the NICs has transmitted over 5.6 terabytes in that time!).

We are now migrating some servers to Feisty, mainly for the kernel support of newer 3ware RAID cards (the PCIe models).

---

### Post by eohman on 2007-05-22
Question for you PressureMan...

I recently turned up a Dual AMD Opteron with 6gb ECC and 8 SATA drives on Ubuntu x64 7.04 Fiesty. I couldn't get the RAID controller to work, so I access the drives directly.

The problem that i'm having is as follows:
1. System recognizing each volume separately - cannot mount each drive .. been using GPart and can SEE the volumes, they display as being mounted, however, i cannot write to the disks.

2. Trying to assign or use a "Physical" disk / drive in VMWARE 1.3 server. During the creation, when i click next to start formatting the vmware drive, it gives me a "no Access Rights" amongst many other messages.

I just need help getting over the hump and would be willing to hire someone to consult with to get this setup.

Thanks for any advice.

:popcorn:

---

### Post by pressureman on 2007-05-22
Firstly, contrary to my post above, I do not recommend Feisty as a host OS for VMware. We have found it to perform considerably slower than Edgy or Dapper. In actual fact, it seems to be a kernel issue, affecting 2.6.19  and later. It's not unreasonable, as these later kernels are not officially supported by VMware.

See [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/113532](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/113532)

So we are basing our VMware hosts on Edgy for now. It's a slight inconvenience with the 3ware 9650SE controllers, as they aren't supported natively in that kernel. It's easy enough to compile the updated 3w-9xxx driver supplied by 3ware though.

Be warned however - we're also experiencing some odd issues with the 9650SE controllers. None of the systems I've seen with this model of card running has had "Memory Write & Invalidate" enabled. This PCI option greatly improves the performance of the RAID, and I'm fairly sure we're noticing the performance degradation by not having it enabled. Previous 3ware models always seem to have it enabled. You can check whether or not it's enabled by looking for the flag "MemWINV" next to the 3ware card entry in the output of "lspci -vv". For example, this shows a 9650SE with MemWINV disabled:

```

0b:00.0 RAID bus controller: 3ware Inc Unknown device 1004 (rev 01)
        Subsystem: 3ware Inc Unknown device 1004
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr+ Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

```

and this shows a 9550SX with it enabled:

```

19:03.0 RAID bus controller: 3ware Inc 9550SX SATA-RAID
        Subsystem: 3ware Inc 9550SX SATA-RAID
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-

```

.... slight digression there, but hopefully helpful to others.

Anyway, eohman, some info on your RAID controller and motherboard would be helpful. I think you should try to get it working as a RAID rather than individual disks, since a RAID10 will increase your read/write performance by being able to write to multiple platters simultaneously. Of course, if it's a softraid or fakeraid, you might want to think twice, but hardware raid is well worth it.

I'd also do some more research on the merits of using physical partitions, versus VMDK's. Most of the stuff I've read suggests that the marginal performance increase of using physical partitions is not worth giving up the portability of a VMDK. We use VMDK's on top of ext3, mounted with noatime.

---

### Post by Matzu on 2007-05-25
Pressureman - thank you for the info - it sounds like you can recommend the 3Ware 9550-SX card as a good option for hardware RAID on Ubuntu Dapper Drake? I am building a new server as VMWare Host for primarily virtual Ubuntu LAMP servers, and I am looking for a rock solid and well performing option. I will be adding eight Western Digital SATA-II drives (raid edition). How would you recommend configuring the RAID? I am considering two RAID10 sets, but I would like to hear what you are using on your servers?

I was worried about the stability of the 9550-SX card, as I read some reviews indicating that the hardware failure rate might be quite high?

Your help is greatly appreciated!

---

### Post by pressureman on 2007-05-26
We had box running Ubuntu Dapper on a 3ware 9550SX card with 10 drives, and it ran under moderately heavy load for over 200 days straight. This box hosted about 10 or so VM guests (mixture of Linux, Win2K and Win2K3). That box has recently been rebuilt with Edgy, and is still performing like a champ.

So far I haven't personally seen any 3ware cards fail, but that's not to say it's impossible ;-)

Regarding the RAID configuration, if it's a single controller, my advice would be to configure it as a single RAID-10, rather than two. Assuming an average hard disk has a write speed of around 60 MB/s, a RAID-10 of four disks will be writing to two disks simultaneously (two striped mirror sets), so you will get around 120 MB/s. A RAID-10 of eight disks will be writing to four disks simultaneously (four striped mirror sets). So you will potentially get up to 240 MB/s. Try it for yourself... use something like bonnie++ to measure disk write speed with various array configurations, before you decide.

Of course these numbers will depend on various factors - are you using a 64 bit PCI card? Is it in a 66 MHz slot or 33 MHz? You see, a standard 32 bit, 33MHz PCI card tops out at 132 MB/s. So it's not much use having a RAID capable of writing data faster than the PCI bus can move the bits... whereas a 66MHz, 64 bit PCI card tops out at 528 MB/s. Most of the 3ware cards are 64 bit / 66MHz capable.

Oh, and I prefer AMD Opterons over Intel Xeons....  ;-)

---

### Post by CraigUTS on 2007-05-26
Hi,

I'm was very interested to see the previous poster had Ubuntu working with the 9650SE.
I've been trying to get this to work and failing miserably.
I've got an Asus P5BE-Plus with 9650SE and 4 disks
I can get Ubuntu 6.10 Server to install but when I reboot it generates fault messages that  I can't fathom:
Bad pte process vm_flags = 75

Did you do anything special to get the 9650SE to work?

Many thanks,

Craig.

---

### Post by Matzu on 2007-05-26
Pressureman - thank you very much for sharing your experience and insight on this issue! Based a. o. on your advice, I will go for the 3Ware Escalade 9550SXU-8LP controller and make it a RAID10 spanning all eight disks. Somehow, I remebered RAID10 as a four-drive only technology, but obviously it is possible to stripe across four drives and then mirror it - and certainly this is preferable. The motherboard is an ASUS P5M2 with PCI-X 133/100 MHz 64-bit slots, so the bandwith should be OK. The chip will be a Core 2 Duo @ 2.66 GHz, so it's not an opteron ;) I've had very good experience with Core 2 Duo and VMWare on Dapper, so I'll continue down that line though I do not doubt that opteron is also an excellent processor.

One additional question - why did you ugrade the Dapper box to Edgy? Is there any particular advantage to this when running a VMWare host?

---

### Post by Kilz on 2007-05-26
Just for your info, a Dapper server (because its a long term release)has support until sometime in 2011. Edgy will end support in 2008 (forcing you to upgrade).
IMHO Edgy was one of the worst releases to date. It only had 4 months of development and was rushed IMHO. I would think real hard about moving off of Dapper. Dapper is very stable.

---

### Post by pressureman on 2007-05-26
> **Kilz said:**
> Just for your info, a Dapper server (because its a long term release)has support until sometime in 2011. Edgy will end support in 2008 (forcing you to upgrade).
IMHO Edgy was one of the worst releases to date. It only had 4 months of development and was rushed IMHO. I would think real hard about moving off of Dapper. Dapper is very stable.

Those are valid points, and I certainly was not that impressed with Edgy desktop. However for a server, the amount of packages installed is quite minimal, so I don't see a lot of difference between Dapper and Edgy server, other than a newer kernel. I also found the Edgy install a bit cleaner, as it didn't install LVM/EVMS/mdadm by default.

I realise Edgy is not an LTS release, but I'm fairly confident we'll see another LTS before Edgy support runs out. In any case, they're not public-facing boxes, so security is not so critical.

---

### Post by pressureman on 2007-05-26
> **CraigUTS said:**
> I'm was very interested to see the previous poster had Ubuntu working with the 9650SE.
I've been trying to get this to work and failing miserably.
I've got an Asus P5BE-Plus with 9650SE and 4 disks
I can get Ubuntu 6.10 Server to install but when I reboot it generates fault messages that  I can't fathom:
Bad pte process vm_flags = 75

Did you do anything special to get the 9650SE to work?


Any kernel prior to 2.6.19 does not support the 9650SE natively. That version is when the updated 3w-9xxx driver was merged with mainline kernel.

To get around this, you need to use precompiled kernel modules and initrd images, available from 3ware at [http://www.3ware.com/KB/article.aspx?id=14546](http://www.3ware.com/KB/article.aspx?id=14546)

Beware that whenever you update your kernel, you need to overwrite the Ubuntu 3w-9xxx.ko module with the 3ware one (or your own compiled version, as I do), and run update-initramfs so that it rebuilds the initrd with the updated module, otherwise you won't be able to boot.

---

### Post by pressureman on 2007-05-26
> **Matzu said:**
> Somehow, I remebered RAID10 as a four-drive only technology, but obviously it is possible to stripe across four drives and then mirror it - and certainly this is preferable.

3ware's RAID-10 creates multiple RAID-1 mirrors, then stripes data across the mirror sets (this is the RAID-0 bit). There is a subtle different between RAID-10 (or RAID 1+0) versus RAID 0+1, in that RAID-10 is striped mirror sets, whereas RAID 0+1 is mirrored stripe sets.

See [http://en.wikipedia.org/wiki/Nested_RAID_levels](http://en.wikipedia.org/wiki/Nested_RAID_levels) for more information.

> **Matzu said:**
> The chip will be a Core 2 Duo @ 2.66 GHz, so it's not an opteron ;) I've had very good experience with Core 2 Duo and VMWare on Dapper, so I'll continue down that line though I do not doubt that opteron is also an excellent processor.

Once you have it running smoothly, have a look at running irqbalance. For some reason, Ubuntu 64 bit kernels do not have irq load balancing compiled in (kirqd), so all hardware interrupts end up getting serviced by CPU0. You can improved the performance of the box by running the userspace irqbalance daemon, which will distribute IRQs across all available cores.

> **Matzu said:**
> One additional question - why did you ugrade the Dapper box to Edgy? Is there any particular advantage to this when running a VMWare host?

The only reason was to have slightly newer packages of everything, and the most recent kernel (excluding the problematic 2.6.20 (and maybe 2.6.19) kernel. We had very stable performance on Dapper too, so it would be a perfectly reasonable choice to run with that.

---

### Post by Kilz on 2007-05-27
> **pressureman said:**
> Those are valid points, and I certainly was not that impressed with Edgy desktop. However for a server, the amount of packages installed is quite minimal, so I don't see a lot of difference between Dapper and Edgy server, other than a newer kernel. I also found the Edgy install a bit cleaner, as it didn't install LVM/EVMS/mdadm by default.

I realise Edgy is not an LTS release, but I'm fairly confident we'll see another LTS before Edgy support runs out. In any case, they're not public-facing boxes, so security is not so critical.

Last I read the next LTS is scheduled for Gutsy +2 and possibly +3 thats 18 months at minimum. Edgy has about 12 left.

---

### Post by Matzu on 2007-05-27
Thanks for the info - it seems the difference between 0+1 and 10 if all drives are on the same controller is minimal. Anyway the 3ware 9550SX supports RAID10 and not 0+1. I gather the 3Ware 9550SX is supported natively by Dapper, and due to the LTS situation, I think I will stick with dapper for now. Thanks also for the info on IRQ load-balancing, I will certainly follow your advice. I was not aware of this issue.

---

### Post by pressureman on 2007-05-27
> **Kilz said:**
> Last I read the next LTS is scheduled for Gutsy +2 and possibly +3 thats 18 months at minimum. Edgy has about 12 left.

Just because a particular release is not LTS, doesn't mean it's inherently unstable. The installation on our VMware servers is so minimal, and they do such a specific task, that I doubt we'll run into issues. A desktop install is another matter entirely, and Edgy desktop is probably responsible for some people's low opinion of Edgy.

We'd be running Feisty if it weren't for the problems with the 2.6.20 kernel, and that's not just an Ubuntu issue, it's distro-agnostic (trust me, I did a lot of testing before reverting to an older release). Hopefully Gutsy runs ok with VMware, because then we'll probably upgrade from Edgy -> Feisty -> Gutsy.

I think the LTS concept is a good idea, but the problem is that it ends up resembling Debian-stale, and newer hardware becomes a bit of a hassle to support. If you just want something rock solid, that's fine. But we've got bleeding edge hardware that needs to be supported (such as hardware virtualisation), and want the best possible performance out of these boxes.

---

### Post by Kilz on 2007-05-27
> **pressureman said:**
> Just because a particular release is not LTS, doesn't mean it's inherently unstable. The installation on our VMware servers is so minimal, and they do such a specific task, that I doubt we'll run into issues. A desktop install is another matter entirely, and Edgy desktop is probably responsible for some people's low opinion of Edgy.

We'd be running Feisty if it weren't for the problems with the 2.6.20 kernel, and that's not just an Ubuntu issue, it's distro-agnostic (trust me, I did a lot of testing before reverting to an older release). Hopefully Gutsy runs ok with VMware, because then we'll probably upgrade from Edgy -> Feisty -> Gutsy.

I think the LTS concept is a good idea, but the problem is that it ends up resembling Debian-stale, and newer hardware becomes a bit of a hassle to support. If you just want something rock solid, that's fine. But we've got bleeding edge hardware that needs to be supported (such as hardware virtualisation), and want the best possible performance out of these boxes.

No, I never said just because it wasnt a long term release it was unstable. I said it was unstable because imho it was rushed. Dappers is version 6.06 the version is its release date. Dappers release was 6th month of 2006. Edgy is version 610 or the 10th month off 2006. That means it only had 4 months of development vs the normal 6 months most versions of Ubuntu receive. I think it showed. True its had some time to get updated. But Dapper has had a longer time, its rock solid.
What I was pointing out about the LTS is its end of life. Some people like to update every release, but some people want to have a machine, and not have to think about the upgrade for a bit. 
I have a Dapper server, and a Dapper Desktop. They do all I need them to do. To often imho people get into the "I must have the latest" mentality. Thats fine if you need something , like a driver that was added, or an application that isnt available in older versions. But there is something good to be said about a operating system that is stable and still has plenty of life left in it. 
To often people install the latest only to find bugs and problems. Edgy wouldnt be a bad option, now. But the problem is, in no time you will have to move to another version with possibly a new set of issues. All the while, I will sit back and enjoy what works. :D 
Feel free to hype the latest, just as I will share the info that sometimes, all it is is hype and bugs. That way the user can make an informed decision.

---

### Post by pressureman on 2007-05-28
Good points again.... but I don't entirely agree with saying that Edgy is unstable because it only had four months of rushed development. Breaking up the development of the OS into discrete chunks like six months is irrelevant. The development is a continual, evolutionary process. Upstream source release timeframes are not driven by marketing departments, like certain other OSes. In any case, you may be referring to Edgy desktops being unstable - which may well be the case... but I'm not running Edgy desktop here.

I think you and I are talking about different requirements. I agree that most people want the latest on their desktop, but to be honest, there is stuff all difference between releases for console mode servers, other than the kernel. Most of the instability I've seen come about is due to the large number of patches that Ubuntu applies against mainline for support of every possible known gadget, and desktop bling, neither of which I care about on a server.

What I do care about though, is that my array controller is supported, and that the box runs fast when under load. We have modern hardware to support. We invested substantial cash in an 8-way Xeon box with 16GB RAM. This box supports hardware virtualisation, so we needed to run a modern kernel to take advantage of that. Unfortunately I was only able to have one of those with Feisty, hence my downgrade to Edgy.

I spent a lot of time and effort benchmarking the various releases of Ubuntu (in essence, the various kernel releases), and settled on Edgy for reasons of performance. This is a biggish VMware server that needs to run as well as it can. That means not only stability, but speed. Maybe we'll upgrade it to Gutsy when it comes out, or Gutsy+1. Maybe we'll migrate all the VMs to ESX, or Xen, or KVM... Whether or not we use an LTS release is irrelevant to me. This thread is about VMware servers, not public facing web or ftp servers, where conservatism might be preferred.

As for people installing the latest, only to find bugs and problems... well, that's how things get fixed. If nobody ran the new versions, it would take a long time for development to move to the next step. If you've got the time and expertise, it's a good way to contribute back to the community.

I don't intend to upgrade servers every six months (although I do with my desktop install). But if I wanted to run a kernel from the stone age, I'd be using Red Hat.

---

