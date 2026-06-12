---
title: "Root permission problem"
date: 2007-09-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by RevolutionnaireY on 2007-09-23
Ok here I have a good problem, I want to open my port for azureus, so I checked on azureus wiki, [http://www.azureuswiki.com/index.php/NAT_problem#Port_Forwarding_on_Linux.2C_specifically_Ubuntu](http://www.azureuswiki.com/index.php/NAT_problem#Port_Forwarding_on_Linux.2C_specifically_Ubuntu)

so I need to put a file in ect/... but I can't even if I connect in root it says that I dont have the permission and I can't change them cuz it's all gray. 

here is my sudo -fdisk

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        5099    40957686    7  HPFS/NTFS
/dev/hda2            5100        9729    37190475    5  Extended
/dev/hda5            5100        5239     1124518+  82  Linux swap / Solaris
/dev/hda6            5240        9729    36065893+  83  Linux

Disk /dev/hdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/hdb2           12749       38913   210170362+   f  W95 Ext'd (LBA)
/dev/hdb5           12749       25496   102398278+   7  HPFS/NTFS
/dev/hdb6           25497       38913   107772021   83  Linux


I am on 64bit thats why I posted here, if I am not in the right forum, please tell me I'am new to ubuntu and the forum. If my disks are not well partition please can you tell me how to make them right because I will reinstall everything soon since I'll change my pross and motherboard( still 64 bit)

---

### Post by Kilz on 2007-09-24
Connect as root? By default Ubuntu doesnt have a root login. It is not recommended that you use one. Use sudo in the terminal like to chown

```
sudo Chown -R accoutname:users/some/path/here
```

You can open up nautilus as an adminastrator , open terminal

```
gksudo nautilus
```

But be very careful what you do as you could fubar your install. You also dont need to reinstall if you are keeping a 64bit board and chip.

---

