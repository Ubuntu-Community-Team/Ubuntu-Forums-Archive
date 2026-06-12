---
title: "64bit won't see partitions"
date: 2005-12-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by michellembrodeur on 2005-12-11
I have partitioned my WD 200 GB sata drive into

Boot (300 megs about) Smallest it can be. This is for XOSL for multiboot.
Win-XP 20 gigs  NTFS
Storage 100 gigs Fat 32
/ 20 gigs
swap 1.5 gigs
home 15 gigs
The rest for Games fat 32

The thing is 64bit Kubuntu sees it all as a 200 Gig SCSI drive. It won't see any partitions. So I wiped everything out and did it over again with using the Kubuntu partitioner and installed Kubuntu.
But after installing win-xp and using XOSL to see both OS's kubuntu won't start.

Any help will be appreciated.
thanks in adavanced.

---

### Post by tomcoussement on 2005-12-15
It's better to install windows xp before installing linux and use grub as bootloader.

You can solve your problem by booting from live cd 
chroot into your linux on hd and run grub-install.

If you can boot your linux after that, you can adjust your /boot/grub/menu.lst to be able to dualboot linux/windows.

---

### Post by michellembrodeur on 2005-12-15
I thank you for your help.
But once I booted into LIVE, I was really kind of lost.

Can you please explain in detail what I should do.
Write out the lines and where I what I should type and so forth.

I went to a shell and typed run grub-install and errors only.

I am still pretty new to this.

thanks
Michelle


[QUOTE=tomcoussement]It's better to install windows xp before installing linux and use grub as bootloader.

You can solve your problem by booting from live cd 
chroot into your linux on hd and run grub-install.

If you can boot your linux after that, you can adjust your /boot/grub/menu.lst to be able to dualboot linux/windows.[/QUOTE]

---

### Post by psusi on 2005-12-15
What is this "XOSL"?

Usuaully installing ubuntu after windows just works fine out of the box.  

When you install windows, have it create only a single partition to install on.  Then install ubuntu, and have the installer make the other partitions.  It should automatically set up grub to dual boot with windows.  

By the way, I'm not sure why you said 300 MB is the minimum size for /boot.  Mine is just under 50 MB.

---

### Post by michellembrodeur on 2005-12-15
XOSL is a boot manager so you have have a lot of different OS's installed. Was going to put more of them in later.

Next, Kubuntu would not see any of the partitions on my SATA 200 GIG WD HD. It saw all 6 of the partition as one whole 200 gig partition.

That is my main problem.

Next with ACRONIS the smallest partition I could make was the one about 300 megs. Remember it is a 200 gig drive.

So what do I do when I use LIVE to boot up in. To see the other drives and fix the grub.

thanks

Michelle


[QUOTE=psusi]What is this "XOSL"?

Usuaully installing ubuntu after windows just works fine out of the box.  

When you install windows, have it create only a single partition to install on.  Then install ubuntu, and have the installer make the other partitions.  It should automatically set up grub to dual boot with windows.  

By the way, I'm not sure why you said 300 MB is the minimum size for /boot.  Mine is just under 50 MB.[/QUOTE]

---

### Post by tburns on 2005-12-15
[QUOTE=michellembrodeur]XOSL is a boot manager so you have have a lot of different OS's installed. Was going to put more of them in later.

Next, Kubuntu would not see any of the partitions on my SATA 200 GIG WD HD. It saw all 6 of the partition as one whole 200 gig partition.

That is my main problem.

Next with ACRONIS the smallest partition I could make was the one about 300 megs. Remember it is a 200 gig drive.

So what do I do when I use LIVE to boot up in. To see the other drives and fix the grub.

thanks

Michelle[/QUOTE]


How many primary partitions do you have? You might try to trim it down to three primary partitons and a swap.

---

### Post by michellembrodeur on 2005-12-16
[QUOTE=tburns]How many primary partitions do you have? You might try to trim it down to three primary partitons and a swap.[/QUOTE]


Only have two primary, windows XP and Kubuntu Root.

Its just that 5.10 won't see any partitions.

---

