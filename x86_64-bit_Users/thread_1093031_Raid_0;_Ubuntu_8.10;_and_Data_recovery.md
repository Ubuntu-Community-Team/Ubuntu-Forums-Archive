---
title: "Raid 0; Ubuntu 8.10; and Data recovery"
date: 2009-03-11
forum: x86 64-bit Users
---

### Post by ChadAragorn on 2009-03-11
Here's my story. I used to have an XP box with A8N-SLI mobo and 2 seagate 160 gb hdd's in raid 0. Somehow the controller drivers for my raid array got wiped and I was unable to get them back. So I bought a new 500gb drive and installed a fresh copy of XP on it only to get myself a copy of Ubuntu 8.10. Installed that and have it working great and am vastly impressed with Linux. Never used Linux before and I'm glad that I made the switch. 
   Now to get to the meat of my problem. There is tons of data on that raid array that I would like to recover. Is there any possible way to enable the raid controller in Ubuntu so that it will recognize the array? The array is still healthy and the data is not corrupted. If I could get my new system to realize it's there without having to format it, I could then access the data. Sorry for the novel, but I need some help and it warrants an explanation. Thanks in advance.

---

### Post by klemens on 2009-03-11
raid 0 in linux simply is a big issue when it comes to onboard solutions.

you probably will have bigger chance to get this done in windows.

by googling a bit a got this [http://forums.whirlpool.net.au/forum-replies-archive.cfm/482749.html]("http://forums.whirlpool.net.au/forum-replies-archive.cfm/482749.html")
btw i didn't try this so @ proper risk.

---

### Post by ChadAragorn on 2009-03-11
Here is some more data that may be helpful to the situation. I don't know what to make of it though.

chad@chad-desktop:~$ sudo dmraid -ay
RAID set "nvidia_defgigbi" already active
RAID set "nvidia_defgigbi1" already active
chad@chad-desktop:~$ sudo dmraid -r
/dev/sdc: nvidia, "nvidia_defgigbi", stripe, ok, 312581806 sectors, data@ 0
/dev/sdb: nvidia, "nvidia_defgigbi", stripe, ok, 312581806 sectors, data@ 0
chad@chad-desktop:~$ sudo dmraid -b
/dev/sdd:     78165360 total, "DWW-AM1D"
/dev/sdc:    312581808 total, "WD-WCANM2688693"
/dev/sdb:    312581808 total, "WD-WCANM2690401"
/dev/sda:    976773168 total, "WD-WCASY3437044"
chad@chad-desktop:~$ sudo dmraid -s
*** Active Set
name   : nvidia_defgigbi
size   : 625163520
stride : 128
type   : stripe
status : ok
subsets: 0
devs   : 2
spares : 0
chad@chad-desktop:~$ 

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => No known boot loader is installed in the MBR of /dev/sdc
 => Windows is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       
    Boot sector type:  Windows XP
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0f52e239

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   964,719,314   964,719,252  83 Linux
/dev/sda2         964,719,315   976,768,064    12,048,750   5 Extended
/dev/sda5         964,719,378   976,768,064    12,048,687  82 Linux swap / Solaris


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xffffffff

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   625,137,344   625,137,282   7 HPFS/NTFS

/dev/sdb1 ends after the last sector of /dev/sdb

Drive sdc: _____________________________________________________________________

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

Invalid MBR Signature found


Drive sdd: _____________________________________________________________________

Disk /dev/sdd: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xefcddfd9

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             63    78,140,159    78,140,097   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="05d7c628-c1a7-40b3-9aa8-9a9d4dca8486" TYPE="ext3" 
/dev/sda5: UUID="c8e7c9d5-d443-44e3-beb9-70d5b6e61a72" TYPE="swap" 
/dev/mapper/nvidia_defgigbi1: UUID="CC5C77055C76E99A" TYPE="ntfs" 
/dev/sdd1: UUID="BA4855034854BFB5" LABEL="External 2" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/chad/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=chad)
/dev/sdd1 on /media/External 2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

=========================== sda1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=05d7c628-c1a7-40b3-9aa8-9a9d4dca8486 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=05d7c628-c1a7-40b3-9aa8-9a9d4dca8486

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
uuid		05d7c628-c1a7-40b3-9aa8-9a9d4dca8486
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=05d7c628-c1a7-40b3-9aa8-9a9d4dca8486 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		05d7c628-c1a7-40b3-9aa8-9a9d4dca8486
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=05d7c628-c1a7-40b3-9aa8-9a9d4dca8486 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		05d7c628-c1a7-40b3-9aa8-9a9d4dca8486
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=05d7c628-c1a7-40b3-9aa8-9a9d4dca8486 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		05d7c628-c1a7-40b3-9aa8-9a9d4dca8486
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=05d7c628-c1a7-40b3-9aa8-9a9d4dca8486 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		05d7c628-c1a7-40b3-9aa8-9a9d4dca8486
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdd1
title		Microsoft Windows XP Home Edition
root		(hd3,0)
savedefault
makeactive
map		(hd0) (hd3)
map		(hd3) (hd0)
chainloader	+1


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=05d7c628-c1a7-40b3-9aa8-9a9d4dca8486 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=c8e7c9d5-d443-44e3-beb9-70d5b6e61a72 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


 176.5GB: boot/grub/menu.lst
 176.5GB: boot/grub/stage2
 176.5GB: boot/initrd.img-2.6.27-11-generic
 176.6GB: boot/initrd.img-2.6.27-7-generic
 176.5GB: boot/vmlinuz-2.6.27-11-generic
 176.5GB: boot/vmlinuz-2.6.27-7-generic
 176.5GB: initrd.img
 176.6GB: initrd.img.old
 176.5GB: vmlinuz
 176.5GB: vmlinuz.old

================================ sdd1/boot.ini: ================================

[boot loader]

timeout=1

default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect


=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdc

00000000  01 01 00 00 00 00 00 03  00 00 00 00 00 03 14 00  |................|
00000010  01 00 11 00 01 01 00 00  00 00 00 05 14 00 00 00  |................|
00000020  01 02 00 00 00 00 00 05  20 00 00 00 20 02 00 00  |........ ... ...|
00000030  01 01 00 00 00 00 00 05  12 00 00 00 00 00 00 00  |................|
00000040  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000050  b8 01 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000060  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000070  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000090  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000100  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000110  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000120  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000130  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000140  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000160  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000200


=============================== StdErr Messages: ===============================

boot_info_script.txt: line 1043: [: =: unary operator expected

---

### Post by ronparent on 2009-03-11
Yes and no. Being a noob to linux myself I found a work around that is maybe a bit cumbersome but works.

I used a downloaded program called dmraid which when run mapped all my windows raid0 drives to a directory called /dev/mapper. To 'see' a drive so that it can be accessed by nautilus (the file browser) I placed statements in fstab to automatically map it on boot. The /etc/fstab statement I used was of a form as follows:

#/dev/sdb nvidia_aebhdfib7 f:\PICTURES
/dev/mapper/nvidia_aebhdfib7 /media/WinXP-f:PICTURES	auto	relatime	0	1

Where the line preceded by the # symbol designates an explanatory statement (to identify windows drive that you are addressing). the following line represents the statement that actually designates the linux file system location to which my f:\PICTURES windows drive on the raid0 was mapped. '/media' already existed, but I had to manually created a subdirectory which I called '/WinXP-f:PICTURES' into which my referenced windows drive was mounted. The windows drive you want to mount can be either ntfs or fat32. Incidently, you need to do all these things as sudo. I belive that these proceedure, incidently, can be used to access individual directories so that you can access as much or as little as you want. In my case I am set up to dual boot either WinXP or Ubuntu (another involved topic). Be aware that his process only allows you to view (or work on) the windows files, it doesn't physically move the files. If you want to permantly move them, you have to physically copy them to somewhere in your linux file system (not neccessaqry unless you plan to reformat the location).

Good luck. Drop me a note if you need more info.

---

### Post by ronparent on 2009-03-11
ChadAragorn

Please excuse the smilely faces, not meant where inserted. Apparently inadvertently placed by combination of symbols used in my post. I would try to explain, but we would probably only get more smilely faces!

---

### Post by LaughingBubba on 2009-04-26
Hi RonParent, I'm planning to install Kubuntu 9.04 (64 bit) on my new pc which already has XP and Raid-0 ... Did you use the alernate iso or does the standard iso come with Raid controllers?

Also, did you have any dramas whilst installing?

PS: I want to dual boot but also keep the raid-0. 

Cheers,
LB

PC Spec: i7-920 CPU, Asus P6T Mother board, 6 GB RAM, nVidia GTX295

---

