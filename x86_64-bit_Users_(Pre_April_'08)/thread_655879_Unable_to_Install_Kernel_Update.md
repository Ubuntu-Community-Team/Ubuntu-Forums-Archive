---
title: "Unable to Install Kernel Update"
date: 2008-01-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by ProfDecoy on 2008-01-01
I've been trying to find a solution to this elsewhere and haven't been very successful yet at finding an answer, maybe I've been searching for the wrong thing.

In any rate, I've been trying to install the recent security update for the 2.6 kernel.  When Synaptic tries to unpack it, it comes back and says there's no space left on the device.  I've checked my /var partition and I have plenty of free space.  I've also tried deleting the package from the /var/cache/apt directory to force a redownload, but I still get the same error.

Here's the terminal log from Synaptic:

```

Log started: 2008-01-01  22:28:12
(Reading database ... 143058 files and directories currently installed.)
Preparing to replace linux-image-2.6.22-14-generic 2.6.22-14.46 (using .../linux-image-2.6.22-14-generic_2.6.22-14.47_amd64.deb) ...
Done.
Unpacking replacement linux-image-2.6.22-14-generic ...
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.22-14-generic_2.6.22-14.47_amd64.deb (--unpack):
 failed in buffer_write(fd) (10, ret=-1): backend dpkg-deb during `./lib/modules/2.6.22-14-generic/kernel/net/ipv4/ah4.ko': No space left on device
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.22-14-generic
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done

Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.22-14-generic_2.6.22-14.47_amd64.deb
Log ended: 2008-01-01  22:28:20

```

There's probably something I'm failing to see that would explain what's going on.

Thanks for any help.

---

### Post by dcstar on 2008-01-02
> **ProfDecoy said:**
> I've been trying to find a solution to this elsewhere and haven't been very successful yet at finding an answer, maybe I've been searching for the wrong thing.

In any rate, I've been trying to install the recent security update for the 2.6 kernel.  When Synaptic tries to unpack it, it comes back and says there's no space left on the device.  I've checked my /var partition and I have plenty of free space.  I've also tried deleting the package from the /var/cache/apt directory to force a redownload, but I still get the same error.

Here's the terminal log from Synaptic:

```

Log started: 2008-01-01  22:28:12
(Reading database ... 143058 files and directories currently installed.)
Preparing to replace linux-image-2.6.22-14-generic 2.6.22-14.46 (using .../linux-image-2.6.22-14-generic_2.6.22-14.47_amd64.deb) ...
Done.
Unpacking replacement linux-image-2.6.22-14-generic ...
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.22-14-generic_2.6.22-14.47_amd64.deb (--unpack):
 failed in buffer_write(fd) (10, ret=-1): backend dpkg-deb during `./lib/modules/2.6.22-14-generic/kernel/net/ipv4/ah4.ko': No space left on device
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.22-14-generic
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done

Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.22-14-generic_2.6.22-14.47_amd64.deb
Log ended: 2008-01-01  22:28:20

```

There's probably something I'm failing to see that would explain what's going on.

Thanks for any help.

It is reading from /var, not necessarliy writing to it.

Post the output of **fdisk -l**

---

### Post by ProfDecoy on 2008-01-02
Happen to be running an LVM encrypted disk, but here's the the output for the partition listing. 

```

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003cded

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          31      248976   83  Linux
/dev/sda2              32       30401   243947025    5  Extended
/dev/sda5              32       30401   243946993+  83  Linux

```

Partition listing from lvm:

```

lvm> lvs
  LV     VG        Attr   LSize   Origin Snap%  Move Log Copy%
  home   laptop -wi-ao 217.49G
  root   laptop -wi-ao 292.00M
  swap_1 laptop -wi-ao   5.90G
  tmp    laptop -wi-ao 392.00M
  usr    laptop -wi-ao   5.72G
  var    laptop -wi-ao   2.86G

```

---

