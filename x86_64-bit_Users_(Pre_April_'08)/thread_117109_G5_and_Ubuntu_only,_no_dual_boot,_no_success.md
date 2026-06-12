---
title: "G5 and Ubuntu only, no dual boot, no success"
date: 2006-01-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by NOx4 on 2006-01-14
Hi folks,

I'm having problems starting Ubuntu in my G5 Dual 1.8 GHz. First steps go just fine, packages are copied to hdd. Problems start after this, cd out, reboot and then I get the cli which allows me to select OS. Because I have not other systems in my computer (single hard disk only for Ubuntu) options are linux and cd. If I select Linux system tries to load second stage bootstrap. This results a flashing question mark. If I select CD system will boot from the Ubuntu CD if it's in the drive.

Hdd partitions are #1 boot (1.0 MB), #2 ext3 (154 GB) for / and #3 swap (6.1 GB) for swap. Partition do no have names. This schema was created automatically by the Ubuntu installer. In the first place I had my own configuration with smaller partitions for ext3 and swap. In the installation options I used powerpc64, default didn't work at all.

I tried the OF OS selection by pressing option key during the startup. OF show me there's is Linux installed, I can select it but only thing I get is the same boot selection option (yaboot?). If I select Linux, it will bring me back to OF OS selection list.

To me it seem Linux doesn't find where it should boot from but I don't have a clue how to solve this problem. I'm a total newbie with Linux and Linux or Ubuntu tools and commands.

Any help and suggestions are welcome.

---

### Post by ssam on 2006-01-14
did you choose the powerpc 64 option when you booted the installer?

---

### Post by NOx4 on 2006-01-14
[QUOTE=ssam]did you choose the powerpc 64 option when you booted the installer?[/QUOTE]

Yes I did. The default option gave only a white screen.

Thanks for suggestion.

Can you tell something about the partitions in Linux? If I try something else than installer automatically opts I get lots of error messages. I reverted back and let the installer automatically create partitions.

I'm a bit confused with the partitions. There's a partition for boot. Then there's a partition for /, where the system gets installed. Swap is for swap, that is clear.

The first two partitions confuse me. Should they have names, sounds odd to me if that is the case? In what format should the boot be? Can the system root and boot be one and the same partition?

I manage OS X servers from the cli. Tools like diskutil are quite different from the Linux. I even don't know where to start from. 

I have only one computer at home, so after reading something I need to switch the disks in the chassis before trying new tricks. ;)

---

### Post by NOx4 on 2006-01-14
[QUOTE=ssam]did you choose the powerpc 64 option when you booted the installer?[/QUOTE]

Took a second look at the options. There's install-powerpc64 and oem-powerpc64. As I'm using G5 which is the right one (I used install-powerpc64)?

---

### Post by ssam on 2006-01-14
yaboot needs a small partiton that openfirmware can read to get yaboot started. from there yaboot reads the ext2/3 linux partiton can boots the kernel.

its slightly different on x86 machines (not the new apples, just normal ones). they have a master boot record (MBR) which is the first 512 bytes of a disk. grub (the x86 linux bootload) gets installed into the MBR.

on the unix filesystem there is a /boot directory. this contains the first few thing that the boot process need, eg the kernel. some people like to keep this on a seperate boot partion for various reasons. this is different form the boot partition on powerpc linux which contains just the boot loader.

ide drives in linux are lables hda, hdb, hdc... the partitions on hda would be hda1, hda2, hda3... a partition can be given a name, but this is not often done. to use mac os x, there must be a bunch of small partitions at the start of a disk (hda1 to hda8 for me), i think they hold things like drivers and firmware. they are probably worth keeping.

the method i use for partitioning a disk is to use apples disk utility to format the disk, and create any hfsplus partitions that you might want for mac os X, and leaving the rest (or all) of the disk as free space. this ensure that all the little partitons get created. then install mac os x if you need. then run the ubuntu installer and create a boot, swap and / partition in the free space. you should only be given a filesystem choice for the / partition, choose ext3 unless you know what you are doing. set the swap size to aboult 1 to 2 times the amount of ram you have.

sorry if that was a bit rambly, feel free to ask more questions.

---

### Post by NOx4 on 2006-01-14
[QUOTE=ssam]yaboot needs a small partiton that openfirmware can read to get yaboot started. from there yaboot reads the ext2/3 linux partiton can boots the kernel.
---
sorry if that was a bit rambly, feel free to ask more questions.[/QUOTE]

Thanks Sam,

that helped me to understand the Linux boot process. I'm familiar with the good(?) old DOS and OS X boot process.

Meanwhile I solved the problem, I'm sitting in front of Ubuntu and writing this reply with Firefox. :)

The problem was very simple but also surprising, at least to me. I simply switched my SATA disk from the lower slot to the upper slot which is default location for one disk configuration. I don't what is the problem, but believe it is related to yaboot/Ubuntu installer as I can run OS X from the slower slot/cabling/controller.

Started install-powerpc64 once again, did the default partitioning and that was it. Got the stage 2, Ubuntu booted from hard disk. Now it's updating components.

Thanks once again

---

### Post by ssam on 2006-01-14
glad you go it fixed.

maybe openfirmware considers it the first disk even if its on the second slot, whereas the kernel just uses the slot number, or the other way around.

---

