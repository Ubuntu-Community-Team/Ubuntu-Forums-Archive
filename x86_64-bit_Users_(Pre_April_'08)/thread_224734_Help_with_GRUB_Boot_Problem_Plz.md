---
title: "Help with GRUB Boot Problem Plz"
date: 2006-07-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by trogbot on 2006-07-28
Can anyone help me with a GRUB boot problem?  My system is as follows:

AMD 64 3400+
1 GIG Memory
1 IDE 80 GB Drive (Ubuntu)
2 SATA 160 GB Drives Mirror'd (Win XP Pro)
1 IDE3 120 GB Drive  (OpenSuse)
DVD-RW/CD-RW/Floppy

My problem is that the MBR on 1st drive reflects all the OS's, but will not let me boot SUSE after Ubuntu was installed.  The same thing happened when I installed SUSE.  It would let me boot all but Ubuntu.

I have Ubuntu set up now with shared printer for Win Users and Samba running.  Can use CUPS & SWAT browser interfaces, etc. & don't want to lose my Ubuntu setup; but would like to play with Suse also.

My disks display is as follows:

code
Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13054   104856223+   7  HPFS/NTFS

Disk /dev/sdb: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       13054   104856223+   7  HPFS/NTFS

Disk /dev/sdc: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       10443    83883366    7  HPFS/NTFS
/dev/sdc2           10444       12244    14466532+  83  Linux
/dev/sdc3           12245       14946    21703815   83  Linux

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9354    75135973+  83  Linux
/dev/hda2            9355        9729     3012187+   5  Extended
/dev/hda5            9355        9729     3012156   82  Linux swap / Solaris
/code

My /boot/grub/menu.lst is as follows:
code
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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
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
# kopt=root=/dev/hda1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-26-amd64-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-amd64-generic root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-amd64-generic
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-amd64-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-amd64-generic root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-26-amd64-generic
boot

title		Ubuntu, kernel 2.6.15-23-amd64-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-amd64-generic root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-amd64-generic
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-amd64-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-amd64-generic root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-23-amd64-generic
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Microsoft Windows XP Professional
root		(hd3,0)
savedefault
makeactive
map		(hd0) (hd3)
map		(hd3) (hd0)
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc2.
title		SUSE Linux 10.1 (on /dev/sdc2)
root		(hd3,1)
kernel		/boot/vmlinuz root=/dev/sda2 vga=0x31a resume=/dev/hda5 splash=silent showopts 
initrd		/boot/initrd
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc2.
title		Failsafe -- SUSE Linux 10.1 (on /dev/sdc2)
root		(hd3,1)
kernel		/boot/vmlinuz root=/dev/sda2 vga=normal showopts ide=nodma apm=off acpi=off noresume edd=off 3 
initrd		/boot/initrd
savedefault
boot
/code

By looking at above, can anyone tell me how to fix the menu.lst so I can boot into Suse.  Thanks in advance.  All help greatly appreciated by this Linux newbie.

---

### Post by trogbot on 2006-07-28
Sorry about above post with attempt at code box...apparently I don't know how to do that; so plz ignore "code" & "/code" statements.

---

### Post by aarbear26 on 2006-07-28
there are some interesting things there that don't pan out.  If your drive is an ide why is it saying sdc?  thats saying it's a third sata drive, but when it boots it uses hd3 rather than sd3.  It also seems to see 3 windows installs.  How many windows installs do you have?

---

### Post by trogbot on 2006-07-28
You are correct with the IDE drive; it actually is another SATA drive.  As far as why 3 Win OS's show:  There is only 1 Win XP Pro install, but it is to a RAID Mirror'd setup on my 2 160GB Sata Drives; that's the reason for the first 2 Win OS's; I think:confused: As far as the 3rd Win OS:confused: :confused: , that's part of my problem I think; and why The SUSE OS is labeled "hd3" instead of "sd?", I cannot say, that's the problem.  I haven't touched menu.lst after my Ubuntu install, so I don't know where it got its info.  Does this help & is it correctable?

---

### Post by trogbot on 2006-07-28
BTW, here's what the device map shows.

code:
(hd0)	/dev/hda
(hd1)	/dev/sda
(hd2)	/dev/sdb
(hd3)	/dev/sdc
/code:

---

### Post by aarbear26 on 2006-07-30
ok, well thats getting somewhere, what happens exactly when you click on the third windows partition to boot or either Suse option.  That would give me some idea as to whats going on.  and by the way, to use the code function put a "[" in front of code or /code and a "]"behind it.  that will give you the desired result.

---

