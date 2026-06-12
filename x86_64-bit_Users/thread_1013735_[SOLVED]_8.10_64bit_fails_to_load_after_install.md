---
title: "[SOLVED] 8.10 64bit fails to load after install"
date: 2008-12-17
forum: x86 64-bit Users
---

### Post by 73ckn797 on 2008-12-17
I have installed Intrepid 8.10 64bit. Initially performed checksums and then self test for disk on Live CD boot. Installed OS and all appeared to go smoothly. 

When booting into OS the system stops at a certain point (see photos of screen). This occurs whether booting into system normally or via Recovery mode.

Any suggestions?

Should I install Hardy 64 bit instead? I have loaded it previously with no problems. System specs in signature. Loaded on desktop system.

---

### Post by dabl on 2008-12-17
Google found this thread:

[http://linux.derkeiler.com/Mailing-Lists/Fedora/2008-01/msg04465.html](http://linux.derkeiler.com/Mailing-Lists/Fedora/2008-01/msg04465.html)

which suggests the problem has to do with the partition labels on multiple hard drives.  Are you booting "by-label"?  and is it possible you've got a duplication of labels, or something inconsistent in /etc/fstab, vs. the actual labels on the partitions?

Here is another possibility:

[http://saalwaechter-notes.blogspot.com/2008/10/requestmodule-runaway-loop-modprobe.html](http://saalwaechter-notes.blogspot.com/2008/10/requestmodule-runaway-loop-modprobe.html)

But that should not happen on a fresh 64-bit installation -- where would you get a 32-bit kernel?

---

### Post by 73ckn797 on 2008-12-17
> **dabl said:**
> Google found this thread:

[http://linux.derkeiler.com/Mailing-Lists/Fedora/2008-01/msg04465.html](http://linux.derkeiler.com/Mailing-Lists/Fedora/2008-01/msg04465.html)

which suggests the problem has to do with the partition labels on multiple hard drives.  Are you booting "by-label"?  and is it possible you've got a duplication of labels, or something inconsistent in /etc/fstab, vs. the actual labels on the partitions?

Here is system info of disk installed on:
```
Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        8998    72276403+  83  Linux
/dev/sdb2            9729       19457    78148192+   7  HPFS/NTFS
/dev/sdb3            8999        9728     5863725    5  Extended
/dev/sdb5            8999        9728     5863693+  82  Linux swap / Solaris
```
```

sudo blkid
/dev/sda1: UUID="32dd3252-53b9-4647-b538-95793e7a55e2" TYPE="ext3" LABEL="Ubuntu" 
/dev/sda5: TYPE="swap" UUID="d81a0c0e-1b88-40fb-abed-2c9b15d0db6f" 
/dev/sdc1: UUID="B2B0D32BB0D2F537" LABEL="Backups" TYPE="ntfs" 
/dev/sdd1: UUID="48EA-8696" TYPE="vfat" LABEL="BACKUPFLASH" 
/dev/sdb4: TYPE="swap" UUID="67e9932c-9bf7-4186-b147-0b534ed4080f" 
/dev/sdf1: SEC_TYPE="msdos" UUID="48EA-8696" TYPE="vfat" LABEL="BACKUPFLASH" 
/dev/sde1: SEC_TYPE="msdos" UUID="48EA-8696" TYPE="vfat" LABEL="BACKUPFLASH" 
/dev/sdd5: TYPE="swap" UUID="bf5881cf-1674-4f8e-a1b7-96083c9f0dd2" 
/dev/sdg1: UUID="48F4-EAEE" TYPE="vfat" SEC_TYPE="msdos" 
/dev/sdd2: UUID="1306a0e0-da49-4c2a-bc75-87a7c682aba3" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdh1: UUID="96E0-B4FA" TYPE="vfat" SEC_TYPE="msdos" 
/dev/sdi1: SEC_TYPE="msdos" UUID="48EA-8696" TYPE="vfat" LABEL="BACKUPFLASH" 
/dev/sdb5: TYPE="swap" UUID="0821b7d3-f061-4264-be80-c5656a61ddb4" 
/dev/sdc3: UUID="4f92449d-38a5-4453-b22e-9e3785987a02" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc4: TYPE="swap" UUID="67e9932c-9bf7-4186-b147-0b534ed4080f" 
/dev/sdc5: TYPE="swap" UUID="4e1e2438-4522-4134-95c5-af5de6d4b796" 
[B]/dev/sdb1: UUID="70c85158-82db-4bab-9526-b94f1695af1e" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb2: UUID="7A64FC0A64FBC743" LABEL="WinDocs" TYPE="ntfs"[/B] 
```

**Grub:**
```
title        Ubuntu 8.10, kernel 2.6.27-7-generic
uuid        32dd3252-53b9-4647-b538-95793e7a55e2
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=32dd3252-53b9-4647-b538-95793e7a55e2 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-7-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid        32dd3252-53b9-4647-b538-95793e7a55e2
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=32dd3252-53b9-4647-b538-95793e7a55e2 ro  single
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu 8.10, memtest86+
uuid        32dd3252-53b9-4647-b538-95793e7a55e2
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


# This entry automatically added by the Debian installer for a non-linux OS
## on /dev/sdd1
title Windows XP
root (hd0,0)
chainloader +1


title        Ubuntu 8.10 64 bit, kernel 2.6.27-7-generic
uuid        70c85158-82db-4bab-9526-b94f1695af1e
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=70c85158-82db-4bab-9526-b94f1695af1e ro quiet splash 
initrd        /boot/initrd.img-2.6.27-7-generic
quiet

title        Ubuntu 8.10 64 bit, kernel 2.6.27-7-generic (recovery mode)
uuid        70c85158-82db-4bab-9526-b94f1695af1e
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=70c85158-82db-4bab-9526-b94f1695af1e ro  single
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu 8.10 64 bit, memtest86+
uuid        70c85158-82db-4bab-9526-b94f1695af1e
kernel        /boot/memtest86+.bin
quiet
```

I will look into the link you provided later. Have to leave for work now.
I figured the system info may be of some help.

Thanks for your help and I will see what happens and follow-up.

---

### Post by dabl on 2008-12-17
OK -- look at your partition labels.  What's the deal with that "BACKUPFLASH" appearing as different devices and partitions, but all with the same UUID?  I think that's probably the problem that's keeping it from booting.

The other concerning thing that I see in your system configuration is the Grub menu list.  Did you manipulate it in any way, or is that how the installer wrote it?  The format is weird, in my experience -- ubuntu should not be listed below the "end automagic kernels" line, only your non-ubuntu OSs should be there.  Here's the relevant part of mine, so you see what I mean:

> ## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-9-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=4ee99d57-a4e3-4381-a900-7a57cfa9eea2 ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=4ee99d57-a4e3-4381-a900-7a57cfa9eea2 ro xforcevesa  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=4ee99d57-a4e3-4381-a900-7a57cfa9eea2 ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=4ee99d57-a4e3-4381-a900-7a57cfa9eea2 ro xforcevesa  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title .
root

title Other operating systems:
root

title .
root

title	Debian sidux GNU/Linux, kernel 2.6.27-9.slh.1-sidux-amd64
root	(hd4,0)
kernel	/boot/vmlinuz-2.6.27-9.slh.1-sidux-amd64 root=UUID=26138929-7ea6-4893-8c3a-03c13e24a4d1 ro quiet vga=791 
initrd	/boot/initrd.img-2.6.27-9.slh.1-sidux-amd64

title	Debian sidux GNU/Linux, kernel 2.6.27-8.slh.1-sidux-amd64
root	(hd4,0)
kernel	/boot/vmlinuz-2.6.27-8.slh.1-sidux-amd64 root=UUID=26138929-7ea6-4893-8c3a-03c13e24a4d1 ro quiet vga=791 
initrd	/boot/initrd.img-2.6.27-8.slh.1-sidux-amd64

Also, I do believe it needs to say "root" ahead of the partition where the kernel is/are, not just "UUID" like yours says.

For future reference (irrelevant to your problem, AFAIK), you only need one swap partition anywhere on the system.  It will be used by whatever Linux you boot, so you've got wasted space in the multiple swap partitions.  :mad:

---

### Post by 73ckn797 on 2008-12-17
> **dabl said:**
> OK -- look at your partition labels.  What's the deal with that "BACKUPFLASH" appearing as different devices and partitions, but all with the same UUID?  I think that's probably the problem that's keeping it from booting.

Backup flash is a 1Gib memory stick I leave plugged into the mobo at the rear. (edit out incorrect comment) There was, at the time, a 4Gib flash plugged in also at the front panel but that number is different. Could the duplicate number come from the 8.04 to 8.10 updating?

> **dabl said:**
> The other concerning thing that I see in your system configuration is the Grub menu list.  Did you manipulate it in any way, or is that how the installer wrote it?  The format is weird, in my experience -- ubuntu should not be listed below the "end automagic kernels" line, only your non-ubuntu OSs should be there.  Here's the relevant part of mine, so you see what I mean:

 I did copy the latter section from the menu.lst created by the 64bit install. Upon initial, after install boot, the 64bit had not been written into the 32bit menu.lst. I will move that up ahead of the Windows info, above the automagic comment. Does it matter about the kernel number being the same? I figure as long as it reads from the correct drive that it should not matter. I may be figuring incorrectly!?

> **dabl said:**
> Also, I do believe it needs to say "root" ahead of the partition where the kernel is/are, not just "UUID" like yours says.

The grub uuid lines were written by the installation.

> **dabl said:**
> For future reference (irrelevant to your problem, AFAIK), you only need one swap partition anywhere on the system.  It will be used by whatever Linux you boot, so you've got wasted space in the multiple swap partitions.  :mad:

That can be easily remedied.

I will play around and see what happens.

---

### Post by 73ckn797 on 2008-12-18
> **dabl said:**
> OK -- look at your partition labels.  What's the deal with that "BACKUPFLASH" appearing as different devices and partitions, but all with the same UUID?  I think that's probably the problem that's keeping it from booting.

My earlier comments were in ignorance. I completely missed the duplicate uuid of the flash drive you mentioned. If that is causing a problem it is only affecting the 8.10 64bit.  My regular intrepid boots up with no problems. I did an upgrade from Hardy to Intrepid. Would that be the cause of the duplication?

Any suggestion on changes to the menu.lst?

---

### Post by dabl on 2008-12-18
> **73ckn797 said:**
> My earlier comments were in ignorance. I completely missed the duplicate uuid of the flash drive you mentioned. If that is causing a problem it is only affecting the 8.10 64bit.  My regular intrepid boots up with no problems. I did an upgrade from Hardy to Intrepid. Would that be the cause of the duplication?

Any suggestion on changes to the menu.lst?

I would recommend, as an experiment to narrow down where the problem is, editing your menu.lst file, just for the 64-bit kernel that you're trying to boot.  Use my menu.lst as an example, and edit the first stanza under "## ## End Default Options ##" so it looks like mine, using the UUID number of the partition where your system is installed, and using the "root (hd1,0)" notation instead of the "UUID" notation on the root line of the stanza.

So, if I understand your setup correctly, that first stanza will look like this:

```
title Ubuntu 8.10, kernel 2.6.27-7-generic
root (hd1,0)
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=470c85158-82db-4bab-9526-b94f1695af1e ro quiet splash
initrd /boot/initrd.img-2.6.27-7-generic
quiet
```

Save it, and reboot, and see what happens.  If it boots correctly, then you'll want to edit the recovery mode stanza as well, to match.

BTW, you've probably already figured out that this issue, like 90% of the other threads on this sub-forum, is totally unrelated to "64-bit" -- it's just a problem mapping to the kernel location.  I think you've presently got it mapped to the 32-bit kernel, generating the error as reported in the second link that I posted before.

:)

---

### Post by 73ckn797 on 2008-12-18
> **dabl said:**
> I would recommend, as an experiment to narrow down where the problem is, editing your menu.lst file, just for the 64-bit kernel that you're trying to boot.  Use my menu.lst as an example, and edit the first stanza under "## ## End Default Options ##" so it looks like mine, using the UUID number of the partition where your system is installed, and using the "root (hd1,0)" notation instead of the "UUID" notation on the root line of the stanza.

So, if I understand your setup correctly, that first stanza will look like this:

```
title Ubuntu 8.10, kernel 2.6.27-7-generic
root (hd1,0)
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=470c85158-82db-4bab-9526-b94f1695af1e ro quiet splash
initrd /boot/initrd.img-2.6.27-7-generic
quiet
```Save it, and reboot, and see what happens.  If it boots correctly, then you'll want to edit the recovery mode stanza as well, to match.

BTW, you've probably already figured out that this issue, like 90% of the other threads on this sub-forum, is totally unrelated to "64-bit" -- it's just a problem mapping to the kernel location.  I think you've presently got it mapped to the 32-bit kernel, generating the error as reported in the second link that I posted before.

:)

Thanks for the info. I will look into it further and get back.

As I mentioned in an earlier post, I ran the disk self test and it checked good. I have a suspicion that there still may be a problem with the disk. When I burned it, Brasero kicked an error after completing the burn. It may not have anything to do with any of this but it is a concern. I downloaded the iso again and reburned using Gnomebaker with no errors. I will be loading that in place of the previous install and see what happens.

Brasero has been giving problems recently. Why I do not know. Too many things to keep up with lately. Otherwise Ubuntu has been a great experience and reliable OS.

---

### Post by 73ckn797 on 2008-12-18
> **dabl said:**
> I would recommend, as an experiment to narrow down where the problem is, editing your menu.lst file, just for the 64-bit kernel that you're trying to boot.  Use my menu.lst as an example, and edit the first stanza under "## ## End Default Options ##" so it looks like mine, using the UUID number of the partition where your system is installed, and using the "root (hd1,0)" notation instead of the "UUID" notation on the root line of the stanza.

So, if I understand your setup correctly, that first stanza will look like this:

```
title Ubuntu 8.10, kernel 2.6.27-7-generic
root (hd1,0)
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=470c85158-82db-4bab-9526-b94f1695af1e ro quiet splash
initrd /boot/initrd.img-2.6.27-7-generic
quiet
```Save it, and reboot, and see what happens.  If it boots correctly, then you'll want to edit the recovery mode stanza as well, to match.



EDIT

I used your example, changing the uuid to suit. First reboot failed with the same results in my first post. The physical setup of my drives and the order in the bios places the drive with the 64 Ubuntu as hd2, which is the actual bios order. I changed that and 64 boots perfectly.

I will edit the remainder of the menu.lst for the 64bit mapping.

The menu.lst created on the 64 install in /boot/grub has everything referring to hd* screwed up. It must read hd0 as the drive it is on because trying to boot with that grub setup results in errors trying to boot Ubuntu 32, 64 and Win XP. WinXP is actually on hd0, Ubuntu 32 on hd1 and Ubuntu 64 hd2 which is the physical and bios order. Even the drive order in gparted has it all mixed up.

I have always had issue with the hd* configuration created on Ubuntu installations. That has always been the cause of problems with every Ubuntu install I have performed. I understood the use of uuid to be the new way of things, at least I thought I read that somewhere on the forums or documentations.

This reply is through the 64 bit OS.

---

