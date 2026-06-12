---
title: "Booting into 8.10 64bit w/NeoGrub"
date: 2009-01-18
forum: x86 64-bit Users
---

### Post by AustinJM on 2009-01-18
I use EasyBCD to boot Vista, XP, NeoGrub and a Windows 7 beta .  I loaded 64 bit 8.10, and I'm trying to use NeoGrub to boot into it.

Can someone assist with the correct NeoGrub config file?  

I know I have the correct hdd and partition - it's the only ext3 partition.  When I select these options with NeoGrub, it says file not found.  

#new entry
title		Ubuntu 8.10 (hd3,1) 2.6.22-14 
root		(hd3,1)   	#hdd4 part2
kernel		/boot/vmlinuz-2.6.22-14-generic root=/dev/sdd2
initrd		/boot/initrd.img-2.6.22-14-generic
#End entry

#new entry
title		Ubuntu 8.10 (hd3,1) 2.6.27-9
root		(hd3,1)   	#hdd4 part2
kernel		/boot/vmlinuz-2.6.27-9-generic root=/dev/sdd2
initrd		/boot/initrd.img-2.6.27-9-generic
#End entry

#new entry
title		Ubuntu 8.10 (hd3,1) 2.6.27-9 
root		(hd3,1)   	#hd4 part2
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=45d5665d-e465-11dd-b221-0001e8c0bdec ro single
initrd		/boot/initrd.img-2.6.27-9-generic
#End entry

#new entry
title		Ubuntu 8.10 (hd3,1) 2.6.27-7
root		(hd3,1)   	#hdd4 part2
kernel		/boot/vmlinuz-2.6.27-7-generic root=/dev/sdd2
initrd		/boot/initrd.img-2.6.27-7-generic
#End entry

---

### Post by caljohnsmith on 2009-01-18
In order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what it will take to boot Ubuntu using NeoGrub.

---

### Post by AustinJM on 2009-01-19
Based on the results.txt file, I entered the following in NeoGrub config file:

```
title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		0180d1d8-c6ee-439e-be68-1d841c13db26
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=0180d1d8-c6ee-439e-be68-1d841c13db26 ro quiet splash
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		0180d1d8-c6ee-439e-be68-1d841c13db26
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=0180d1d8-c6ee-439e-be68-1d841c13db26 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		0180d1d8-c6ee-439e-be68-1d841c13db26
kernel		/boot/memtest86+.bin
quiet
```

The above didn't allow me to boot into Ubuntu.


Here's the full RESULTS.txt file:

(sorry it's so long...)

```
============================= Boot Info Summary: ==============================



 => Drive sde does not have a valid partition table.

 => Windows is installed in the MBR of /dev/sda

 => Windows is installed in the MBR of /dev/sdb

 => Windows is installed in the MBR of /dev/sdc

 => Windows is installed in the MBR of /dev/sdd



sda1: _________________________________________________________________________



    File system:       ntfs

    Boot sector type:  Windows Vista

    Boot sector info:  No errors found in the Boot Parameter Block.

    Operating System:  Windows Vista

    Boot files/dirs:   /NST/menu.lst /bootmgr /Boot /NST



sdb1: _________________________________________________________________________



    File system:       ntfs

    Boot sector type:  Windows Vista

    Boot sector info:  No errors found in the Boot Parameter Block.

    Operating System:  

    Boot files/dirs:   



sdc1: _________________________________________________________________________



    File system:       

    Boot sector type:  -

    Boot sector info:  

    Mounting failed:

mount: you must specify the filesystem type



sdc2: _________________________________________________________________________



    File system:       ntfs

    Boot sector type:  Windows Vista

    Boot sector info:  According to the info in the boot sector, sdc2 starts 

                       at sector 264192. But according to the info from 

                       fdisk, sdc2 starts at sector .

    Operating System:  

    Boot files/dirs:   

sdd1: _________________________________________________________________________



    File system:       ntfs

    Boot sector type:  Windows Vista

    Boot sector info:  No errors found in the Boot Parameter Block.

    Operating System:  

    Boot files/dirs:   



sdd2: _________________________________________________________________________



    File system:       ext3

    Boot sector type:  Grub

    Boot sector info:  Grub0.97 is installed in the boot sector of /dev/sdd2 

                       and looks at sector 663771136 of the same hard drive 

                       for the stage2 file and on partition #2 for 

                       /boot/grub/menu.lst .

    Operating System:  Ubuntu 8.10

    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub



sdd3: _________________________________________________________________________



    File system:       ntfs

    Boot sector type:  Windows Vista

    Boot sector info:  No errors found in the Boot Parameter Block.

    Operating System:  Windows Vista

    Boot files/dirs:   



=========================== Drive/Partition Info: =============================



Drive sda: _____________________________________________________________________



fdisk -lu /dev/sda:



Disk /dev/sda: 150.0 GB, 150039945216 bytes

255 heads, 63 sectors/track, 18241 cylinders, total 293046768 sectors

Units = sectors of 1 * 512 = 512 bytes

Disk identifier: 0x3c4544ef



   Device Boot      Start         End      Blocks   Id  System

/dev/sda1   *        2048   293044223   146521088    7  HPFS/NTFS



sfdisk -V /dev/sda:



Warning: partition 1 extends past end of disk



Drive sdb: _____________________________________________________________________



fdisk -lu /dev/sdb:



Disk /dev/sdb: 500.1 GB, 500107862016 bytes

255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors

Units = sectors of 1 * 512 = 512 bytes

Disk identifier: 0x9cb40896



   Device Boot      Start         End      Blocks   Id  System

/dev/sdb1            2048   976771071   488384512    7  HPFS/NTFS


sfdisk -V /dev/sdb:



Warning: partition 1 extends past end of disk



Drive sdc: _____________________________________________________________________



fdisk -lu /dev/sdc:



Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes

256 heads, 63 sectors/track, 121126 cylinders, total 1953525168 sectors

Units = sectors of 1 * 512 = 512 bytes

Disk identifier: 0x6c827132



   Device Boot      Start         End      Blocks   Id  System

/dev/sdc1               1  4294967295  2147483647+  ee  GPT



sfdisk -V /dev/sdc:




WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util sfdisk 
doesn't support GPT. Use GNU Parted.



Warning: partition 1 extends past end of disk



Drive sdd: _____________________________________________________________________



fdisk -lu /dev/sdd:



Disk /dev/sdd: 500.1 GB, 500107862016 bytes

255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors

Units = sectors of 1 * 512 = 512 bytes

Disk identifier: 0xa828be7e



   Device Boot      Start         End      Blocks   Id  System

/dev/sdd1            2048   618371063   309184508    7  HPFS/NTFS

/dev/sdd2       618371072   669569023    25598976   83  Linux

/dev/sdd3   *   669571072   976769023   153598976    7  HPFS/NTFS



sfdisk -V /dev/sdd:



Warning: partition 3 extends past end of disk



Drive sde: _____________________________________________________________________



fdisk -lu /dev/sde:



sfdisk -V /dev/sde:

/dev/sde: No medium found



sfdisk: cannot open /dev/sde for reading



blkid -c /dev/null: ____________________________________________________________



/dev/sda1: UUID="0A9C1CCF9C1CB6E3" LABEL="HDD0 Raptor 150Gb" TYPE="ntfs" 

/dev/sdb1: UUID="1A4815D44815B00D" LABEL="HDD2 Maxtor 500Gb" TYPE="ntfs" 

/dev/sdc2: UUID="9E1E1AFD1E1ACDE1" LABEL="HDD3 WestDigi 1Tb" TYPE="ntfs" 
/dev/sdd1: UUID="38A81F24A81EDFE4" LABEL="HDD1 Maxtor 500Gb" TYPE="ntfs" 

/dev/sdd2: UUID="0180d1d8-c6ee-439e-be68-1d841c13db26" SEC_TYPE="ext2" TYPE="ext3" 

/dev/sdd3: UUID="CAB09F84B09F7623" LABEL="HDD1 Z Partition" TYPE="ntfs" 

/dev/loop0: TYPE="squashfs" 



=============================== "mount" output: ===============================



/proc on /proc type proc (rw)

sysfs on /sys type sysfs (rw)

tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)

tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)

tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)

varrun on /var/run type tmpfs (rw,nosuid,mode=0755)

varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)

udev on /dev type tmpfs (rw,mode=0755)

tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)

devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)

rootfs on / type rootfs (rw)

fusectl on /sys/fs/fuse/connections type fusectl (rw)

/dev/scd0 on /cdrom type iso9660 (ro,noatime)

/dev/loop0 on /rofs type squashfs (ro,noatime)

tmpfs on /tmp type tmpfs (rw,nosuid,nodev)

binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
g
vfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)



============================== sda1/NST/menu.lst: ==============================



# NeoSmart NeoGrub Bootloader Configuration File
#
# This is the NeoGrub configuration file, and should be located at C:\NST\menu.lst
# Please see the EasyBCD Documentation for information on how to create/modify entries:
# http://neosmart.net/wiki/display/EBCD

#This is a comment. Comments are prefixed with a '#'

default 0		#Pick the task to be run if the user doesn't pick one within the time limit.
timeout 15		#Give the user 10 seconds to choose a task.

#"title" keyword indicates a new entry in the menu
title		Ubuntu (hd3,1) 2.6.22-14   
root		(hd3,1)   	#Load Ubuntu from the 4th harddrive's 2 partition.
#Next Line: Translate (hd3,1) to Linux notation and set that as the root partition
kernel		/boot/vmlinuz-2.6.22-14-generic root=/dev/sdd2
initrd		/boot/initrd.img-2.6.22-14-generic
#End Ubuntu entry

#"title" keyword indicates a new entry in the menu
title		Ubuntu (hd3,1) 2.6.27-9   
root		(hd3,1)   	#Load Ubuntu from the 4th harddrive's 2 partition.
#Next Line: Translate (hd3,1) to Linux notation and set that as the root partition
kernel		/boot/vmlinuz-2.6.27-9-generic root=/dev/sdd2
initrd		/boot/initrd.img-2.6.27-9-generic
#End Ubuntu entry

#"title" keyword indicates a new entry in the menu
title		Ubuntu (hd3,1) 2.6.27-7   
root		(hd3,1)   	#Load Ubuntu from the 4th harddrive's 2 partition.
#Next Line: Translate (hd3,1) to Linux notation and set that as the root partition
kernel		/boot/vmlinuz-2.6.27-7-generic root=/dev/sdd2
initrd		/boot/initrd.img-2.6.27-7-generic
#End Ubuntu entry

#"title" keyword indicates a new entry in the menu
title Ubuntu 8.10, kernel 2.6.27-7-generic
uuid ddcc8f13-1e42-457d-a481-8c8fd17f1445
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=45d5665d-e465-11dd-b221-001e8c0b0dec ro quiet splash
initrd /boot/initrd.img-2.6.27-7-generic
quiet

#"title" keyword indicates a new entry in the menu
title Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid ddcc8f13-1e42-457d-a481-8c8fd17f1445
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=45d5665d-e465-11dd-b221-001e8c0b0dec ro single
initrd /boot/initrd.img-2.6.27-7-generic

#"title" keyword indicates a new entry in the menu
title Ubuntu 8.10, memtest86+
uuid ddcc8f13-1e42-457d-a481-8c8fd17f1445
kernel /boot/memtest86+.bin
quiet


================================== sda1/Boot: ==================================


total 852

drwxrwxrwx 1 root root   4096 2009-01-17 07:40 .

drwxrwxrwx 1 root root  20480 2009-01-18 01:46 ..

-rwxrwxrwx 1 root root  45056 2009-01-19 04:32 BCD

-rwxrwxrwx 1 root root 262144 2009-01-18 20:36 BCD.LOG

-rwxrwxrwx 2 root root      0 2008-01-01 19:40 BCD.LOG1

-rwxrwxrwx 2 root root      0 2008-01-01 19:40 BCD.LOG2

-rwxrwxrwx 1 root root  65536 2009-01-17 07:40 bootstat.dat

drwxrwxrwx 1 root root      0 2009-01-17 07:40 cs-CZ

drwxrwxrwx 1 root root      0 2009-01-17 07:40 da-DK

drwxrwxrwx 1 root root      0 2009-01-17 07:40 de-DE

drwxrwxrwx 1 root root      0 2009-01-17 07:40 el-GR

drwxrwxrwx 1 root root      0 2009-01-17 07:40 en-US

drwxrwxrwx 1 root root      0 2009-01-17 07:40 es-ES

drwxrwxrwx 1 root root      0 2009-01-17 07:40 fi-FI

drwxrwxrwx 1 root root      0 2009-01-17 07:40 Fonts

drwxrwxrwx 1 root root      0 2009-01-17 07:40 fr-FR

drwxrwxrwx 1 root root      0 2009-01-17 07:40 hu-HU

drwxrwxrwx 1 root root      0 2009-01-17 07:40 it-IT

drwxrwxrwx 1 root root      0 2009-01-17 07:40 ja-JP

drwxrwxrwx 1 root root      0 2009-01-17 07:40 ko-KR

-rwxrwxrwx 1 root root 473864 2008-12-13 07:01 memtest.exe

drwxrwxrwx 1 root root      0 2009-01-17 07:40 nb-NO

drwxrwxrwx 1 root root      0 2009-01-17 07:40 nl-NL

drwxrwxrwx 1 root root      0 2009-01-17 07:40 pl-PL

drwxrwxrwx 1 root root      0 2009-01-17 07:40 pt-BR

drwxrwxrwx 1 root root      0 2009-01-17 07:40 pt-PT

drwxrwxrwx 1 root root      0 2009-01-17 07:40 ru-RU

drwxrwxrwx 1 root root      0 2009-01-17 07:40 sv-SE

drwxrwxrwx 1 root root      0 2009-01-17 07:40 tr-TR

drwxrwxrwx 1 root root      0 2009-01-17 07:40 zh-CN

drwxrwxrwx 1 root root      0 2009-01-17 07:40 zh-HK

drwxrwxrwx 1 root root      0 2009-01-17 07:40 zh-TW

================================== sda1/NST: ==================================


total 32

drwxrwxrwx 1 root root     0 2009-01-18 01:46 .

drwxrwxrwx 1 root root 20480 2009-01-18 01:46 ..

-rwxrwxrwx 1 root root  2304 2009-01-18 20:24 menu.lst

-rwxrwxrwx 1 root root  8192 2008-04-08 17:50 NeoGrub.mbr


=========================== sdd2/boot/grub/menu.lst: ===========================



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

# kopt=root=UUID=0180d1d8-c6ee-439e-be68-1d841c13db26 ro



## default grub root device

## e.g. groot=(hd0,0)

# groot=0180d1d8-c6ee-439e-be68-1d841c13db26



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



title		Ubuntu 8.10, kernel 2.6.27-7-generic

uuid		0180d1d8-c6ee-439e-be68-1d841c13db26

kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=0180d1d8-c6ee-439e-be68-1d841c13db26 ro quiet splash

initrd		/boot/initrd.img-2.6.27-7-generic

quiet



title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)

uuid		0180d1d8-c6ee-439e-be68-1d841c13db26

kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=0180d1d8-c6ee-439e-be68-1d841c13db26 ro  single

initrd		/boot/initrd.img-2.6.27-7-generic



title		Ubuntu 8.10, memtest86+

uuid		0180d1d8-c6ee-439e-be68-1d841c13db26

kernel		/boot/memtest86+.bin

quiet



### END DEBIAN AUTOMAGIC KERNELS LIST



# This is a divider, added to separate the menu items below from the Debian

# ones.

title		Other operating systems:

root




# This entry automatically added by the Debian installer for a non-linux OS

# on /dev/sda1

title		Windows Vista/Longhorn (loader)

root		(hd0,0)

savedefault

chainloader	+1




=============================== sdd2/etc/fstab: ===============================


# /etc/fstab: static file system information.

#

# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc            /proc           proc    defaults        0       0

# /dev/sdd2

UUID=0180d1d8-c6ee-439e-be68-1d841c13db26 /               ext3    relatime,errors=remount-ro 0       1

/dev/scd2       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0



================================== sdd2/boot: ==================================



total 12808
drwxr-xr-x  3 root root    4096 2009-01-18 00:32 .

drwxr-xr-x 20 root root    4096 2009-01-18 00:32 ..

-rw-r--r--  1 root root  503560 2008-10-24 07:55 abi-2.6.27-7-generic

-rw-r--r--  1 root root   85316 2008-10-24 07:55 config-2.6.27-7-generic

drwxr-xr-x  2 root root    4096 2009-01-18 00:32 grub

-rw-r--r--  1 root root 8646214 2009-01-18 00:32 initrd.img-2.6.27-7-generic

-rw-r--r--  1 root root  124152 2008-09-11 20:11 memtest86+.bin

-rw-r--r--  1 root root 1352144 2008-10-24 07:55 System.map-2.6.27-7-generic

-rw-r--r--  1 root root    1130 2008-10-24 07:57 vmcoreinfo-2.6.27-7-generic

-rw-r--r--  1 root root 2339712 2008-10-24 07:55 vmlinuz-2.6.27-7-generic



=============================== sdd2/boot/grub: ===============================


total 216

drwxr-xr-x 2 root root   4096 2009-01-18 00:32 .

drwxr-xr-x 3 root root   4096 2009-01-18 00:32 ..

-rw-r--r-- 1 root root    197 2009-01-18 00:32 default

-rw-r--r-- 1 root root     60 2009-01-18 00:32 device.map

-rw-r--r-- 1 root root   8108 2009-01-18 00:32 e2fs_stage1_5

-rw-r--r-- 1 root root   7856 2009-01-18 00:32 fat_stage1_5

-rw-r--r-- 1 root root     16 2009-01-18 00:32 installed-version

-rw-r--r-- 1 root root   8712 2009-01-18 00:32 jfs_stage1_5

-rw-r--r-- 1 root root   4608 2009-01-18 00:32 menu.lst

-rw-r--r-- 1 root root   7352 2009-01-18 00:32 minix_stage1_5

-rw-r--r-- 1 root root   9756 2009-01-18 00:32 reiserfs_stage1_5

-rw-r--r-- 1 root root    512 2009-01-18 00:32 stage1

-rw-r--r-- 1 root root 121460 2009-01-18 00:32 stage2

-rw-r--r-- 1 root root   9556 2009-01-18 00:32 xfs_stage1_5



=============================== StdErr Messages: ===============================



WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util sfdisk doesn't support GPT. Use GNU Parted.


/dev/sde: No medium found

sfdisk: cannot open /dev/sde for reading


WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util sfdisk doesn't support GPT. Use GNU Parted.


Use the --force flag to overrule this check.
/home/ubuntu/Desktop/boot_info_script_011.sh:
line 412: [: =: unary operator expected
/home/ubuntu/Desktop/boot_info_script_011.sh:
line 412: [: =: unary operator expected

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'!
The util sfdisk doesn't support GPT. Use GNU Parted.

Use the --force flag to overrule this check.

/home/ubuntu/Desktop/boot_info_script_011.sh:
line 412: [: =: unary operator expected
/home/ubuntu/Desktop/boot_info_script_011.sh:
line 412: [: =: unary operator expected

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'!
The util fdisk doesn't support GPT. Use GNU Parted.


WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'!
The util sfdisk doesn't support GPT. Use GNU Parted.


WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'!
The util fdisk doesn't support GPT. Use GNU Parted.


```

---

### Post by caljohnsmith on 2009-01-19
I think the only problem may be that NeoGrub doesn't yet support using the lastest "uuid" line notation that Grub now supports, instead of using a "root (hdX,Y)" line. But the good news is that NeoGrub has something just as good, which is the "find" command used to set the root partition. How about instead trying:
```
title		Ubuntu 8.10, kernel 2.6.27-7-generic
[COLOR="Blue"]find --set-root /boot/grub/stage1[/COLOR]
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=0180d1d8-c6ee-439e-be68-1d841c13db26 ro quiet splash
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
[COLOR="Blue"]find --set-root /boot/grub/stage1[/COLOR]
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=0180d1d8-c6ee-439e-be68-1d841c13db26 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
[COLOR="Blue"]find --set-root /boot/grub/stage1[/COLOR]
kernel		/boot/memtest86+.bin
quiet
```
How about giving that a shot and let me know how it goes, or if you run into problems.

---

### Post by AustinJM on 2009-01-19
caljohnsmith - thanks for your help.

When I put the find line in my config file, I receive this error message when trying to boot:

```
Warning: Unrecognized partition table for drive 82.  Please rebuild it using a Microsoft compatible fdisk tool(err=4).  Current C/H/S = 16383/255/63

Error 17:  File not found
```

---

### Post by caljohnsmith on 2009-01-19
The "unrecognized partition table for drive 82" is probably because your sdc drive uses a GPT (GUID Partition Table) rather than the standard MS-DOS partition table, so I don't think that warning is anything to be worried about unless your sdc drive is not supposed to use a GPT. About the Grub error though, how about for your first Ubuntu entry trying:
```
title		Ubuntu 8.10, kernel 2.6.27-7-generic
[COLOR="Blue"]find --set-root /boot/vmlinuz-2.6.27-7-generic[/COLOR]
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=0180d1d8-c6ee-439e-be68-1d841c13db26 ro quiet splash
initrd		/boot/initrd.img-2.6.27-7-generic
quiet
```
If that doesn't work and still gives a Grub error 17, I think that could be a bad sign. So if it doesn't work, how about instead trying:
```
title		Ubuntu 8.10, kernel 2.6.27-7-generic
[COLOR="Blue"]root (hdX,1)[/COLOR]
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=0180d1d8-c6ee-439e-be68-1d841c13db26 ro quiet splash
initrd		/boot/initrd.img-2.6.27-7-generic
quiet
```
And let X be 1 or 2. You might think that X should be 3 since sdd=(hd3) when you run Grub commands, but on start up it is a whole different story: 
```
(hd0) = 1st boot drive
(hd1) = 2nd boot drive
(hd2) = 3rd boot drive
...etc.
```
So on start up the Grub sees the order of drives as the BIOS boot order, not as they are ordered in linux. Thus your sdd drive might be 2nd (hd1) or 3rd (hd2) in the BIOS boot order. Let me know how that goes.

---

### Post by AustinJM on 2009-01-20
Again, thanks for your continued help.

I tried every iteration between (hd0,0) and (hd3,3).  I have only one non-ntfs partition, and it was located at (hd3,1).

When I entered:

```
title		Ubuntu 8.10, kernel 2.6.27-7-generic root (hd3,1)
root (hd3,1)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=0180d1d8-c6ee-439e-be68-1d841c13db26 ro quiet splash
initrd		/boot/initrd.img-2.6.27-7-generic
quiet
```

I received:

```
root (hd3,1)
 Filesystem type is ext2fs, partition type 0x83
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=0180d1d8-c6ee-439e-be68-1d841c13db26 ro quiet splash
Error 2: Bad file or directory type
```

The boot info script you had me run earlier identified that partition as ext3, and that's what I selected when installing 8.10.  I'm not sure why it's now being identified as ext2fs.

---

### Post by caljohnsmith on 2009-01-20
I think I might know what the problem is: Intrepid uses the latest ext3 standard and formats its ext3 partitions differently then all previous versions of Ubuntu. Intrepid uses a 256 byte inode size for its ext3 partitions, whereas previous versions of Ubuntu used a 128 byte inode size. It's interesting to note that NeoGrub is actually a derivative of "Grub4DOS", and I think Grub4DOS began supporting 256 byte inode size ext3 partitions back in about July of 2008; I'm guessing that maybe NeoGrub has not been updated with those changes since it is now independent of the Grub4DOS project. So if that is the case, we should try booting Ubuntu using the "chainloader" technique with NeoGrub, because in that case NeoGrub doesn't have to actually mount the ext3 partition and read the boot files; using "chainloader" simply boots the boot sector of the Ubuntu partition, effectively handing-off the booting process to Ubuntu's Grub without mounting/reading the partition. From the results of the Boot Info Script, you all ready have Grub installed to the boot sector of the Ubuntu partition, so that is all ready to go. So bottom line, how about trying:
```
title Ubuntu's Grub Menu
root (hdX,1)
chainloader +1
```
And again, try X=1,2 and 3, and let me know if that works or not (you could put all three cases in your menu.lst temporarily to make it easy to try them all). Also, since you received a Grub error 2 when using (hd3,1), I think that is probably the correct one to use, but try X=1 and 2 if it doesn't. Let me know how that goes.

---

### Post by AustinJM on 2009-01-20
caljohnsmith - thanks for sticking with me until you fixed my problem!

This worked:
```
title Ubuntu's Grub Menu
root (hd3,1)
chainloader +1
```

I really appreciate your help.  I'm up & running thanks to you.

---

### Post by caljohnsmith on 2009-01-21
Glad to hear that worked OK; cheers and enjoy Vista and Ubuntu. :)

---

### Post by kdegaz on 2009-01-25
Hi,
this sounded the same as the problem I'm having too - I've installed Vista 64bit and Kubuntu 8.10 64bit and had them both working until I tried adding EasyBCD and NeoGRUB, now I can only boot Vista.  I had the eror 17, but have followed caljohnsmith's suggestions and currently have my NST/menu.lst set up with just the three commands in it - title, root and chainloader, and was hoping this would fix my boot problem too, but now I get :

```

GRUB4DOS 0.4.3 2007-06-14, memory: 636k/2942M, codeend 0x3Ef2C
Booting 'Kubuntu Grub Menu'
root (hd0,5)
  filesystem type is ext2fs, partition type 0x83
chainloader +1
Error 14: Invalid or unsupported executable format

```
The hd0,5 is the partition showing as sda6 ext3 with my Kubuntu OS and /boot/grub/menu.lst on it when I look at the boot_info_script results output.

Any ideas why mine won't boot and what I can try next?

Thanks,
Gary.

---

### Post by caljohnsmith on 2009-01-25
Sounds like you might need to install Grub to boot sector of your Kubuntu partition:
```
sudo grub
grub> root (hd0,5)
grub> setup (hd0,5)
grub> quit
```
How about trying that, and if it doesn't work, please run the Boot Info Script from post #2 and post the results.

---

### Post by kdegaz on 2009-01-26
Caljohnsmith, you are a star, that's fixed it and I'm a happy bunny again!   8-)

Thank you so much... I'm off to play with Kubuntu now.

Cheers,
Gary.

---

