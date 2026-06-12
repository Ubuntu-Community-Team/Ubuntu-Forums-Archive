---
title: "New User Set"
date: 2006-02-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by rosingjh on 2006-02-28
Hey, I am a new linux user.  I recently installed ubuntu on my computer.  I partioned one drive to share windows and ubuntu.  However, my computer also consist of another hard drive full of data.  IS there a way I can acess the data on the hard drive using both ubuntu and windows?  Is there any tips or ideas you have for me?  Learned about it in my MIS class.  Anyway..Thanks

---

### Post by Sutekh on 2006-02-28
[QUOTE=rosingjh]Hey, I am a new linux user.  I recently installed ubuntu on my computer.  I partioned one drive to share windows and ubuntu.  However, my computer also consist of another hard drive full of data.  IS there a way I can acess the data on the hard drive using both ubuntu and windows?  Is there any tips or ideas you have for me?  Learned about it in my MIS class.  Anyway..Thanks[/QUOTE]
Do you know what filesystem is the hard drive (with the data) formatted with?  NTFS or FAT?  If the drive is NTFS you will only be able to read the data, not modify it.  If the drive is FAT32 then you can have full access to the data on the drive.

Have a read of this link.  It will show you how to mount a NTFS and FAT partition in Ubuntu, so that you can access your data.  

[http://www.psychocats.net/linux/mountwindows.php]("http://www.psychocats.net/linux/mountwindows.php")

If you have any questions, fire away.

---

### Post by rosingjh on 2006-02-28
I still don't understand where you type the actual code?  I am not completly new to computer programming but there seems to be no place to do it.

---

### Post by tyr1973 on 2006-02-28
Hi!

You have to modify your /etc/fstab
In order to see what your other harddrive is called use System > Administration > Disks Manager.  The drive is probably called hdb?.  

cheers

---

### Post by Sutekh on 2006-02-28
[QUOTE=rosingjh]I still don't understand where you type the actual code?  I am not completly new to computer programming but there seems to be no place to do it.[/QUOTE]
Sorry about that

You need to open a **Terminal** window.  It should be found in the **Applications -> Accessories** menu.  Alternatively you can press **Alt**+**F2** on your keyboard and type **gnome-terminal** to open the same.

Once you open the terminal, you can enter the commands as you need.

Are you okay with the commands given in the link?



To start you need to determine the location of your partitions using
```
sudo fdisk -l
```
You can post the output of this command here if you want to make sure that you are choosing the right device.

Once you know the name of the shared drive (/dev/hdb1, /dev/sda1, I can't say for sure), you can edit your **/etc/fstab**.  fstab is a configuration file that contains information regarding your partitions and where they should be mounted.

You should create a backup of the fstab before editing it
```
sudo cp /etc/fstab /etc/fstab_backup
```
Then you can edit it using **gedit, nano**, whatever you wish
```
sudo gedit /etc/fstab
```

Once you have opened the fstab then you need to add the line to mount the shared drive.  From what I gather you will have two options.

**1 - The drive is formatted NTFS**, you should add a line similar to this one
```
[COLOR="Blue"]/dev/hdb1[/COLOR]    [COLOR="Red"]/media/windows[/COLOR]   [COLOR="Green"]ntfs[/COLOR]   [COLOR="DarkOrchid"]nls=utf8,umask=0222[/COLOR]   0   0
```
 - [COLOR="Blue"]/dev/hdb1[/COLOR] - is the location of the shared drive, you will have to edit this as apropriate

 - [COLOR="Red"]/media/windows[/COLOR] - this is the folder where the drive will be *mounted*.  If this folder doesn't exist you will need to create it yourself ```
sudo mkdir [COLOR="Red"]/media/windows[/COLOR]
```
**Note** you don't have to use [COLOR="Red"]/media/windows[/COLOR], in my system I use [COLOR="Red"]/mnt/winxp[/COLOR]; its up to you

 - [COLOR="Green"]ntfs[/COLOR] - this specifies the filesystem as ntfs

 - [COLOR="DarkOrchid"]nls=utf8,umask=0222[/COLOR] - these options set the character encoding to utf8 (for special chars) and sets the **umask**.  The umask is important as it restricts the access to the drive.  I can explain this more, but for now just know that [COLOR="DarkOrchid"]umask=0222[/COLOR] only allows read and execute access to the partition NOT write



**2 - The drive is formatted FAT32**, you should add a line similar to this one
```
[COLOR="Blue"]/dev/hdb1[/COLOR]    [COLOR="Red"]/media/windows[/COLOR]   [COLOR="Green"]vfat[/COLOR]   [COLOR="DarkOrchid"]iocharset=utf8,umask=0000[/COLOR]   0   0
```
 - [COLOR="Blue"]/dev/hdb1[/COLOR] - is the location of the shared drive, you will have to edit this as apropriate

 - [COLOR="Red"]/media/windows[/COLOR] - this is the folder where the drive will be *mounted*.  If this folder doesn't exist you will need to create it yourself ```
sudo mkdir [COLOR="Red"]/media/windows[/COLOR]
```
**Note** you don't have to use [COLOR="Red"]/media/windows[/COLOR], in my system I use [COLOR="Red"]/mnt/os-shared[/COLOR], its up to you

 - [COLOR="Green"]vfat[/COLOR] - this specifies the filesystem as fat

 - [COLOR="DarkOrchid"]iocharset=utf8,umask=0222[/COLOR] - these options set the character encoding to utf8 (for special chars) and sets the **umask**.  [COLOR="DarkOrchid"]umask=0000[/COLOR] allows read, write and execute access to the partition.


Once you've modified the /etc/fstab, you can save it and issue the command```
sudo mount -a
```This re-mounts the partitions, without you having to restart your computer.

---

### Post by rosingjh on 2006-02-28
I did what you said...and I get:

mount: wrong type, bad option, bad superblock on /dev/hdb1,
          missing codepage or other error
           In some cases useful info is found in syslog - try
           dmesg | tail or so

what did I do wrong?

this is what my gedit says:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdb1       /media/windows  ntfs    nls=utf8,unmask=0222 0    0  (This is the one in question)
  
Is there any difference in where the 0's land?

---

### Post by Sutekh on 2006-02-28
Youre gonna have enlighten me on the commands you used

Paste the output of ```
sudo fdisk -l
```
and paste the command you used that gave you the error

---

### Post by rosingjh on 2006-02-28
Okay..
sudo fdisk -l is
Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9119    73248336    7  HPFS/NTFS
/dev/hda2            9120       14150    40411507+  83  Linux
/dev/hda3           14151       14593     3558397+   5  Extended
/dev/hda5           14368       14593     1815313+  82  Linux swap / Solaris
/dev/hda6           14151       14367     1742989+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        5099    40957686    7  HPFS/NTFS
/dev/hdb2            5100       19457   115330635    7  HPFS/NTFS

Disk /dev/sda: 4095 MB, 4095737856 bytes
255 heads, 63 sectors/track, 497 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1           5       40131    0  Empty
/dev/sda2   *           6         497     3951990    b  W95 FAT32

(/dev/hdb1 and hdb2 are the hard drives I want mounted)

To get that error i typed:
sudo mount -a

Does this help?  Thank you for helping me..I like open source so far, espically if I can get this to work.

---

### Post by Sutekh on 2006-02-28
[QUOTE=rosingjh]
/dev/hdb1       /media/windows  ntfs    nls=utf8,u**n**mask=0222 0    0  
  
Is there any difference in where the 0's land?[/QUOTE]
No its not the 0's

People usually put important lines in CODE boxes so it makes it easier for people to copy and paste commands, rather than type them out and become prone to typos.  All that happened is that you used u**n**mask instead of umask, otherwise you should be set.

---

