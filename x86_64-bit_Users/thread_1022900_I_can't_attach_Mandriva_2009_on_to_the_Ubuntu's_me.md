---
title: "I can't attach Mandriva 2009 on to the Ubuntu's menu.lst file."
date: 2008-12-27
forum: x86 64-bit Users
---

### Post by Gins on 2008-12-27
Hi

My Ubuntu 8.04 LTS Desktop Edition works fine.

I have even installed 'open SuSE' , Windows 2008 Server and Windows Vista.

All works fine. When the computer starts the menu from Ubuntu appears to select the operating system. My default operating system is Ubuntu.

Yesterday I installed Mandriva 2009 too. The installation was fine.
It is not on the menu. I added some stanzas arbitrarily.
......................................................
[I]title Mandriva 2009

root (hd1,4)                      

configfile /boot/grub/menu.lst[/I]
.......................................................

It does not work.

**What are the stanzas for Mandriva 2009?**

I installed Mandriva on 'sdb5' partition; which is a logical partition.

However, Ubuntu is on 'sdb3' partition; which is a primary partition.

I installed open SuSE on 'sdb8' partition; which is a logical partition.


```
sdb1 for Windows 2008 server {Primary partition}
sdb2 for Windows Vista {Primary partition} 
sdb3 for Ubuntu {Primary partition} 
sdb5 for Mandriva 2009 {Logical
sdb6 --- Empty partiton for Linux installations {Logical 
sdb7 --- Small partion (8.0GB) {Linux swap 
sdb8 for open SuSE 10,3 {Logical 
```



**The following is the output of the fdisk file in Ubuntu.**
```
root@ni-desktop:/home/ni# fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes

255 heads, 63 sectors/track, 30401 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0x24312430



   Device Boot      Start         End      Blocks   Id  System

/dev/sda1               2       26912   216162607+   5  Extended

/dev/sda2   *       26913       30402    28025856    7  HPFS/NTFS

/dev/sda5               2        8955    71922973+  83  Linux

/dev/sda6            8956       18034    72927036   83  Linux

/dev/sda7           18035       26912    71312503+  83  Linux



Disk /dev/sdb: 500.1 GB, 500107862016 bytes

255 heads, 63 sectors/track, 60801 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0xdd98dd98



   Device Boot      Start         End      Blocks   Id  System

/dev/sdb1   *           1       13057   104880321    7  HPFS/NTFS

/dev/sdb2           13058       22724    77650177+   7  HPFS/NTFS

/dev/sdb3           22725       31836    73192140   83  Linux

/dev/sdb4           31837       59748   224203140    5  Extended

/dev/sdb5           40791       49744    71922973+  83  Linux

/dev/sdb6           49745       58698    71922973+  83  Linux

/dev/sdb7           58699       59748     8434093+  82  Linux swap / Solaris

/dev/sdb8           31837       40790    71922942   83  Linux



Partition table entries are not in disk order

root@ni-desktop:/home/ni# 

```


**The following is the Ubuntu's menu.ist file.**
```
root@ni-desktop:/boot/grub# cat menu.lst

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

timeout		30



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

# kopt=root=UUID=c5fb4ab5-6767-44e8-b89a-6383b86e2bad ro



## Setup crashdump menu entries

## e.g. crashdump=1

# crashdump=0



## default grub root device

## e.g. groot=(hd0,0)

# groot=(hd1,2)



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



title		Ubuntu 8.04, kernel 2.6.24-16-generic

root		(hd1,2)

kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=c5fb4ab5-6767-44e8-b89a-6383b86e2bad ro quiet splash

initrd		/boot/initrd.img-2.6.24-16-generic

quiet



title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)

root		(hd1,2)

kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=c5fb4ab5-6767-44e8-b89a-6383b86e2bad ro single

initrd		/boot/initrd.img-2.6.24-16-generic



title		Ubuntu 8.04, memtest86+

root		(hd1,2)

kernel		/boot/memtest86+.bin

quiet






title Mandriva 2009


root (hd1,4)                      

configfile /boot/grub/menu.lst







### END DEBIAN AUTOMAGIC KERNELS LIST



# This is a divider, added to separate the menu items below from the Debian

# ones.

title		Other operating systems:

root





# This entry automatically added by the Debian installer for a non-linux OS

# on /dev/sda2

title		Windows 2008 Server

root		(hd0,1)

savedefault

makeactive

chainloader	+1





title           Windows Vista/Longhorn (loader)

root            (hd0,2)

savedefault

makeactive

chainloader     +1




root@n-desktop:/boot/grub# 



```

[COLOR="Blue"]The bottom line is the stanzas for attaching Mandriva 2009 which resides on 'sdb5' partition to Ubuntu's meun.lst file.
I appreciate your help.[/COLOR]

---

### Post by cariboo on 2008-12-27
I really can't tell from the info provided where exactly you installed Mandriva, but have you mounted the partion it is installed on and made sure there actually is a /boot/grub/menu.lst.

If there is I would suggest using uuid to mount your partions. I have a problem with having both ide and sata drives installed and the devicee label changes on occasion, using uuid to mount partitions gets around the problem.

To find the blkid's of your partitions in a terminal type:

```
blkid
```

the result should look something like this:

```
 blkid
/dev/sda1: UUID="7E002ED0002E8F69" TYPE="ntfs" 
/dev/sdb1: UUID="c6afffda-4b72-454e-8bfb-29d122e3cc3e" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="23255756-0fe7-46c5-b66c-1b43e34c5e8d" 
/dev/sda6: UUID="efccc4e7-3273-43d3-871c-1eb69aeaaa27" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: UUID="9f702ef1-20bd-4aef-8f22-cd6830d83a50" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb2: UUID="4c4b39f7-3289-4d4b-b520-f93dd04baab3" SEC_TYPE="ext2" TYPE="ext3"

```

Then edit /boot/grub/menu.lst to look like this:

```
title		Mandriva
uuid		9f702ef1-20bd-4aef-8f22-cd6830d83a50
configfile	/boot/grub/menu.lst
```

Change the uuid to the one that Mandriva is installed on, and you should be good to go.

Jim

---

### Post by logos34 on 2008-12-27
> **cariboo907 said:**
> 
```
title		Mandriva
uuid		9f702ef1-20bd-4aef-8f22-cd6830d83a50
configfile	/boot/grub/menu.lst
```


I thought it had to look like this:

> title Mandriva 2009
configfile (hd1,4)/boot/grub/menu.lst

?

---

### Post by Gins on 2008-12-27
I thank both of you for the excellent comments.


**I am not 100% but 200% sure that I installed Mandriva 2009 on 'sdb5'.**

As far as I am concerned, Mandriva is the easiest Linux distro to install.

It tells you in crystal clear terms every step.

The installation gave me a couple of alternatives to install the bootloader program.

I selected 'the root partition of Mandriva 2009'.

So the GRUB of Mandriva is on its root partition.

It is not the case with 'open SuSE'. 

It dictated terms and I just obliged.

It was not my intention to install 'open SuSE' on 'sdb8' partition.


```
root@ni-desktop:/home/ni# blkid
/dev/sda2: UUID="0290058290057E03" TYPE="ntfs" 
/dev/sda5: LABEL="Linux5" UUID="7e99b107-7ea3-a85d-99a1-b6b7d63875f0" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: LABEL="Linux6" UUID="3cc445e0-9203-4c4d-790b-e968b2b2ff8e" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: LABEL="Linux7" UUID="7086cf99-e968-2aa4-18d9-c97778e0daf0" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: UUID="CE1D3FDB434D957C" LABEL="Windows 200" TYPE="ntfs" 
/dev/sdb2: UUID="7C1596897D349719" LABEL="Windows Vis" TYPE="ntfs" 
/dev/sdb3: UUID="c5fb4ab5-6767-44e8-b89a-6383b86e2bad" TYPE="ext3" 
/dev/sdb5: LABEL="Linux3" UUID="6460a523-8375-40e3-9958-31c179210b3a" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb6: LABEL="Linux4" UUID="513bed05-4400-974b-8ed3-085c7928928e" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb7: TYPE="swap" UUID="743165c2-5731-4133-9976-0fc7fd90d02c" 
/dev/sdb8: UUID="ea708229-6c8b-4f64-a93b-59bee3c3fbcd" SEC_TYPE="ext2" TYPE="ext3" 
root@ni-desktop:/home/ni# 


```

[B]What is the next step?
I will oblige to your suggestions.[/B]

By the way what is this 'blkid' command?
I worked with Linux for over 10 years and I have never heard of it.
It can't be a UNIX command.

---

### Post by logos34 on 2008-12-27
there's also the 'chainloader' method, but grub needs to be installed to the mandriva / partition:

> sudo grub

grub> **find /boot/grub/stage1 **
(->this should output 3 locations--use the mandriva)
grub> **root (hd1,4)**
grub> **setup (hd1,4)**
grub> **quit**

add this entry to ubuntu grub:
> 
title Mandriva 2009
root (hd1,4)
chainloader +1

The only problem I can recall having when trying to dual boot hardy and Mandriva 2008.1 was with the inodes (mandriva uses 256 byte vs. 128)

---

### Post by Gins on 2008-12-27
I edited the 'menu.lst' file and added the following:

-------------------------------------
title Mandriva 2009

root (hd1,4)
chainloader +1 
--------------------------------------
It created big problems when I selected 'Mandriva 2009' from Ubintu's menu. I was forced to shutdown the power.

Please read the following to see the entry.
```
ni@ni-desktop:~$ sudo su root
[sudo] password for ni: 
root@ni-desktop:/home/ni# cd /boot
root@ni-desktop:/boot# cd grub
root@ni-desktop:/boot/grub# ls
default        fat_stage1_5       menu.lst           stage1
device.map     installed-version  minix_stage1_5     stage2
e2fs_stage1_5  jfs_stage1_5       reiserfs_stage1_5  xfs_stage1_5
root@ni-desktop:/boot/grub# cat menu.lst
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
timeout		30

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
# kopt=root=UUID=c5fb4ab5-6767-44e8-b89a-6383b86e2bad ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,2)

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=c5fb4ab5-6767-44e8-b89a-6383b86e2bad ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=c5fb4ab5-6767-44e8-b89a-6383b86e2bad ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd1,2)
kernel		/boot/memtest86+.bin
quiet




title Mandriva 2009

root (hd1,4)
chainloader +1 



                      







### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows 2008 Server
root		(hd0,1)
savedefault
makeactive
chainloader	+1


title           Windows Vista/Longhorn (loader)
root            (hd0,2)
savedefault
makeactive
chainloader     +1

















root@ni
```

---

### Post by logos34 on 2008-12-27
there's a space in your entry between 'title' and 'root'--that can't be helping:

> **Gins said:**
> 
title		Ubuntu 8.04, memtest86+
root		(hd1,2)
kernel		/boot/memtest86+.bin
quiet
[COLOR="Red"]


title Mandriva 2009

root (hd1,4)
chainloader +1 [/COLOR]



                   
### END DEBIAN AUTOMAGIC KERNELS LIST



I would try Super Grub Disk next.  (See link my signature below).  Burn it to cd and boot it.  See if you can boot mandriva that way. 

Either that or reinstall Mandriva on 128 byte inode size, assuming that's the problem.  (in which case you'd need to change the partition options with tune2fs)

---

### Post by caljohnsmith on 2008-12-27
Gins, if the Super Grub Disk doesn't help you solve your booting problem with Mandriva, how about doing:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup and hopefully what your problem might be.

---

### Post by Gins on 2008-12-27
It is too late here. I must leave for work tomorrow morning at 5 o' clock.

I will attend this tomorrow evening.

I must sleep now.

[COLOR="SeaGreen"]I take my hat off for all the help.[/COLOR]

Please keep a good watch on this thread.

PS
I can't burn program using the K3b program.

A friend of mine who uses windows downaloaded and burnt Mandriva DVD.

He lives far away.

[B]I can download programs. I can't burn using the K3b. I get an error message. Some bloody problems with the latest K3b.

This is hell for me.[/B]

---

### Post by logos34 on 2008-12-27
you know, you can use Nautilus to burn discs too (CD/DVD Creator)

---

