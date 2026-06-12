---
title: "Kernel panic during boot (after kernel update)"
date: 2005-06-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by cobalt on 2005-06-12
After updating the kernel from the update manager, my computer refused to boot up again. I've tried to boot from grub using all the possible kernel choices (recovery mode etc) but none of them helped.

I've attached a picture of the error message which occurs while booting. (Actually it's a shot from a earlier problem which I got fixed, but as the error message is exactly the same, didn't bother to take a new picture. But because of this the kernel version number might be incorrect?)

I have a live cd to work with, but at the moment I have no idea how I could fix this. There have been partially similar threads about this, but none of them has given me a satisfying and understandable solution. Someone mentioned that copying the kernel from a live cd might help, but I have no idea how to do it.

I believe many other amd64 or reiserfs users or kernel updaters have had the same problem. Hopefully someone has solved it.

---

### Post by elvis on 2005-06-24
It seems the reiserfs stuff is working, but maybe udev isn't (now that devfs is depreciated).  Have you got udev installed?  If not...

I would:

1) Boot from a LiveCD

2) Mount your hard disk's partitions

3) chroot into the mount

4) mount the chroot'ed environment's /proc

5) apt-get install udev

6) exit/umount/reboot

And see what happens.

---

### Post by skoal on 2005-06-24
What is /dev/hdd1? Do you have SATA disks per chance?

\\//_

---

### Post by mohaham on 2005-06-24
should'nt that be /dev/hda1
can u post the /boot/grub/menu.lst  file here..

---

### Post by skoal on 2005-06-24
IDE Raid array maybe?

\\//_

---

### Post by elvis on 2005-06-24
[QUOTE=mohaham]should'nt that be /dev/hda1
can u post the /boot/grub/menu.lst  file here..[/QUOTE]

Well where ever hdd1 points to, it found a kernel and decompressed it OK.  The error is after that.

---

### Post by skoal on 2005-06-25
The error is in the initrd, these lines in (<ramdisk>/sbin/init) to be precise (I believe):
```
if [ $rootdev != 256 ]; then
        mount_root
        cd mnt
        [ $DEVFS ] && mount -nt devfs devfs dev
        [COLOR=DarkRed]pivot_root . initrd[/COLOR]
fi
if ! [ -x ${init#/} ]; then
        init=/sbin/init
fi
if type chroot > /dev/null 2>&1; then
        [COLOR=DarkRed]exec chroot . $init "$@" < dev/console > dev/console 2>&1[/COLOR]
fi
exec $init "$@" < dev/console > dev/console 2>&1
```
[list]
[*]:. Init cannot find the drive/partition /root is on.  No devices made...hmm...
[*]recent kernel update script (in rules) changed root partition in grub entry?  Thus, what is hdd1?
[*]You have a SATA controller? I'm no expert on VIA/NFORCE/AMD/ETC., but maybe you have a module missing from loading during init, one of these maybe:
skoal@morpheus:///lib/modules/2.6.10-5-686 $ find . -name sata* -type f
./kernel/drivers/scsi/sata_sil.ko
[COLOR=DarkRed]./kernel/drivers/scsi/sata_sis.ko[/COLOR]
./kernel/drivers/scsi/sata_sx4.ko
./kernel/drivers/scsi/sata_svw.ko
./kernel/drivers/scsi/sata_uli.ko
[COLOR=DarkRed]./kernel/drivers/scsi/sata_via.ko[/COLOR]
./kernel/drivers/scsi/sata_vsc.ko
[COLOR=DarkRed]./kernel/drivers/scsi/sata_nv.ko[/COLOR]
./kernel/drivers/scsi/sata_promise.ko

1. Boot from live CD, mount your initrd (/boot/initrd-2.6.10-???) under /mnt, like this:
'sudo mount -t cramfs -o loop /boot/initrd.img-2.6.10??? /mnt'
2. What does:
'cat /mnt/loadmodules'
give?

What's your motherboard and chipset? Nforce maybe?

[*]Can you still boot from an older (prior) Ubuntu kernel? Or have you only been using the live CD up to this point? What kernel versions have you tried before? Have any worked succesfully until this point?
[*]/dev/hda1 (hd0,0) = /boot, /dev/hdd1 (2nd cdrom?)= /root.  Either your ide driver for your chipset is confused (likely), or your /boot/grub/menu.lst entries are fubar'd (unlikely)...
[/list]

** Physical drive layout/partition information, motherboard/chipset info, kernel revisions tried, and /boot/grub/menu.lst would help...I'm just poking my stick in the dark here.  Help a brother out...

\\//_

---

### Post by ricardo06 on 2005-06-25
There is a similar problem that is solved in this thread:

[http://www.ubuntuforums.org/showthread.php?t=43065&highlight=2.6.12](http://www.ubuntuforums.org/showthread.php?t=43065&highlight=2.6.12)

cheers

Richard

---

### Post by skoal on 2005-06-25
[QUOTE=ricardo06]There is a similar problem that is solved in this thread:
[http://www.ubuntuforums.org/showthread.php?t=43065&highlight=2.6.12](http://www.ubuntuforums.org/showthread.php?t=43065&highlight=2.6.12)
[/QUOTE]
I think his issue his different than the VFS kernel panics in that thread (which come from compiling your kernel and not setting up the initrd properly, or leaving it out entirely).  I thought cobalt was using (and having difficulties with) a stock Ubuntu AMD64 kernel package (from a synaptic/apt-get update) in our repos.  Maybe I misunderstood him.  Anyways, my guess is that no "sdx" (SATA) devices are being found in his case, but I may be wrong...

\\//_

---

