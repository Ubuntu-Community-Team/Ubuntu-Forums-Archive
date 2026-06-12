---
title: "Easiest way to dual-boot windows xp x64 and Ubuntu 64-bit"
date: 2006-06-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by lonrot on 2006-06-24
1) Have windows Installed first.

    2) Use any Partion Maker program, I used Acronis Disk Director Suite 10.0. Create a new partition. Recommended 20GB. After creating the partition reboot, When the partition is ready use Acronis again to delete that partition (you must be in Manual Mode). If everything worked fine you can now see 20GB of Unallocated space.

    3) Reboot and launch your Ubuntu Live CD. Chose Install and when asked check the use Free Space, this will take your 20GB unallocated space and make two partitions, the swap-linux and the main ubuntu.

    4) When the installation ends reboot, with the CD out of the tray you will see that GRUB will replace the main boot (GoodBye Windows for now) and will launch Ubuntu. When Logged-in type ALT+F2, in the blank space type ```
gksudo gedit /boot/grub/menu.lst
```
    Type your admin password.
    In the end of the file search for:
    ```
### END DEBIAN AUTOMAGIC KERNELS LIST
```
    Replace with:
    ```
### END DEBIAN AUTOMAGIC KERNELS LIST

    # This is a divider, added to separate the menu items below from the Debian
    # ones.
    title        Other operating systems:
    root


    # This entry automatically added by the Debian installer for a non-linux OS
    # on /dev/hda1
    title        Windows XP Professional x64 Edition
    root        (hd0,0)
    savedefault
    makeactive
    chainloader    +1
    
```
    Save and Exit.

    5)Reboot your system, before GRUB automatically launches Ubuntu Press ESC and Choose WIndows XP Professional x64.

    NOTES:
    If using Acronis Do not install OS Selector (It will screw up GRUB)
    There is a way to set Windows as the default boot but I'm not aware of how.
    And there is a way to make the Grub OS Selector appear before auto-running any OS. So I'll post the how-to eventually.

    Good Luck

---

### Post by mgsfan on 2006-06-24
mm...I have'nt had to go thru all that hassle..I just installed x64 first and ubuntu 64  second and worked off the bat...

---

### Post by mkw87 on 2006-06-26
Same for me, just installed x64 on the first partition on the drive, then installed Dapper on the third partition (second is a 2nd windows partition).

---

### Post by christoffer on 2006-06-27
Same for me.
I partitioned the drive within the Windows setup to the sizes I wanted. About 10Gb of Windows and then let Ubuntu take rest of the disk. Installed. Then booted on the Ubuntu CD, marked the "use largest free partition" option and let it run it's course. After the reboot I got to a grub-menu that already read Ubuntu, Ubuntu rescue mode, Ubuntu mem test and Windows XP.

No hassle, no editing, just installed.

---

### Post by lonrot on 2006-07-02
Good for you guys, but I had a serious time trying to boot XP without any luck, I searched like a freak until I found this solution: editing the grub.

So if anyone has the same problem as I had, this guide will help a lot. I'm sure about it.

---

