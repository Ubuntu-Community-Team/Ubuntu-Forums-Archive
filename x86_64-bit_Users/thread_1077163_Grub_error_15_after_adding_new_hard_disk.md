---
title: "Grub error 15 after adding new hard disk"
date: 2009-02-22
forum: x86 64-bit Users
---

### Post by underground on 2009-02-22
Hello!!
I bought a new wd 1tb hard disk and installed it today to my pc....i booted without problems to windows and i have already about 100gb in the new disk...the disk was formated as ntfs in windows...

About 2 hours ago...i restarted and now i can't see the grub menu...instead it shows me an error 15...it is a file not found error isn't it??

Why i have this problem??Is it because i installed a new hard drive??
Now i am writing from a live cd...

Please help me to restore back the grub...

---

### Post by caljohnsmith on 2009-02-22
In order to get a clearer picture of your setup, how about downloading the **Boot Info Script** to your Ubuntu Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by underground on 2009-02-22
OK..i did it and below are the results
```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #8 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Grub0.97 is installed in the MBR of /dev/sdc and looks on boot drive #2 in 
    partition #8 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda8: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdc5 starts 
                       at sector 4209030. But according to the info from 
                       fdisk, sdc5 starts at sector 4209093.
    Operating System:  
    Boot files/dirs:   

sdc6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdc6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x65f765f7

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   104,840,189   104,840,127   7 HPFS/NTFS
/dev/sda2         104,840,190   780,566,219   675,726,030   f W95 Ext d (LBA)
/dev/sda5         104,840,253   525,534,344   420,694,092   7 HPFS/NTFS
/dev/sda6         525,534,408   676,545,344   151,010,937   7 HPFS/NTFS
/dev/sda7         676,545,408   716,547,194    40,001,787  83 Linux
/dev/sda8         716,547,258   776,566,034    60,018,777  83 Linux
/dev/sda9         776,566,098   780,566,219     4,000,122  82 Linux swap / Solaris


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x46b478be

Partition  Boot         Start           End          Size  Id System

/dev/sdb1              16,065 1,953,520,064 1,953,504,000   f W95 Ext d (LBA)
/dev/sdb5              16,128 1,953,520,064 1,953,503,937   7 HPFS/NTFS


Drive sdc: _____________________________________________________________________

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x13081308

Partition  Boot         Start           End          Size  Id System

/dev/sdc1           4,209,030    81,995,759    77,786,730   f W95 Ext d (LBA)
/dev/sdc5           4,209,093    35,664,299    31,455,207   7 HPFS/NTFS
/dev/sdc6          35,664,363    81,995,759    46,331,397   7 HPFS/NTFS
/dev/sdc2          81,995,823   541,727,864   459,732,042   7 HPFS/NTFS
/dev/sdc3    *    541,727,865   625,121,279    83,393,415   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="5668CD1E68CCFDAD" LABEL="Windows" TYPE="ntfs" 
/dev/sda5: UUID="1EAC68A7AC687AE3" LABEL="Music" TYPE="ntfs" 
/dev/sda6: UUID="5834C3AF34C38F06" LABEL="Progz" TYPE="ntfs" 
/dev/sda7: UUID="6169ee2d-bb95-412e-9904-48a713a8ef0c" TYPE="ext3" 
/dev/sda8: UUID="5502d099-190e-4d34-86ad-fc983feddf43" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda9: UUID="5e63565d-3dfa-4882-8a6f-be35dfc35811" TYPE="swap" 
/dev/sdb5: UUID="E8E47E74E47E453A" LABEL="1TB" TYPE="ntfs" 
/dev/sdc2: UUID="BACCB8A4CCB85BF7" LABEL="220 GB!!!" TYPE="ntfs" 
/dev/sdc3: UUID="42D473DFD473D39F" LABEL="Punk" TYPE="ntfs" 
/dev/sdc5: UUID="2CE89A66E89A2E58" LABEL="xazomares" TYPE="ntfs" 
/dev/sdc6: UUID="086432116432024C" LABEL="lol" TYPE="ntfs" 
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
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda7 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sdb5 on /media/1TB type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /usepmtimer


=========================== sda7/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=6169ee2d-bb95-412e-9904-48a713a8ef0c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=6169ee2d-bb95-412e-9904-48a713a8ef0c

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

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		6169ee2d-bb95-412e-9904-48a713a8ef0c
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=6169ee2d-bb95-412e-9904-48a713a8ef0c ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		6169ee2d-bb95-412e-9904-48a713a8ef0c
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=6169ee2d-bb95-412e-9904-48a713a8ef0c ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-10-generic
uuid		6169ee2d-bb95-412e-9904-48a713a8ef0c
kernel		/boot/vmlinuz-2.6.27-10-generic root=UUID=6169ee2d-bb95-412e-9904-48a713a8ef0c ro quiet splash 
initrd		/boot/initrd.img-2.6.27-10-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-10-generic (recovery mode)
uuid		6169ee2d-bb95-412e-9904-48a713a8ef0c
kernel		/boot/vmlinuz-2.6.27-10-generic root=UUID=6169ee2d-bb95-412e-9904-48a713a8ef0c ro  single
initrd		/boot/initrd.img-2.6.27-10-generic

title		Ubuntu 8.10, kernel 2.6.27-8-generic
uuid		6169ee2d-bb95-412e-9904-48a713a8ef0c
kernel		/boot/vmlinuz-2.6.27-8-generic root=UUID=6169ee2d-bb95-412e-9904-48a713a8ef0c ro quiet splash 
initrd		/boot/initrd.img-2.6.27-8-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-8-generic (recovery mode)
uuid		6169ee2d-bb95-412e-9904-48a713a8ef0c
kernel		/boot/vmlinuz-2.6.27-8-generic root=UUID=6169ee2d-bb95-412e-9904-48a713a8ef0c ro  single
initrd		/boot/initrd.img-2.6.27-8-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		6169ee2d-bb95-412e-9904-48a713a8ef0c
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=6169ee2d-bb95-412e-9904-48a713a8ef0c ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		6169ee2d-bb95-412e-9904-48a713a8ef0c
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=6169ee2d-bb95-412e-9904-48a713a8ef0c ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		6169ee2d-bb95-412e-9904-48a713a8ef0c
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd1,0)
map (hd1) (hd0)
map (hd0) (hd1)
savedefault
makeactive
chainloader	+1


=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda8 :
UUID=6169ee2d-bb95-412e-9904-48a713a8ef0c / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda9 :
UUID=5502d099-190e-4d34-86ad-fc983feddf43 /home ext3 relatime 0 2
# Entry for /dev/sda7 :
UUID=5e63565d-3dfa-4882-8a6f-be35dfc35811 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sdb6 /media/lol ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sdb5 /media/xazomares ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sdb3 /media/Punk ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sdb2 /media/220\040GB!!! ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda6 /media/Progz ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda5 /media/Music ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda1 /media/Windows ntfs-3g defaults,locale=en_US.UTF-8 0 0

=================== sda7: Location of files loaded by Grub: ===================


 349.3GB: boot/grub/menu.lst
 349.3GB: boot/grub/stage2
 349.3GB: boot/initrd.img-2.6.27-10-generic
 349.4GB: boot/initrd.img-2.6.27-11-generic
 349.2GB: boot/initrd.img-2.6.27-7-generic
 349.3GB: boot/initrd.img-2.6.27-8-generic
 349.3GB: boot/vmlinuz-2.6.27-10-generic
 349.4GB: boot/vmlinuz-2.6.27-11-generic
 349.2GB: boot/vmlinuz-2.6.27-7-generic
 349.3GB: boot/vmlinuz-2.6.27-8-generic
 349.4GB: initrd.img
 349.3GB: initrd.img.old
 349.4GB: vmlinuz
 349.3GB: vmlinuz.old

```

---

### Post by caljohnsmith on 2009-02-22
OK, how about doing:
```
sudo grub
grub> root (hd0,6)
grub> setup (hd0)
grub> quit
```
Reboot, and I think you should be able to boot into Ubuntu just fine (assuming you are booting the sda drive on start up), but let me know if you run into problems. Also, it looks like you may have the wrong entry in your menu.lst to boot Windows, so let me know if you have problems booting Windows from your Grub menu.

---

### Post by underground on 2009-02-22
I did what you said but the same error remains...error 15

Does it matter tha i am from live cd??

---

### Post by caljohnsmith on 2009-02-22
It's OK that you are using the Live CD, but did the Grub commands say they completed successfully? If so, you are probably booting your sdc drive on start up instead of the sda drive. Can you go into your BIOS and change the boot order so that your 400 GB sda drive is first to boot?

---

### Post by underground on 2009-02-22
Yes the problem was in bios...now i can see the grub menu and also boot to ubuntu..

But...i can't boot in windows...invalid device requested
That's the new error...do you know what i have to change?

---

### Post by caljohnsmith on 2009-02-22
Try changing your Windows entry to:
```
title		Microsoft Windows XP Professional
root		(hd0,0)
chainloader	+1
```
Let me know if that works or not.

---

### Post by underground on 2009-02-22
I changed it and now everything works fine...

Thank you very very much my friend!!!you can't imagine how helpful you was!!!

Sorry for my english...long time without practising..

---

### Post by caljohnsmith on 2009-02-22
You're welcome, glad to hear that worked OK; cheers and enjoy your dual-boot Ubuntu/Windows setup. :)

---

