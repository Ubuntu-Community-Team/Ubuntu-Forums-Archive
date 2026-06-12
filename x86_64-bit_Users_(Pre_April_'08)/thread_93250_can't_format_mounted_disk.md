---
title: "can't format mounted disk"
date: 2005-11-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by stripeypants on 2005-11-21
Hi,

I installed 5.10 on G3 iBook--works fine.  

I have a Mac OS X formatted external drive that auto-mounts as a read-only filesystem when starting Ubuntu.  However, when I go to System Admin > Disks, because I want to format it, it doesn't show up.  Only the laptop's internal HD and CD-ROM are there.

How can I format the external disk?

TIA for any hints.

---

### Post by er-ku on 2005-11-22
[QUOTE=stripeypants]Hi,

I installed 5.10 on G3 iBook--works fine.  

I have a Mac OS X formatted external drive that auto-mounts as a read-only filesystem when starting Ubuntu.  However, when I go to System Admin > Disks, because I want to format it, it doesn't show up.  Only the laptop's internal HD and CD-ROM are there.

How can I format the external disk?

TIA for any hints.[/QUOTE]

You must unmount the drives before formatting them. Go to places > computer > Right click (or press F12) on your disk, and unmount it. Then proceed to the Disk admin.

---

### Post by oskude on 2005-11-22
you CANT format mounted partitions !
and you dont format a disk, you format a partition...

i never used "System Admin > Disks", so dunno why its not listed there...

but you can format it manually through console
first check where its auto mounted with command```
mount
```
then umount it with```
sudo umount <mount-point or device>
```
and then format it with```
sudo mkfs.<your fs type> <device>
```

if this dont sound familiar, post your output of "mount" (when the external disk is mounted) and the format you want and ill help you...

---

### Post by ssam on 2005-11-22
install gparted, thats the easiest disk formater to use

---

### Post by stripeypants on 2005-11-23
Thank you for your suggestions so far.

So I unmounted, ran the utility, and voila, it shows up.  However, the utility allows you to format partitions, not disks, as stated above.  

My desktop is KDE and it wasn't immediately clear how involved it would be to switch to gnome, so I tried *parted*.  When I do *check 2* it tells me "fs not cleanly mounted.  You should e2fsk.  No implementation: this ext2 fs has a strange layout.  Can't resize (yet)."

*e2fsk * seems to be a diagnostic utility, but didn't get me any close to wiping the disk clean (what is the term for this?).

---

### Post by ssam on 2005-11-23
gparted will run in kde but apt/synaptic may need to install a bunch of other bits (gtk and other libraries). you could try qtparted which is a native kde version.

---

### Post by louisgag on 2006-07-14
I was unable to format using the disk manager utility, but gparted did the trick!  thanks ssam

---

