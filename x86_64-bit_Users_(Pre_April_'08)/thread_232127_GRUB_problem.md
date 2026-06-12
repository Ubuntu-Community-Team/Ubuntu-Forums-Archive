---
title: "GRUB problem"
date: 2006-08-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by vronin on 2006-08-08
My english is quite bad, hope you understand.

My computer: CPU: AMD64 3000+, VIDEO: Ati Radeon x700 pro,  MB: MSI  nforce4, HDD: SATA 200GB and PATA 20GB.

On the 200gb hd i`ve made 3 ntfs partitions and installed windows. On the PATA hard disk i`ve made also 3 partitions 1. ext3 (12GB) 2.Swap (2GB) 3. OSshare (FAT32 , 5GB).

I`ve installed ubuntu installed the GRUB on the ext3 partition, booted with system rescue cd and made the following:
- mkdir /mnt/osshare
- mount -t msdos /dev/hdc6 /mnt/osshare 
- dd if=/dev/hdc1 of=/mnt/osshare/ubuntu.bin bs=512 count=1.

Rebooted in windows copied the ubuntu.bin from fat partiton to c:\ and added the following text to the boot.ini: C:\ubuntu.bin="Ubuntu Linux". Saved the file and rebooted. But when i want to boot into ubuntu i get a black screen only showing GRUB in the top left corner.

I`ve also tried the following:
 grub
 find /boot/grub/stage1
 root (hd0,0)
 setup (hd0)

but with no luck. What else should i do ? I don`t want to install ubuntu on the 200gb hard drive.

---

