---
title: "GRUB loading error 17"
date: 2009-07-11
forum: x86 64-bit Users
---

### Post by caldin on 2009-07-11
hey guys, im brand spankin' new to Ubuntu.  never used anything but windows before.  i recently reformatted my hard drive, having only Ubuntu on my desktop now.  it was working just fine, but now it says

"GRUB loading.........Error 17".

no clue why, any ideas?

---

### Post by merlinus on 2009-07-11
Open a terminal (Applications/Accessories) enter these commands and post results:

```
sudo fdisk -l
cat /boot/grub/menu.lst
```Also, did you move, resize, or format any of your partitions?

---

### Post by caldin on 2009-07-11
i didn't do anything with the hard drives at all.  i just added a wireless network adaptor so i wouldn't have to string a network cable through half the house.

how do i open a terminal to input those commands when it won't load the OS at all?

---

### Post by merlinus on 2009-07-11
Can you boot from the live cd?

---

### Post by caldin on 2009-07-11
i can start Ubuntu from the disc, the option where it says try Ubuntu without installing it to hard drive

---

### Post by merlinus on 2009-07-11
When the live cd is running, open a terminal and post results of

```
sudo fdisk -l
```

---

### Post by caldin on 2009-07-11
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9ba99ba9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60800   488375968+   7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0ff27d9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9327    74919096   83  Linux
/dev/sdb2            9328        9729     3229065    5  Extended
/dev/sdb5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x087e8aff

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121275   974141406    7  HPFS/NTFS
/dev/sdc2          121276      121601     2618595    5  Extended
/dev/sdc5          121276      121579     2441848+  83  Linux
/dev/sdc6          121580      121601      176683+  82  Linux swap / Solaris





the 80GB is my main drive i installed Ubunto on.  the 1TB drive is an external drive.

---

### Post by merlinus on 2009-07-11
Try this in the terminal whilst booted from the live cd:

```
sudo grub
root (hd1,0)
setup (hd0)
quit
```and restart.

Also, is sda (the one with windows) the first hdd in bios boot order?

---

### Post by caldin on 2009-07-11
the sda one shouldn't be first one in boot order, but i can double check that.

---

### Post by merlinus on 2009-07-11
If it is not, then the grub commands I gave will be incorrect.

---

### Post by caldin on 2009-07-11
ya, my 80GB HDD with Ubuntu on it is the first in HDD boot priority.  but the commands still aren't working for me that you gave me.

---

### Post by merlinus on 2009-07-11
If your linux hdd is booting first, then this may work:

```
sudo grub
root (hd0,0)
setup (hd0)
quit
```

---

### Post by caldin on 2009-07-12
i've tried both hd1 and hd0, and it says unrecognized command when i type setup (hd0, 0)

---

### Post by merlinus on 2009-07-12
should be:

setup (hd0)

also, no spaces if you are using

root (hd0,0)

---

### Post by caldin on 2009-07-12
hmmmmmmmmmmm, changed to what you said, and now its saying Error 12: Invalid device requested

---

### Post by merlinus on 2009-07-12
At this point, try supergrub:

[http://supergrubdisk.org](http://supergrubdisk.org)

---

