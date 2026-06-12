---
title: "disks of RAID 1 visible to ubuntu"
date: 2008-10-26
forum: x86 64-bit Users
---

### Post by vikofle on 2008-10-26
Hi,

I setup a Hardware-RAID 1 on my 64Bit AMD X2 Ubuntu recently using the onboard RAID controller. While everything went smooth, I at one point realised that both of the disks in the RAIDArray is visible to the Gnome-Applet for mounting disks, but one of which cannot be mounted .

Logically, soon the disks were in asynchronous state.

Also, when using Gparted I can access both disks in the array - something I m sure I should nt be able to do if the RAID worked correctly. 

The BIOS-RAID Utility (ULi) tells me that the RAID is fine and setup correctly but as said the disks can be accessed directly from the OS

```
[09:15:32]root@maximus:~# ls /dev/disk/by-id/ -lah
insgesamt 0
drwxr-xr-x 2 root root 400 2008-10-26 09:04 .
drwxr-xr-x 5 root root 100 2008-10-26 08:57 ..
lrwxrwxrwx 1 root root   9 2008-10-26 08:57 ata-ExcelStor_Technology_J8160S_PVB300Q40B1N3C -> ../../sda
lrwxrwxrwx 1 root root  10 2008-10-26 08:57 ata-ExcelStor_Technology_J8160S_PVB300Q40B1N3C-part1 -> ../../sda1
lrwxrwxrwx 1 root root  10 2008-10-26 08:57 ata-ExcelStor_Technology_J8160S_PVB300Q40B1N3C-part2 -> ../../sda2
lrwxrwxrwx 1 root root  10 2008-10-26 08:57 ata-ExcelStor_Technology_J8160S_PVB300Q40B1N3C-part3 -> ../../sda3
lrwxrwxrwx 1 root root  10 2008-10-26 09:04 ata-ExcelStor_Technology_J8160S_PVB300Q40B1N3C-part4 -> ../../sda4
lrwxrwxrwx 1 root root   9 2008-10-26 08:57 ata-ST3500320AS_5QM35LR1 -> ../../sdc
lrwxrwxrwx 1 root root  10 2008-10-26 08:57 ata-ST3500320AS_5QM35LR1-part1 -> ../../sdc1
lrwxrwxrwx 1 root root   9 2008-10-26 08:57 ata-ST3500320AS_9QM6VPGX -> ../../sdb
lrwxrwxrwx 1 root root  10 2008-10-26 08:57 ata-ST3500320AS_9QM6VPGX-part1 -> ../../sdb1
lrwxrwxrwx 1 root root   9 2008-10-26 08:57 scsi-1ATA_ExcelStor_Technology_J8160S_PVB300Q40B1N3C -> ../../sda
lrwxrwxrwx 1 root root  10 2008-10-26 08:57 scsi-1ATA_ExcelStor_Technology_J8160S_PVB300Q40B1N3C-part1 -> ../../sda1
lrwxrwxrwx 1 root root  10 2008-10-26 08:57 scsi-1ATA_ExcelStor_Technology_J8160S_PVB300Q40B1N3C-part2 -> ../../sda2
lrwxrwxrwx 1 root root  10 2008-10-26 08:57 scsi-1ATA_ExcelStor_Technology_J8160S_PVB300Q40B1N3C-part3 -> ../../sda3
lrwxrwxrwx 1 root root  10 2008-10-26 09:04 scsi-1ATA_ExcelStor_Technology_J8160S_PVB300Q40B1N3C-part4 -> ../../sda4
lrwxrwxrwx 1 root root   9 2008-10-26 08:57 scsi-1ATA_ST3500320AS_5QM35LR1 -> ../../sdc
lrwxrwxrwx 1 root root  10 2008-10-26 08:57 scsi-1ATA_ST3500320AS_5QM35LR1-part1 -> ../../sdc1
lrwxrwxrwx 1 root root   9 2008-10-26 08:57 scsi-1ATA_ST3500320AS_9QM6VPGX -> ../../sdb
lrwxrwxrwx 1 root root  10 2008-10-26 08:57 scsi-1ATA_ST3500320AS_9QM6VPGX-part1 -> ../../sdb1
```
```

[09:17:34]root@maximus:~# mount -l
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro) []
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-21-generic/volatile type tmpfs (rw)
/dev/sdb1 on /home type ext3 (rw,relatime) []
/dev/sda2 on /opt type ext3 (rw,relatime) []
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/cvh/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=cvh)
```

Any Hint/Help/Advice how to solve this mysteria and get a working RAID 1 configuration is greatly appreciated

TIA

Vikofle/Chris

---

### Post by cariboo on 2008-10-26
I used this:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

To setup raid on my server with an onboard raid controller.

Jim

---

