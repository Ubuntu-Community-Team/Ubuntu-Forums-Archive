---
title: "Busted computer"
date: 2007-10-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by John Jason Jordan on 2007-10-18
My laptop (Feisty amd64, completely up to date as of a week ago) has had periodic problems with hard disk corruption due to a faulty connector. The only way to fix it is to replace the motherboard, which would cost twice as much as the 2 1/2 year old computer is worth. The other day I got badly bitten and e2fsck made about a thousand repairs. Afterwards all seems to be well if I boot into Knoppix or Slax - the drive appears OK. However, it will no longer boot. A file has gone missing during the repairs, but after several hours puzzling over it I can't figure out what file it is. I also have a desktop running Feisty amd64, so sometimes I can copy files from it, but in this case I don't know what to copy. I also have full, recent backups, but only of ~/. I do have a complete copy of the whole drive, but it was made some time ago, perhaps back in the days of Edgy. I really don't want to format and start over because I have hundreds of programs installed, and a lot of the,m took some serious tweaking to get them to run in 64-bit Ubuntu. I am still hoping I can repair this, and with help from folks here, perhaps I can.

The boot screen hangs after only about half a centimeter across the progress bar. It occurred to me that I ought to try recovery mode to see what the boot process is hanging on. After running for several screens full, it finally resulted in the following:

Begin: Running /scripts/init-bottom ...
Done.
run-init: /sbin/init: No such file or directory
[   35.786176] Kernel panic - not syncing: Attempted to kill init!
[   35.786242]

Whereupon it hangs. 

Using a Knoppix CD I find the following in the /boot folder:

/boot
	/grub
		splashimages [folder]
		default
		device.map
		e2fs_stage1_5
		fat_stage1_5
		jfs_stage1_5
		menu.lst (looked at with Gedit, seems intact)
		menu.lst (various backup copies)
		minix_stage1_5
		reiserfs_stage1_5
		stage1
		stage2
		xfs_stage1_5
	abi-2.6.20-15-generic
	abi-2.6.20-16-generic
	config-2.6.20-15-generic
	config-2.6.20-16-generic
	initrd.img-2.6.17-11-generic.bak
	initrd.img-2.6.20-15-generic
	initrd.img-2.6.20-15-generic.bak
	initrd.img-2.6.20-16-generic
	initrd.img-2.6.20-16-generic.bak
	memtest86+.bin
	System.map-2.6.20-15-generic
	System.map-2.6.20-16-generic
	vmlinuz-2.6.20-15-generic
	vmlinuz-2.6.20-16-generic

This looks normal to me. The Grub boot menu lists the 15 and 16 kernels, recovery modes for each, and memtest (five items total). 

In / there are also:

initrd.img
initrd.img.old
vmlinuz
vmlinuz.old

So far I have renamed the initrd.img *.bak files so they are the regular files and renamed the original ones to *.old. I also copied the same files from the desktop computer (although they are smaller and have a different date stamp). And I also copied the /sbin/init file from the desktop and used it to replace the one on the laptop. It still hangs in exactly the same spot.

I hope someone here can tell me what it is trying to do at the point where I get the kernel panic, because the I don't understand what the error message means. Any suggestions for what might be missing/corrupted?

---

