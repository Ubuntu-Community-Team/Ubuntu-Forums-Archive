---
title: "[SOLVED] Cant see windows files anymore"
date: 2007-11-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by Luis Macias on 2007-11-03
Hi, i have around 1 week with Ubuntu 7.10, and at first i could acces my windows files, but suddenly that disk disappeared, u can still see Dell utility partition, but not vista. Hope somebody can help me fix this. Thanks

---

### Post by Jose Catre-Vandis on 2007-11-03
Please advise on your hardware configuration - number of hard disks/partitions etc, how and in what order Vista and Ubuntu installed and output the following back here:
```
sudo fdisk -l
```
```
df -Th
```
```
sudo nano /etc/fstab
```

---

### Post by Luis Macias on 2007-11-04
Thanks for the reponse, here is the info:

Vista came installed in my laptop, and i installed ubuntu...

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x98000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           8       64228+  de  Dell Utility
/dev/sda2               9        1314    10485760    7  HPFS/NTFS
/dev/sda3   *        1314       12013    85937500    7  HPFS/NTFS
/dev/sda4           12014       15672    29390917+   5  Extended
/dev/sda5           12014       15538    28314531   83  Linux
/dev/sda6           15539       15672     1076323+  82  Linux swap / Solaris

--

Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda5     ext3     27G  3.1G   23G  13% /
varrun       tmpfs    944M   88K  944M   1% /var/run
varlock      tmpfs    944M     0  944M   0% /var/lock
udev         tmpfs    944M  112K  944M   1% /dev
devshm       tmpfs    944M   24K  944M   1% /dev/shm
lrm          tmpfs    944M   38M  907M   4% /lib/modules/2.6.22-14-generic/volatile
/dev/sda1     vfat     63M  7.0M   56M  12% /media/sda1

--

  GNU nano 2.0.6                                                        File: /etc/fstab                                                                                                                       

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=06f8b146-6ca4-494a-b91c-810dae12ac4f /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=07D7-0815  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=8286AA0086A9F4B7 /media/sda2     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
UUID=D226AD5026AD35FF /media/sda3     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda6
UUID=20736f2d-dd08-48d8-b6b7-e24180df5f95 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

---

### Post by Luis Macias on 2007-11-04
Hi, i found the problem, i just had to go to vista and safely remove hardware. Thanks for your help anyway. A question, how can i mark this post as solved?

Thanks

---

### Post by discmaster on 2007-11-04
> A question, how can i mark this post as solved?Under Thread Tools, top right area of page. :)

---

### Post by Ares2 on 2007-12-18
I actually have the same problem but it seems like I cant get to boot windows anymore. It actually load up windows, then when it's done loading, I see the blue wallpaper and I cant get to log in or do anything?

I dont know if its ubuntu related, my problem is in windows but I still cant see my partition in ubuntu either. If it's off topic of whatever I'll remove the post but did somebody had this problem?

BTW my results are about the same as the guy mentioned above, I don't see my sda1 in neither my fstab or in df -th

EDIT: When I try to mount my disk this is the message that I get:

$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 /mnt/sda1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 /mnt/sda1 ntfs-3g defaults,force 0 0

I actually started looking for an answer on the internet, all I found was that, when ubuntu did the Disk Check (after 31 boot in my case) it seems that it didnt completed successfully thus, corrupting in some kind of way my ntfs drive ?!!?!

I read somewhere that the way to fix this was to boot in windows and then shutdown the pc so Windows can unboot the ntfs correctly. Then, my problem is that I cant seem to boot windows anymore, does anybody have an idea of what is going on?

---

### Post by Ares2 on 2007-12-18
I think I've found the reason why Windows doesnt boot anymore. The fact that it wasn't able to correctly unmount my hard drive which is the one that windows boot on, it might not be able to boot anymore. I think I'll try to run windows on another HD and see if I can properly unmount my main one. That might fix the problem.

Oh by the way, does somebody know why the disk check did that? Cause I dont want this problem to happen every 31 boot or something..

---

