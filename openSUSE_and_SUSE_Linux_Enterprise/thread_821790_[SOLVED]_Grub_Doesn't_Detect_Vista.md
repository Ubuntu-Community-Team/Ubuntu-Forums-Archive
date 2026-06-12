---
title: "[SOLVED] Grub Doesn't Detect Vista"
date: 2008-06-07
forum: openSUSE and SUSE Linux Enterprise
---

### Post by Vince4Amy on 2008-06-07
Is there any way I can correct this, I don't have much experience with Grub. When I boot up I get the Option to boot OpenSUSE (Fine). But I have windows & windows 1 on my menu, neither of which will boot Vista. 

How do I correct these?

---

### Post by meierfra. on 2008-06-07
Post the output of 

```
sudo fdisk -l
```

```
cat /boot/grub/menu.lst
```

(both "l" are lowercase "L")

---

### Post by meierfra. on 2008-06-07
Also:

Are you getting any error messages?

Did you resize Vista? If yes, what partitioning tool did you use?

Were you able to boot  Vista and XP  before you install Suse?

---

### Post by Vince4Amy on 2008-06-07
Sorry for not posting this info earlier. I'll post it a bit later. Also I didn't resize Vista, I've installed it on a Separate HDD.

---

### Post by Vince4Amy on 2008-06-07
Fdisk Output 

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x38b51c70

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19458   156288000    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x11337014

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19458   156288000    7  HPFS/NTFS

Disk /dev/sdc: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1603e3fa

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         262     2104483+  82  Linux swap / Solaris
/dev/sdc2             263       14946   117949230   83  Linux
```

Windows Vista is stored on /dev/sda

Output of the Grub Menu

```
# Modified by YaST2. Last modification on Sat Jun  7 23:18:34 UTC 2008
default 0
timeout 8
gfxmenu (hd2,1)/boot/message

###Don't change this comment - YaST2 identifier: Original name: linux###
title openSUSE 10.3
    root (hd2,1)
    kernel /boot/vmlinuz-2.6.22.5-31-default root=/dev/disk/by-id/scsi-SATA_Maxtor_6Y120L0_Y35QBR0E-part2 vga=0x31a    resume=/dev/sdc1 splash=silent showopts
    initrd /boot/initrd-2.6.22.5-31-default

###Don't change this comment - YaST2 identifier: Original name: windows 1###
title windows 1
    rootnoverify (hd2,1)
    chainloader (hd0,0)+1

###Don't change this comment - YaST2 identifier: Original name: windows 2###
title windows 2
    rootnoverify (hd2,1)
    chainloader (hd1,0)+1

###Don't change this comment - YaST2 identifier: Original name: failsafe###
title Failsafe -- openSUSE 10.3
    root (hd2,1)
    kernel /boot/vmlinuz-2.6.22.5-31-default root=/dev/disk/by-id/scsi-SATA_Maxtor_6Y120L0_Y35QBR0E-part2 vga=normal showopts ide=nodma apm=off acpi=off noresume nosmp noapic maxcpus=0 edd=off 3
    initrd /boot/initrd-2.6.22.5-31-default
```

---

### Post by meierfra. on 2008-06-07
fdisk  and menu.lst look fine. So I'm not sure what the problem is.

Did you install grub to the MBR of the vista drive?

I suggest to run "fixboot" from the Vista Recovery console:
[URL="http://support.microsoft.com/kb/927392/en-us"]
http://support.microsoft.com/kb/927392/en-us[/URL]


In case this overwrites grub, you can reinstall Grub from the Suse LiveCD 


```

su
grub

```

and at the grub prompt:


```
root (hd2,1)
setup (hd0)
quit

```

(if that did not work try "setup (hd1)" in place of "setup (hd0)")



If "fixboot" did not work, you need to tell me exactly what happens then you choose "Windows 1" and "Windows 2" at the Grub menu.

---

### Post by 67GTA on 2008-06-07
I had trouble with 10.3 and Vista. Suse's grub would never boot it. I finally used the Yast partitioner to make the Vista partition active, and got it to boot. For some reason Vista thinks it has to be the active partition to boot. I'm not sure what error you are getting, but maybe this will help.

---

### Post by meierfra. on 2008-06-07
Both of the windows partition are already active.

---

### Post by Vince4Amy on 2008-06-08
Thanks, I figured it out myself shortly after posting the above information and I changed this line:

```
###Don't change this comment - YaST2 identifier: Original name: windows 1###
title windows 1
    rootnoverify (hd2,1)
    chainloader (hd0,0)+1
```

to:

```
###Don't change this comment - YaST2 identifier: Original name: windows 1###
title Microsoft Windows Vista
    rootnoverify (hd0,1)
    chainloader (hd0,0)+1
```

This works okay, but correct me if I'm wrong.

---

### Post by meierfra. on 2008-06-08
>    rootnoverify (hd0,1)
    chainloader (hd0,0)+1

I know that Suse always uses the "rootnoverify" line and I have  never figured out why.  As far as I know it should not make any difference what numbers you use (as long  the partition exits).

 Just to confirm:

You changed   "rootnoverify (hd2,1)" to "rootnoverify (hd0,1)" and you didn't  do anything else, and now you are able to boot into Windows?


This really makes no sense. According to "fdisk" (hd0,1) does not even exit

---

### Post by Vince4Amy on 2008-06-08
Yes this is what I did then it worked fine.

---

### Post by meierfra. on 2008-06-08
O.K,  I just realized that "rootnoverify (hd0,1)", even though "(hd0,1)" does not exist, will not produce an error message.  

Just to help me understand what is going on, would you delete  "rootnoverify (hd0,1)" from menu.lst. I'm 99% sure that you still will be able to boot into Windows.

---

