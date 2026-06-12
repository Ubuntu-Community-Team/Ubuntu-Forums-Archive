---
title: "RAID setup for p5w dh???"
date: 2007-03-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by saru411 on 2007-03-26
hi there,
   im following this howto ( [http://www.ubuntu-in.org/wiki/SATA_RAID_Howto](http://www.ubuntu-in.org/wiki/SATA_RAID_Howto) ) to setup my raid 5 array with fakeraid. the first problem i come to in this howto is it asks me to look for dev/mapper/nvidia_gahbaaab on the top right.....but i only see my 4 hdds as 4 different hdds, not 1 hdd. i also dont see mapper under the dev folder. im going about this by running edgy eft in safe graphics mode from cd on a freshly setup raid 5 array. thanks for your time and ask me for more info if its needed

---

### Post by saru411 on 2007-03-29
hello again nice people of ubuntu

i finally decided to go with the software raid on the edgy 6.10 alt cd. i built 2 raid arrays out of my 4 hdds(320 gb each).

i have it set up like this

hda 320.1gb
    logical 3gb k raid(part of raid 0 array)
    logical 317.1 gb k raid (part of raid 5 array)
hdb 320.1 gb
    logical 3gb k raid(part of raid 0 array)
    logical 317.1 gb k raid (part of raid 5 array)
hdc 320.1gb
    logical 3gb f swap swap
    logical 317.1 gb k raid (part of raid 5 array)
hdd 320.1 gb
    logical 3gb k reiserfs (for other distros i might want to try out)
    logical 317.1 gb k raid (part of raid 5 array)

i then see this

RAID0 device #0 - 6.0 gb
RAID5 device #1 - 951.2 gb

so i set both of these as lvm drives and proceed to configure them as such -

(ok while writing this im retracing my steps from last night. while trying to see where i got stuck last night and i cannt configure the lvm volumes atm)

vg1 - 6gb (raid0)
    lg1 - 6 gb as boot
vg2 - 951.2 gb (raid5)
    lg2 - 951.2 gb as home

now the cd i have never stopped me to ask if i was to install grub or lilo.....i want to install lilo.
and it installed grub first then after i installed lilo.

now as stated previously i have gotten stuck at the lvm now since i rebooted my pc from last night and have lost my lvm partition table. everytime i go into lvm i get an error that tells me to alt f3 to terminal3 but there are no error codes there, so im kind of lost on how to proceed.

again thanks for the help whoever answers

---

### Post by saru411 on 2007-04-02
well now im fubared. i have been trying to reinstall using the alt cd for edgy/feisty/and edgy kubuntu, none of which let me get past the partitioner. once i select to partition a disk it says something about my dev0 not working. basically i cannt install over my current install, which wont boot. i get a bios bug error at the begining(even when attempting a fresh install) of every boot immediatly after the post.

what i want to do now is completely format all of my hdds including their primary partition tables. i want them to look like they did when i got them from the manufacturer. if you can help please do, im starting to think linux wont ever work for me :(

---

### Post by Velociraptor on 2007-04-04
Are/were you trying to use dmraid for your raid arrays? I managed to get this working on Edgy using the following howto's: 

[https://help.ubuntu.com/community/FakeRaidHowto]("https://help.ubuntu.com/community/FakeRaidHowto")
[https://wiki.ubuntu.com/FakeRaidEdgy]("https://wiki.ubuntu.com/FakeRaidEdgy")

Note: The first howto above describes how to partition the drives using fdisk. The partitioner used by the installer (gparted?) can't handle fake raid so well.

But for dmraid I would seriously recommend using Feisty, because the dmraid package is not broken :) However, there is a known bug, that prevents it from booting. But there is a simple workaround for that, see:

[https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/83231]("https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/83231")

---

### Post by John Jason Jordan on 2007-04-04
> **saru411 said:**
> what i want to do now is completely format all of my hdds including their primary partition tables. i want them to look like they did when i got them from the manufacturer. if you can help please do, im starting to think linux wont ever work for me :(
I had similar problems trying to use the fakeraid on the motherboard (Abit NF-M2S) for a new computer I just built. It was more trouble than it was worth, plus I spoke to a lot of Linux people and they assured me the Linux software RAID was much better anyway. I wanted to set up just RAID 1 because I wanted to use the machine for backups. It has two 320 GB SATA II drives.

I also found that regular Ubuntu install media can't do RAID, you have to use the Alternate version. I wanted only a 64-bit version of Linux. I tried Edgy and Feisty and neither would work. I kept getting stuck. I also tried various other distros -- straight Debian (latest), Mandriva-free-2007, OpenSUSE 10.2, Mepis, among a couple of others. Most used a command line interface for creating the RAID and it was very difficult to figure out. Finally I tried Fedora Core 6, which was the first one where I got close to success. Then I tried Fedora 7 test2 and was able to create the RAID 1 setup that I wanted -- a 2 GB swap, a 40 GB partition for the OS, and the remainder for backups. These are called MD0, MD1 and MD2 respectively.

One I had the RAID partitions set up I tried the other distros again and a couple of them were able to see the MD raid partitions, including Feisty amd64 Alternate. I went ahead and installed Feisty. While I had been unable to use it to create the RAID parttions, once I had them created with F7 test 2 I had no problem installing Feisty amd64 on the RAID partitions. 

However, Feisty did not care much for the motherboard. It could not recognize even the Realtek gigabit or the nVidia GeForce 6100 video onboard. In fact, the only thing on the motherboard that it set up was the audio. As a result I went back to Fedora 7 test2 for this computer. F7 test2 still won't work with the gigabit, although at least it recognizes it, and it does recognize the video and even the monitor, both of which it set up automatically. I'll try Feisty again when it is final later this month. 

I would suggest that you try other distros to see if one of them will get your RAID set up properly the way you want it. I suspect that Feisty will then be able to install itself on the RAID partitions once they have been created.

---

### Post by saru411 on 2007-04-04
well, just an update on things. i installed edgy 6.10 64bit and then finally got all of my previous problems fixed. i found out rebooting after each install of new drivers/apps/ect works much better for me. i believe it had to do with all the updates you install after a fresh install, who knows. i do know my nvidia is working, so is beryl, and also my on board sound device. only thing left is the raid set up. i like the idea of installing fedora 7 test2 to give me more flavors of linux since im such a n00b. thanks for the tips and may the ubuntu be with you =)

---

