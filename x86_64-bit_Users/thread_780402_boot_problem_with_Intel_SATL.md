---
title: "boot problem with Intel SATL"
date: 2008-05-03
forum: x86 64-bit Users
---

### Post by jasonnerothin on 2008-05-03
I'm having a problem getting a clean boot of my new Hardy installation on a Intel DQ35JOE board. 

My OS drive is a (partitioned) ATA drive that - I think - sits beneath some firmware referred to as SATL (SCSI to ATA Translation Layer). On boot, I get some write beyond end of disk errors

```
[   89.013940] attempt to access beyond end of device
[   89.013942] sda: rw=0, want=2147618791, limit=976773168
```

followed by a prompt asking for device path or "Enter to boot". I can hit enter and get Hardy up and running. Once I'm booted, fdisk reports the following:

```
jason@cliff:/etc/modprobe.d$ sudo fdisk -l /dev/sde

Disk /dev/sde: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000da880

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1       12749   102400000    7  HPFS/NTFS
/dev/sde2           12750       60801   385977690    5  Extended
/dev/sde5           12750       58851   370314283+  83  Linux
/dev/sde6           58852       60801    15663343+  82  Linux swap / Solaris
```

which is not what fstab is looking for (by UUID):

```
jason@cliff:/etc/modprobe.d$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=ae182696-f369-4d5a-9867-597715809889 /               ext3    relatime,errors=remount-ro 0       1

```

grub's menu.list makes the following UUID reference:

```

title           Ubuntu 8.04, kernel 2.6.24-16-server
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.24-16-server root=UUID=ae182696-f369-4d5a-9867-597715809889 ro quiet splash
initrd          /boot/initrd.img-2.6.24-16-server
quiet

```

It seems like the UUID reference is causing the mixup here (if my hypothesis is correct that SATL is interfering). But what do I do about it?

---

