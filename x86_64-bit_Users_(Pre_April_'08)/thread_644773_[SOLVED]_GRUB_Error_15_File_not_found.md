---
title: "[SOLVED] GRUB Error 15: File not found"
date: 2007-12-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by hangfire on 2007-12-19
GG 64 on an AMD 3400+, did an Adept update last night, got a new kernel. Great. Shut down.

Powered up this morning, got the grub list of kernel choices to boot, pick any one, get this error (hand typed):

[B]Error 15: File not found
Press any key to continue[/B]

There is no removable media. The hard disk is found because if finds the grub menu.

I am typing this from the Live CD.

I am not a happy camper. :confused:

Any ideas what went wrong? How to fix it?

---

### Post by hangfire on 2007-12-19
From the live CD, I chroot'ed to the root partition with boot mounted. The weird thing is, even through I saw it download a new kernel last night, and the menu.lst is dated as of that time, there is only my original install kernel listed:

```
title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd1,0)
kernel          /vmlinuz-2.6.22-14-generic root=UUID=9518b414-f5cd-49d5-b480-88b8500c3b35 ro quiet splash
initrd          /initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd1,0)
kernel          /vmlinuz-2.6.22-14-generic root=UUID=9518b414-f5cd-49d5-b480-88b8500c3b35 ro single
initrd          /initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd1,0)
kernel          /memtest86+.bin
quiet
```

/boot/vmlinuz-2.6.22-14-generic exists.
/boot/initrd.img-2.6.22-14-generic exists.



**man grub** is useless. info grub has the same useless MAN page that points you to info (????). THIS IS A DOCUMENTATION BUG. Grub should have easy-to-get-to INFORMATION. You know, INFO for people to FIX THINGS.

/proc/partitions does not work from chroot. It also does NOT list the same format as UUID is /etc/fstab. As a consequence, the new UUID scheme is USELESS to me because I CAN'T FIX ANYTHING IF I DON'T KNOW WHAT IT IS. (yes I am screaming here). Just like labels, someone thinks they are fixing something when in fact they are taking away the tools to fix everything.

6.06LTS on my laptop has been rock solid for me after I got the original install issues out of the way. My desktop with GG is now dead in the water and the tools to fix it have been removed.

Unless someone has some ideas FAST, this system is going Fedora Core (ugh) this afternoon. At least that boots.

---

### Post by Woody1987 on 2007-12-19
I have the exact same problem, any news on this?

---

### Post by Woody1987 on 2007-12-19
Fixed! turns out that the update had altered my hard drive mapping from hd(0,0) to hd(1,0), i simply reverted back and it worked.

---

### Post by hangfire on 2007-12-19
I fixed it. :)

The problem was either the UUID or the fact that it was trying to boot HD(1,0) when it should have been hd(0,0). I have a boot disk of /dev/sda (a SATA disk) but I also have a /dev/hda (ATA/IDE old linux disk). Perhaps this is an arrangement the updaters didn't anticipate.

[SIZE="4"]For a quick fix, try this:[/SIZE]

At the boot prompt, hit "e".
Edit the first line
Change **hd(1,0)** to **hd(0,0)**
hit 'b' to boot..

[SIZE="4"]If that doesn't work:[/SIZE]

Boot the live cd, Get a Konsole. 

**sudu bash**

(as root)

[B]mkdir /mnt/root
mount /dev/sda2 (or whatever) /mnt/root
mount /dev/sda1 (or whatever) /mnt/root/boot
chroot /mnt/root

vi /etc/fstab[/B]
(remove all UUID entries, replace them with the commented /dev/?[abc]# entries)
**vi /boot/grub/menu.lst**
(replace all UUID entries with  /dev/?[abc]# format entries).

save, exit (Ctrl-D), reboot.

---

### Post by hangfire on 2007-12-19
Woody,

You fixed it while I typed. Good for you!

If I had spent more time experimenting instead of typing, I would have had it fixed earlier. heh.

Anyway, I lost 1.5 hours to this problem, this morning.

Question- do you have a SATA boot and a second PATA/ATA/IDE disk like me? Or is this problem more generic?

---

### Post by tosk on 2008-02-05
I had the same problem. I have 2 internal SATA disks, one internal IDE optical drive (as Secondary Master), and one external USB HDD (identified as a SCSI).

SATA0 - /dev/sda - Windows XP NTFS
SATA1 - /dev/sdb - Ubuntu ext3
USBHDD - /dev/sdc - Storage FAT32
DVDRW - /dev/hdc

I think my problem was that when GRUB installs, it identifies the NTFS drive during it's BIOS probe and assigns it (hd0), but during boot, since GRUB can't read NTFS, it skips that drive and assigns SATA1 to (hd0). All I had to do was change menu.lst to read (hd0,0) for each of the Ubuntu options and it booted right up!

---

### Post by Cryptic1911 on 2008-02-06
I had the same issue on my dad's pc.. he had two ide drives, and two sata's, so his "root" drive was hd2,0. After the update, it stopped working, and I hit "e" during the grub menu and edited  the (hd2,0) to (hd0,0) and it booted, so then I edited the /boot/menu.lst file to reflect the change

---

### Post by hangfire on 2008-02-06
It just happened to me again, got another kernel, it changed my menu.lst to (hd1,0) from (hd0,0). I too used 'e' to boot and the vi to fix it after the fax.

Two disks, boot SATA, second PATA.

kernel updates are getting to be a REAL pain.

-HF

---

### Post by kurtpete on 2008-02-06
I have this issue, too.  If you're aware of it, and happen to remember when you update the kernel, you can modify your menu.lst before you restart (after applying the update) and then not have to do anything else fancy (live cd, etc...).

---

### Post by hangfire on 2008-02-12
Now, I REALLY fixed the problem, thanks to John Jason Jordan's post.

I changed the comment

**# groot=(hd1,0)**

to

**# groot=(hd0,0)**

Yes, comment. This is **NOT** documented in **man grub** or **info grub**. How it got set wrong in the first place, I have no idea.

I just got a new kernel today, and with the groot comment set, it didn't trash my menu.lst.

By the way, updatedefaultentry=false was already set in my menu.lst, and it trashed it anyway. Does it's position in the file matter?

-HF

---

### Post by M00_cow on 2008-02-29
Im not on 64 bit but yer, same problem... but your fix i.e. change hd(1,0) to watever trevor didnt work. Im completely nub. I've gone through every possible configuration mbers of hd(#,#) to no avail. Either get the error 15 or cannot mount selected partition. At the moment, the laptop has 2 sata drives, the first has vista (goes and throws up) and the 2nds got NTFS + linux partitions (Kubuntu 7.10 i thunk). Can someone give me an even more basic description of how to fix?

thanx

---

### Post by hangfire on 2008-03-22
Second disk- hd(1, *<something>*)

That *<something>* is the partition number, start counting from zero for the first partition.

However if you installed to the second disk when it was the first disk, and/or switched the disk recognition order in BIOS (some BIOS allow you to do that, some don't), you'll need to reinstall Grub.

-HF

---

### Post by KenWD0ELQ on 2008-03-31
I'm running (or, WAS running) Kubuntu 7.10 in a Microsoft Virtual PC 2007 window. I recently updated and now  I'm getting the same error that others are getting;  Error 15: File not found

My HD mapping says "root  (hd0,0)" , but again, that's for the one-and-only VIRTUAL disk, so "0,0" ought to be correct.

---

