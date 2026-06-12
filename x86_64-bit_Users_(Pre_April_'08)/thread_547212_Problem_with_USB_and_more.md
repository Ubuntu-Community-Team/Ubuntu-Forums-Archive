---
title: "Problem with USB and more"
date: 2007-09-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by a.drewmc on 2007-09-09
Okay, so I just started using ubuntu (Feisty 7.04) and love it, however when I plug in any USB device it never mounts, apart from it physically being there I cannot tell it is connected to the laptop.  I have tried it on these devices

SanDisk Sansa Connect
OLD SanDisk 128MB
SanDisk 1 GB micro SD card with SD adapter.

It is vital that I get this working otherwise I will be forced to switch back to Windows.

All these devices have been tested on a windows XP machine

Here are some specs about my computer
Intel Core 2 Duo 
1GB RAM
80GB hard drive
[Compal HEL-80]("http://www.xoticpc.com/article_info.php/articles_id/20")

PLEASE I LOVE UBUNTU BUT I NEED USB TO WORK.

---

### Post by ddrichardson on 2007-09-09
Check by opening the terminal and doing fdisk -l after the drive is inserted to see if the drive is being picked up.

You may be able to mount it manually until you find out what's wrong.

---

### Post by a.drewmc on 2007-09-10
no bones:

andrew@andrew-laptop:~$ fdisk -l
andrew@andrew-laptop:~$ 

PLEASE HELP ME!

Would a re-install of ubuntu help?

---

### Post by ddrichardson on 2007-09-10
sorry - that needs doing as sudo:```
sudo fdisk -l
```

---

### Post by a.drewmc on 2007-09-10
andrew@andrew-laptop:~$ sudo fdisk -l
Password:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9355    75144006   83  Linux
/dev/sda2            9356        9729     3004155    5  Extended
/dev/sda5            9356        9729     3004123+  82  Linux swap / Solaris
andrew@andrew-laptop:~$

Cant find a the drive.

---

### Post by ddrichardson on 2007-09-11
First, check for any USB or Plug & Play options in BIOS.

Second check the output of dmesg when the device is plugged in and report any errors.

---

### Post by Jouke74 on 2007-09-11
For the beginner: "dmesg" is also a command. Sudo means doing things under the "administrator account", named "root".... If none of the devices are working I guess you have a problem with your USB port, not the things that go into that. Indeed check the BIOs for USB and switch legacy on / off, thus the other option on which it is now.

---

