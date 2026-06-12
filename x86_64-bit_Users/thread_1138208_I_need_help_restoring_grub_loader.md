---
title: "I need help restoring grub loader"
date: 2009-04-26
forum: x86 64-bit Users
---

### Post by gretarsson on 2009-04-26
I had ubuntu 8.10 and upgrade to 9.04 from terminal but when i restart my pc, it freeze after ubuntu loading bar run to end. it look like loading bar from 8.10 not this new one from 9.04 so I thing my pc is running wrong grub loader.   I am running my pc from live cd but I am not sure how to fix my grub loader from terminal in live cd, I already split up my hard disk and put in fresh os 9.04 into the new part but my grub loader is still same
here is some thing from terminal my main hard disk is 500gb /dev/sdc1
From terminal in live cd.

root@ubuntu:/home/ubuntu# fdisk -l 

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00062f79

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       37778   303451753+  83  Linux
/dev/sda2           37779       38913     9116887+   5  Extended
/dev/sda5           37779       38913     9116856   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9e43e6f2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001   83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8beb7ab2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       21264   170803048+  83  Linux
/dev/sdc2           21265       60801   317580952+   5  Extended
/dev/sdc5           59676       60801     9044563+  82  Linux swap / Solaris
/dev/sdc6           21265       58561   299588089+  83  Linux
/dev/sdc7           58562       59675     8948173+  82  Linux swap / Solaris

Partition table entries are not in disk order
----------------------------------------------------------
from fstab in old disk part 

proc            /proc           proc    defaults        0       0
UUID=3eeec21a-a713-4ad1-b530-d1ac785c32c2 /               ext3    relatime,errors=remount-ro 0       1
UUID=6dbed386-1cda-4598-a4be-2e5dad2f6ac3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb1    /media/disk   ext3    defaults     0        0
/dev/sda1    /media/disk-1   ext3    defaults     0        0

----------------------------------------------------------------
from fstab in new disk part 

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdc6 during installation
UUID=a9411b0e-2a90-4444-b357-89f828906e7f /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdc7 during installation
UUID=1ba55356-8e75-4ac1-9d53-5675ceeb36f0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by meierfra. on 2009-04-26
In order to get a clearer picture of your setup, I suggest to boot from the Ubuntu LiveCD and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post,  highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by gretarsson on 2009-04-27
> **meierfra. said:**
> In order to get a clearer picture of your setup, I suggest to boot from the Ubuntu LiveCD and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post,  highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

Thanks for reply and your help.  here are copy text from Results.txt
```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #3 in 
    partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Grub0.97 is installed in the MBR of /dev/sdc and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub is installed in the boot sector of sda1 and looks 
                       at sector 532234303 of the same hard drive for the 
                       stage2 file, but no stage2 files can be found at this 
                       location.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu jaunty (development 
                       branch)
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdc7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00062f79

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   606,903,569   606,903,507  83 Linux
/dev/sda2         606,903,570   625,137,344    18,233,775   5 Extended
/dev/sda5         606,903,633   625,137,344    18,233,712  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9e43e6f2

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   488,392,064   488,392,002  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8beb7ab2

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   341,606,159   341,606,097  83 Linux
/dev/sdc2         341,606,160   976,768,064   635,161,905   5 Extended
/dev/sdc5         958,678,938   976,768,064    18,089,127  82 Linux swap / Solaris
/dev/sdc6         341,606,286   940,782,464   599,176,179  83 Linux
/dev/sdc7         940,782,528   958,678,874    17,896,347  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="ca39f40c-428f-4932-9504-7f956fb2d7ac" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="503e2895-42ef-4615-bb4e-9d29081d53ae" TYPE="swap" 
/dev/sdb1: UUID="d6a55d52-66de-457e-9018-a07df8217992" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc1: UUID="3eeec21a-a713-4ad1-b530-d1ac785c32c2" TYPE="ext3" 
/dev/sdc5: UUID="6dbed386-1cda-4598-a4be-2e5dad2f6ac3" TYPE="swap" 
/dev/sdc6: UUID="a9411b0e-2a90-4444-b357-89f828906e7f" TYPE="ext3" 
/dev/sdc7: UUID="1ba55356-8e75-4ac1-9d53-5675ceeb36f0" TYPE="swap" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdc1 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sdc6 on /media/disk-1 type ext3 (rw,nosuid,nodev,uhelper=hal)


=========================== sdc1/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		4

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=3eeec21a-a713-4ad1-b530-d1ac785c32c2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=3eeec21a-a713-4ad1-b530-d1ac785c32c2

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-14-generic
uuid		3eeec21a-a713-4ad1-b530-d1ac785c32c2
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=3eeec21a-a713-4ad1-b530-d1ac785c32c2 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-14-generic
#quiet

title		Ubuntu 8.10, kernel 2.6.27-14-generic (recovery mode)
uuid		3eeec21a-a713-4ad1-b530-d1ac785c32c2
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=3eeec21a-a713-4ad1-b530-d1ac785c32c2 ro  single
initrd		/boot/initrd.img-2.6.27-14-generic

title		Ubuntu 8.10, memtest86+
uuid		3eeec21a-a713-4ad1-b530-d1ac785c32c2
kernel		/boot/memtest86+.bin
#quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sdc1/etc/fstab: ===============================

proc            /proc           proc    defaults        0       0
UUID=3eeec21a-a713-4ad1-b530-d1ac785c32c2 /               ext3    relatime,errors=remount-ro 0       1
UUID=6dbed386-1cda-4598-a4be-2e5dad2f6ac3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb1    /media/disk   ext3    defaults     0        0
/dev/sda1    /media/disk-1   ext3    defaults     0        0




=================== sdc1: Location of files loaded by Grub: ===================


 149.5GB: boot/grub/menu.lst
 110.9GB: boot/grub/stage2
 110.9GB: boot/initrd.img-2.6.27-14-generic
 110.9GB: boot/vmlinuz-2.6.27-14-generic
 110.9GB: initrd.img
 110.9GB: vmlinuz

=========================== sdc6/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
#Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=a9411b0e-2a90-4444-b357-89f828906e7f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=a9411b0e-2a90-4444-b357-89f828906e7f

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu jaunty (development branch), kernel 2.6.28-11-generic
uuid		a9411b0e-2a90-4444-b357-89f828906e7f
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=a9411b0e-2a90-4444-b357-89f828906e7f ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu jaunty (development branch), kernel 2.6.28-11-generic (recovery mode)
uuid		a9411b0e-2a90-4444-b357-89f828906e7f
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=a9411b0e-2a90-4444-b357-89f828906e7f ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu jaunty (development branch), memtest86+
uuid		a9411b0e-2a90-4444-b357-89f828906e7f
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
#title		Ubuntu 8.10, kernel 2.6.27-14-generic (on /dev/sdc1)
#root		(hd2,0)
#kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=3eeec21a-a713-4ad1-#b530-d1ac785c32c2 ro quiet splash 
#initrd		/boot/initrd.img-2.6.27-14-generic
#savedefault
#boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
#title		Ubuntu 8.10, kernel 2.6.27-14-generic (recovery mode) (on /#dev/sdc1)
#root		(hd2,0)
#kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=3eeec21a-a713-4ad1-#b530-d1ac785c32c2 ro single 
#initrd		/boot/initrd.img-2.6.27-14-generic
#savedefault
#boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc1.
#title		Ubuntu 8.10, memtest86+ (on /dev/sdc1)
#root		(hd2,0)
#kernel		/boot/memtest86+.bin  
#savedefault
#boot


=============================== sdc6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdc6 during installation
UUID=a9411b0e-2a90-4444-b357-89f828906e7f /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdc7 during installation
UUID=1ba55356-8e75-4ac1-9d53-5675ceeb36f0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdc6: Location of files loaded by Grub: ===================


 314.8GB: boot/grub/menu.lst
 314.7GB: boot/grub/stage2
 314.8GB: boot/initrd.img-2.6.28-11-generic
 314.7GB: boot/vmlinuz-2.6.28-11-generic
 314.8GB: initrd.img
 314.7GB: vmlinuz
```

---

### Post by zip_000 on 2009-04-27
Try this to restore GRUB:

In the Live CD, open a terminal.
Type:
sudo grub
- root (hd0,0)
- setup (hd0)
- quit
- exit 

This is from a guide to dual boot, but it's how I restored grub recently. Full guide here:
[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5)

---

### Post by gretarsson on 2009-04-27
> **zip_000 said:**
> Try this to restore GRUB:

In the Live CD, open a terminal.
Type:
sudo grub
- root (hd0,0)
- setup (hd0)
- quit
- exit 

This is from a guide to dual boot, but it's how I restored grub recently. Full guide here:
[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5)

sorry but I only have Linux in my pc and if I try this grub setup I got this

ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> root (hd0,0)
root (hd0,0)
grub> setup (hd0)
setup (hd0)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no

Error 15: File not found
grub> quit
quit
ubuntu@ubuntu:~$

---

### Post by meierfra. on 2009-04-27
It seems that your Ubuntu parition on /dev/sdc1 is still using the old kernel. Try this:

Boot from the LiveCD and open a terminal.Then

```
sudo mount /dev/sdc1 /mnt
cd /mnt
sudo cp {/,}etc/resolv.conf
sudo mount --bind {/,}proc
sudo mount --bind {/,}sys
sudo mount --bind {/,}dev
sudo chroot /mnt
```

and at the new prompt



```
apt-get update
apt-get dist-upgrade
```

Post the whole content of the terminal.

Reboot and see whether you can boot into Ubuntu.

---

### Post by gretarsson on 2009-04-28
> **meierfra. said:**
> It seems that your Ubuntu parition on /dev/sdc1 is still using the old kernel. Try this:

Boot from the LiveCD and open a terminal.Then

```
sudo mount /dev/sdc1 /mnt
cd /mnt
sudo cp {/,}etc/resolv.conf
sudo mount --bind {/,}proc
sudo mount --bind {/,}sys
sudo mount --bind {/,}dev
sudo chroot /mnt
```

and at the new prompt



```
apt-get update
apt-get dist-upgrade
```

Post the whole content of the terminal.

Reboot and see whether you can boot into Ubuntu.

Hi again and thanks for your giving your time for your help here are  my list from terminal

```
ubuntu@ubuntu:~$ sudo mount /dev/sdc1 /mnt
ubuntu@ubuntu:~$ cd /mnt
ubuntu@ubuntu:/mnt$ sudo cp {/,}etc/resolv.conf
ubuntu@ubuntu:/mnt$ sudo cp {/,}etc/resolv.conf
ubuntu@ubuntu:/mnt$ sudo mount --bind {/,}proc
ubuntu@ubuntu:/mnt$ sudo mount --bind {/,}sys
ubuntu@ubuntu:/mnt$ sudo mount --bind {/,}dev
ubuntu@ubuntu:/mnt$ sudo chroot /mnt
root@ubuntu:/# apt-get update
Hit http://ubuntu.lhi.is intrepid Release.gpg
Ign http://ubuntu.lhi.is intrepid/main Translation-en_US
Ign http://ubuntu.lhi.is intrepid/universe Translation-en_US                   
Ign http://ubuntu.lhi.is intrepid/restricted Translation-en_US                 
Hit http://ubuntu.lhi.is intrepid Release                                      
Hit http://ubuntu.lhi.is intrepid/main Packages                                
Hit http://ubuntu.lhi.is intrepid/universe Packages
Hit http://ubuntu.lhi.is intrepid/restricted Packages
Hit http://archive.canonical.com jaunty Release.gpg
Ign http://archive.canonical.com jaunty/partner Translation-en_US
Hit http://archive.ubuntu.com jaunty Release.gpg
Ign http://archive.ubuntu.com jaunty/main Translation-en_US
Hit http://archive.canonical.com jaunty Release
Ign http://archive.ubuntu.com jaunty/restricted Translation-en_US
Ign http://archive.ubuntu.com jaunty/universe Translation-en_US
Ign http://archive.ubuntu.com jaunty/multiverse Translation-en_US
Get:1 http://archive.ubuntu.com jaunty-updates Release.gpg [189B]
Ign http://archive.ubuntu.com jaunty-updates/main Translation-en_US
Ign http://archive.ubuntu.com jaunty-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com jaunty-updates/universe Translation-en_US
Ign http://archive.ubuntu.com jaunty-updates/multiverse Translation-en_US
Hit http://archive.ubuntu.com jaunty-backports Release.gpg
Ign http://archive.canonical.com jaunty/partner Packages
Ign http://archive.ubuntu.com jaunty-backports/main Translation-en_US
Ign http://archive.ubuntu.com jaunty-backports/restricted Translation-en_US
Ign http://archive.ubuntu.com jaunty-backports/universe Translation-en_US
Ign http://archive.ubuntu.com jaunty-backports/multiverse Translation-en_US
Get:2 http://archive.ubuntu.com jaunty-security Release.gpg [189B]
Ign http://archive.ubuntu.com jaunty-security/main Translation-en_US
Ign http://archive.canonical.com jaunty/partner Sources
Ign http://archive.ubuntu.com jaunty-security/restricted Translation-en_US
Ign http://archive.ubuntu.com jaunty-security/universe Translation-en_US
Ign http://archive.ubuntu.com jaunty-security/multiverse Translation-en_US
Get:3 http://archive.ubuntu.com jaunty-proposed Release.gpg [189B]
Ign http://archive.ubuntu.com jaunty-proposed/restricted Translation-en_US
Ign http://archive.ubuntu.com jaunty-proposed/main Translation-en_US
Ign http://archive.ubuntu.com jaunty-proposed/multiverse Translation-en_US
Ign http://archive.ubuntu.com jaunty-proposed/universe Translation-en_US
Hit http://archive.ubuntu.com jaunty Release   
Hit http://archive.canonical.com jaunty/partner Packages            
Get:4 http://archive.ubuntu.com jaunty-updates Release [49.6kB]     
Hit http://archive.canonical.com jaunty/partner Sources
Hit http://archive.ubuntu.com jaunty-backports Release
Get:5 http://archive.ubuntu.com jaunty-security Release [49.6kB]
Get:6 http://archive.ubuntu.com jaunty-proposed Release [49.6kB]
Hit http://archive.ubuntu.com jaunty/main Packages    
Hit http://archive.ubuntu.com jaunty/restricted Packages
Hit http://archive.ubuntu.com jaunty/restricted Sources
Hit http://archive.ubuntu.com jaunty/main Sources
Hit http://archive.ubuntu.com jaunty/multiverse Sources
Hit http://archive.ubuntu.com jaunty/universe Sources
Hit http://archive.ubuntu.com jaunty/universe Packages
Hit http://archive.ubuntu.com jaunty/multiverse Packages
Get:7 http://archive.ubuntu.com jaunty-updates/main Packages [14.4kB]
Get:8 http://archive.ubuntu.com jaunty-updates/restricted Packages [14B]
Get:9 http://archive.ubuntu.com jaunty-updates/restricted Sources [14B]
Get:10 http://archive.ubuntu.com jaunty-updates/main Sources [4149B]
Get:11 http://archive.ubuntu.com jaunty-updates/multiverse Sources [14B]
Get:12 http://archive.ubuntu.com jaunty-updates/universe Sources [14B]
Get:13 http://archive.ubuntu.com jaunty-updates/universe Packages [5411B]
Get:14 http://archive.ubuntu.com jaunty-updates/multiverse Packages [14B]
Hit http://archive.ubuntu.com jaunty-backports/main Packages
Hit http://archive.ubuntu.com jaunty-backports/restricted Packages
Hit http://archive.ubuntu.com jaunty-backports/universe Packages
Hit http://archive.ubuntu.com jaunty-backports/multiverse Packages
Hit http://archive.ubuntu.com jaunty-backports/main Sources
Hit http://archive.ubuntu.com jaunty-backports/restricted Sources
Hit http://archive.ubuntu.com jaunty-backports/universe Sources
Hit http://archive.ubuntu.com jaunty-backports/multiverse Sources
Get:15 http://archive.ubuntu.com jaunty-security/main Packages [11.5kB]
Get:16 http://archive.ubuntu.com jaunty-security/restricted Packages [14B]
Get:17 http://archive.ubuntu.com jaunty-security/restricted Sources [14B]
Get:18 http://archive.ubuntu.com jaunty-security/main Sources [3370B]
Get:19 http://archive.ubuntu.com jaunty-security/multiverse Sources [14B]
Get:20 http://archive.ubuntu.com jaunty-security/universe Sources [14B]
Get:21 http://archive.ubuntu.com jaunty-security/universe Packages [4141B]
Get:22 http://archive.ubuntu.com jaunty-security/multiverse Packages [14B]
Get:23 http://archive.ubuntu.com jaunty-proposed/restricted Packages [14B]
Get:24 http://archive.ubuntu.com jaunty-proposed/main Packages [31.0kB]
Get:25 http://archive.ubuntu.com jaunty-proposed/multiverse Packages [2241B]
Get:26 http://archive.ubuntu.com jaunty-proposed/universe Packages [8968B]
Get:27 http://archive.ubuntu.com jaunty-proposed/restricted Sources [14B]
Get:28 http://archive.ubuntu.com jaunty-proposed/main Sources [10.6kB]
Get:29 http://archive.ubuntu.com jaunty-proposed/multiverse Sources [796B]
Get:30 http://archive.ubuntu.com jaunty-proposed/universe Sources [2097B]
Fetched 248kB in 1s (130kB/s)                        
Failed to open connection to "system" message bus: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory
E: Problem executing scripts APT::Update::Post-Invoke-Success '/usr/bin/dbus-send --system --dest=org.freedesktop.PackageKit --type=method_call /org/freedesktop/PackageKit org.freedesktop.PackageKit.StateHasChanged string:'cache-update''
E: Sub-process returned an error code
root@ubuntu:/# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  scim-gtk2-immodule: Depends: scim-modules-socket (= 1.4.7-3ubuntu12) but 1.4.7-3ubuntu10 is installed
W: Duplicate sources.list entry http://archive.ubuntu.com jaunty/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_jaunty_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://archive.ubuntu.com jaunty/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_jaunty_restricted_binary-amd64_Packages)
W: You may want to run apt-get update to correct these problems
E: Unmet dependencies. Try using -f.
root@ubuntu:/# 
```

---

### Post by meierfra. on 2009-04-30
Try the commands from  my last post again. But once you are at the "root@ubuntu" prompt do

```

apt-get -f install
dpkg --configure -a
apt-get  update
apt-get dist-upgrade 
```

---

### Post by gretarsson on 2009-05-01
> **meierfra. said:**
> Try the commands from  my last post again. But once you are at the "root@ubuntu" prompt do

```

apt-get -f install
dpkg --configure -a
apt-get  update
apt-get dist-upgrade 
```

Thanks for reply but  my grub and fstab was so f.. up.  so I went in terminal and took backup copy of my folders and then I made clean install of 9.04  so you can say my problem is gone now.  I say Thanks people for all your time trying to help me

---

### Post by inobe on 2009-05-01
heres really good Grub ubuntu documentation.

[https://help.ubuntu.com/community/GrubHowto#head-616e8477b76f70cdd317812fef0ac88b248e25b4](https://help.ubuntu.com/community/GrubHowto#head-616e8477b76f70cdd317812fef0ac88b248e25b4)

may not be needed' but thought it should be posted for reference.

---

