---
title: "GRUB error 22"
date: 2008-01-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by cryptlordgr on 2008-01-28
Hi 
First of all i would like to thank a long time ago the whole community for their helpful posts but now i can't find my solution. I've installed Kubuntu 7.10 and i hadn't many problems.
In my first hard disk drive which is Sata2 i have only the partitions for linux which work perfect whoever when i put the other 2 hard disk drives which are also sata2 and try to boot up i face the error 22 on GRUB. In this two hard disk drive i have NTFS partitions.
Thanks in advance

---

### Post by jeffus_il on 2008-01-28
Do you always boot from the same bios harddrive?
Does you boot work correctly when you choose Ubuntu on the grub menu and does not work when you boot from windows?

---

### Post by cryptlordgr on 2008-01-28
Sorry for my English but i can totally understand your first question but i do not change anything in the bios of my motherboard.

For the second question my Grub boots up fine when i have connected only the first hard disk which is the one with linux. But when i put the other hard disk which has NOT windows inside but there are just partitions of NTFS it shows the eroor 22 in the GRUB and it doesn't reposnd
thanks for your fast reply

---

### Post by jeffus_il on 2008-01-28
Grub need to be written to the boot sector of the disk you boot from, if you change the hard disk setup on your machine, and there is no grub on it, it won't work.

---

### Post by cryptlordgr on 2008-01-29
so how can i resolve this problem? But the GRUB is one the first hard disk drive so i think nothing changes

---

### Post by jeffus_il on 2008-01-29
Ok. can you post your /boot/grub/menu.lst

---

### Post by cryptlordgr on 2008-01-29
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=0fff311a-5a0e-4c05-b01b-624f55c8fb20 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=0fff311a-5a0e-4c05-b01b-624f55c8fb20 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=0fff311a-5a0e-4c05-b01b-624f55c8fb20 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by jeffus_il on 2008-01-29
Looks fine, It is possible that the additional disks are changing you disk id's (sda, sdb, sdc etc.) Make sure that your original Linux disk is connected to the first sata socket on the motherboard and the new disks to the second and third, if its not clear on the board, use your manual. This should solve your problem.

---

### Post by cryptlordgr on 2008-01-29
The linux disk is in the first sata controller :S
I will try different combination of the connections of the sata
And thanks for all your help

---

### Post by Yellow Pasque on 2008-01-29
Use these commands to figure out which filesystem corresponds to each disk and uuid.
```
cd /dev/disk/by-uuid; ls -l
```
shows:
> lrwxrwxrwx 1 root root 10 2008-01-29 01:01 196c7c15-ca90-492f-a140-1957cfb65bfe -> ../../sda5
lrwxrwxrwx 1 root root 10 2008-01-29 01:01 **7a119114-4fd7-4ee0-922f-a7d03a5b4b3e -> ../../sda1**
&
```
sudo lshw -businfo -C disk
```
shows:
> Bus info          Device       Class       Description
======================================================
scsi@0:0.0.0      /dev/sda     disk        298GB SAMSUNG HD321KJ
scsi@1:0.0.0      /dev/cdrom1  disk        CDDVDW SH-S203B

---

### Post by cryptlordgr on 2008-01-30
I can't boot with the other hard disk drives so the results or these are 

lrwxrwxrwx 1 root root 10 2008-01-29 14:49 0fff311a-5a0e-4c05-b01b-624f55c8fb20 -> ../../sda1
lrwxrwxrwx 1 root root 10 2008-01-29 14:49 5dd839fd-10d6-4b88-9345-47ad1778daec -> ../../sda5

Bus info          Device     Class       Description
====================================================
ide@0.0           /dev/hda   disk        CD-W516EB
scsi@2:0.0.0      /dev/sda   disk        149GB WDC WD1600JS-00M

can you explain all these because i'm a little noob?

---

### Post by jeffus_il on 2008-01-30
Turn off your machine
Hook up all of your disks.
Boot the livecd
Open a terminal
run ```
sudo parted
```
then ```
print all
```
post the output
OK?!

---

### Post by Yellow Pasque on 2008-01-30
> **cryptlordgr said:**
> I can't boot with the other hard disk drives so the results or these are 

lrwxrwxrwx 1 root root 10 2008-01-29 14:49 0fff311a-5a0e-4c05-b01b-624f55c8fb20 -> ../../sda1
lrwxrwxrwx 1 root root 10 2008-01-29 14:49 5dd839fd-10d6-4b88-9345-47ad1778daec -> ../../sda5

Bus info          Device     Class       Description
====================================================
ide@0.0           /dev/hda   disk        CD-W516EB
scsi@2:0.0.0      /dev/sda   disk        149GB WDC WD1600JS-00M

can you explain all these because i'm a little noob?

Good, now post your /boot/grub/menu.lst and /etc/fstab files and we will change them to use the UUID instead of the /dev path.

---

### Post by cryptlordgr on 2008-01-30
Thanks for all your help. I found the solution for my problem. In my case the problem was the sata controller cause even if it was numbered 1,2,3 the slots didn't correspond to their real value of the control :lolflag:so after canging sometimes my satas i saw the difference and understood which was the first so now i have mount them correctly and i'm fine :D

Thanks for all your help

An admin can close the post

---

