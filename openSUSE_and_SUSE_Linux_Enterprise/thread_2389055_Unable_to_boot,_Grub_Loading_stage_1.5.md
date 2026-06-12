---
title: "Unable to boot, Grub Loading stage 1.5"
date: 2018-04-10
forum: openSUSE and SUSE Linux Enterprise
---

### Post by bikrumlinux on 2018-04-10
Hi,

I am new on Linux system, last time I clone one of the systems to new HDD, when I try to boot from new HDD it shows error like 

Grub"GRUB Loading State 1.5

GRUB LOADING, please wait...
graphics file "(hd0,0)/boot/message"missing, press a key to continue.

You help will be much more appreciated.


I'd tried with boot repair and hdd status is like this


```
Boot Info Script 8f991e4 + Boot-Repair extra info [Boot-Info 25oct2017]




============================= Boot Info Summary: ===============================


=> Syslinux MBR (5.00 and higher) is installed in the MBR of /dev/sda.
=> Syslinux MBR (5.00 and higher) is installed in the MBR of /dev/sdb.


sda1: __________________________________________________________________________


File system: ext3
Boot sector type: -
Boot sector info: 
Operating System: 
Welcome to SuSE Linux 8.2 (i586) - Kernel ().
Boot files: /boot/grub/menu.lst /etc/fstab /etc/lilo.conf /boot/map


sda2: __________________________________________________________________________


File system: swap
Boot sector type: -
Boot sector info: 


sda3: __________________________________________________________________________


File system: ext3
Boot sector type: -
Boot sector info: 
Operating System: 
Boot files: 


sda4: __________________________________________________________________________


File system: ext3
Boot sector type: -
Boot sector info: 
Operating System: 
Boot files: 


sdb1: __________________________________________________________________________


File system: vfat
Boot sector type: SYSLINUX 6.03 2014-10-06................................................2....0............A20 gate n
Boot sector info: Syslinux looks at sector 17184 of /dev/sdb1 for its 
second stage. SYSLINUX is installed in the /multiboot 
directory. No errors found in the Boot Parameter Block.
Operating System: 
Boot files: /multiboot/boot-repair-disk-32bit/casper/vmlinuz.efi 
/multiboot/boot-repair-disk-32bit/EFI/BOOT/bootia32.efi
                        
/multiboot/kali-linux-light-2018.1-i386/efi/boot/bootia
32.efi 
/multiboot/kali-linux-light-2018.1-i386/efi/boot/bootx6
4.efi


============================ Drive/Partition Info: =============================


Drive: sda _____________________________________________________________________
Disk /dev/sda: 74.5 GiB, 80030957056 bytes, 156310463 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos


Partition Boot Start Sector End Sector # of Sectors Id System


/dev/sda1 * 63 4,096,574 4,096,512 83 Linux
/dev/sda2 4,096,575 5,156,864 1,060,290 82 Linux swap / Solaris
/dev/sda3 5,156,865 9,253,439 4,096,575 83 Linux
/dev/sda4 9,253,440 78,156,224 68,902,785 83 Linux




Drive: sdb _____________________________________________________________________
Disk /dev/sdb: 3.8 GiB, 4037017600 bytes, 7884800 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos


Partition Boot Start Sector End Sector # of Sectors Id System


/dev/sdb1 * 63 4,128,704 4,128,642 e W95 FAT16 (LBA)




"blkid" output: ________________________________________________________________


Device UUID TYPE LABEL


/dev/loop0 squashfs 
/dev/sda1 1c40d2c9-6fd9-455b-8fc1-01ff398b86ec ext3 
/dev/sda2 swap 
/dev/sda3 92683732-b0de-4619-a856-1c5b14231184 ext3 
/dev/sda4 a8c4347a-74a9-459c-8fc8-a79f232c2399 ext3 
/dev/sdb1 4877-7912 vfat MULTIBOOT
/dev/zram0 078e1739-c88f-4092-b3a7-68e496b9be20 swap 


========================= "ls -l /dev/disk/by-id" output: ======================


total 0
lrwxrwxrwx 1 root root 9 Oct 5 12:15 ata-HL-DT-STDVD-RAM_GH22NP20 -> ../../sr0
lrwxrwxrwx 1 root root 9 Oct 5 12:22 ata-WDC_WD800JD-08MSA1_WD-WMAM9YD90190 -> ../../sda
lrwxrwxrwx 1 root root 10 Oct 5 12:22 ata-WDC_WD800JD-08MSA1_WD-WMAM9YD90190-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Oct 5 12:22 ata-WDC_WD800JD-08MSA1_WD-WMAM9YD90190-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Oct 5 12:22 ata-WDC_WD800JD-08MSA1_WD-WMAM9YD90190-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 Oct 5 12:22 ata-WDC_WD800JD-08MSA1_WD-WMAM9YD90190-part4 -> ../../sda4
lrwxrwxrwx 1 root root 9 Oct 5 12:22 usb-Generic_Flash_Disk_B1B82403-0:0 -> ../../sdb
lrwxrwxrwx 1 root root 10 Oct 5 12:22 usb-Generic_Flash_Disk_B1B82403-0:0-part1 -> ../../sdb1
lrwxrwxrwx 1 root root 9 Oct 5 12:15 usb-IC_USB_Storage-CFC_20020509145305401-0:0 -> ../../sdc
lrwxrwxrwx 1 root root 9 Oct 5 12:15 usb-IC_USB_Storage-MMC_20020509145305401-0:2 -> ../../sde
lrwxrwxrwx 1 root root 9 Oct 5 12:15 usb-IC_USB_Storage-MSC_20020509145305401-0:3 -> ../../sdf
lrwxrwxrwx 1 root root 9 Oct 5 12:15 usb-IC_USB_Storage-SMC_20020509145305401-0:1 -> ../../sdd


================================ Mount points: =================================


Device Mount_Point Type Options


/dev/loop0 /rofs squashfs (ro,noatime)
/dev/sdb1 /cdrom vfat (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)




=========================== sda1/boot/grub/menu.lst: ===========================


--------------------------------------------------------------------------------
color white/blue black/light-gray
default 0
timeout 1
gfxmenu (hd0,0)/boot/message


title Amacs
kernel (hd0,0)/boot/lin-2.4.27 root=/dev/hda1 vga=0x317 hdc=ide-scsi splash=silent showopts splash=silent showopts acpi=noirq
initrd (hd0,0)/boot/initrd-2.4.27
--------------------------------------------------------------------------------


=============================== sda1/etc/fstab: ================================


--------------------------------------------------------------------------------
/dev/hda1    /    ext3    defaults 1 2
/dev/hda4    /data    ext3    defaults 1 2
/dev/sr0    /cdrom    auto    ro,noauto,user,exec 0 0
devpts        /dev/pts    devpts    defaults 0 0
/dev/fd0    /floppy    auto    noauto,user,sync 0 0
proc        /proc    proc    defaults 0 0
usbdevfs    /proc/bus/usb    usbdevfs    noauto 0 0
/dev/cdrom /media/cdrom auto ro,noauto,user,exec 0 0
/dev/sda1 /media/sda1 auto ro,noauto,user,exec 0 0
/dev/fd0 /media/floppy auto ro,noauto,user,exec 0 0
/dev/hda2    swap    swap    pri=42 0 0
/dev/sde1 /media/sde1 auto noauto,user,exec 0 0 #HOTPLUG B3Fu.nXToF54Z8R5
#UUID=a8c4347a-74a9-459c-8fc8-a79f232c2399    /boot    ext3    defaults    0    2
#UUID=a8c4347a-74a9-459c-8fc8-a79f232c2399    /boot    ext3    defaults    0    2
UUID=a8c4347a-74a9-459c-8fc8-a79f232c2399    /boot    ext3    defaults    0    2
--------------------------------------------------------------------------------


============================= sda1/etc/lilo.conf: ==============================


--------------------------------------------------------------------------------
boot    = /dev/hda
read-only
menu-scheme = Wg:kw:Wg:Wg
lba32
prompt
timeout    = 120
message    = /boot/message


image = /boot/vmlinuz
label = Linux
root = /dev/hda1
vga = 791
initrd = /boot/initrd
append = " hdc=ide-scsi acpi=off"
--------------------------------------------------------------------------------


=================== sda1: Location of files loaded by Grub: ====================


GiB - GB File Fragment(s)


1.002593517 = 1.076526592 boot/grub/menu.lst 1
1.002418041 = 1.076338176 boot/grub/stage2 2
0.753196239 = 0.808738304 boot/vmlinuz.shipped 2
0.755225658 = 0.810917376 boot/initrd-2.4.27 2
0.753718853 = 0.809299456 boot/initrd.shipped 2


========= Devices which don't seem to have a corresponding hard drive: =========


sdc sdd sde sdf 




ADDITIONAL INFORMATION :
=================== log of boot-info 20171005_1222 ===================
boot-info version : 4ppa62
boot-sav version : 4ppa62
boot-sav-extra version : 4ppa62
glade2script version : 3.2.3~ppa4
boot-info is executed in live-session (Boot-Repair-Disk 32bit 1oct2017, zesty, Ubuntu, i686)
CPU op-mode(s): 32-bit
BOOT_IMAGE=/multiboot/boot-repair-disk-32bit/casper/vmlinuz file=/cdrom/multiboot/boot-repair-disk-32bit/preseed/lubuntu.seed boot=casper cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid live-media-path=/multiboot/boot-repair-disk-32bit/casper/ initrd=/multiboot/boot-repair-disk-32bit/casper/initrd.lz quiet splash --
ls: cannot access '/home/usr/.config': No such file or directory


=================== os-prober:
/dev/sda1:SuSE Linux 8.2 (i586):SuSE:linux


=================== blkid:
/dev/sda1: UUID="1c40d2c9-6fd9-455b-8fc1-01ff398b86ec" SEC_TYPE="ext2" TYPE="ext3" PARTUUID="000dfc89-01"
/dev/sda3: UUID="92683732-b0de-4619-a856-1c5b14231184" SEC_TYPE="ext2" TYPE="ext3" PARTUUID="000dfc89-03"
/dev/sda4: UUID="a8c4347a-74a9-459c-8fc8-a79f232c2399" SEC_TYPE="ext2" TYPE="ext3" PARTUUID="000dfc89-04"
/dev/sdb1: SEC_TYPE="msdos" LABEL="MULTIBOOT" UUID="4877-7912" TYPE="vfat" PARTUUID="bc65391c-01"
/dev/loop0: TYPE="squashfs"
/dev/sda2: TYPE="swap" PARTUUID="000dfc89-02"
/dev/zram0: UUID="078e1739-c88f-4092-b3a7-68e496b9be20" TYPE="swap"




1 disks with OS, 1 OS : 1 Linux, 0 MacOS, 0 Windows, 0 unknown type OS.


/boot detected in the fstab of sda1: UUID=a8c4347a-74a9-459c-8fc8-a79f232c2399     (sda4)
/mnt/boot-sav/sda1/boot/grub/menu.lst detected


=================== UEFI/Legacy mode:
This live-session is not EFI-compatible.
SecureBoot maybe enabled.




=================== PARTITIONS & DISKS:
sda1    : sda,    not-sepboot,    no-grubenv    grub1,    no-docgrub,    no-update-grub,    32,    with-boot,    is-os,    not--efi--part,    fstab-has-goodBOOT,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    not-far,    notbiosboot, /mnt/boot-sav/sda1.
sda3    : sda,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    notbiosboot, /mnt/boot-sav/sda3.
sda4    : sda,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    notbiosboot, /mnt/boot-sav/sda4.


sda    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    not-mmc, has-os,    63 sectors * 512 bytes




=================== parted -lm:


BYT;
/dev/sda:80.0GB:scsi:512:512:msdos:ATA WDC WD800JD-08MS:;
1:32.3kB:2097MB:2097MB:ext3::boot;
2:2097MB:2640MB:543MB:linux-swap(v1)::;
3:2640MB:4738MB:2097MB:ext3::;
4:4738MB:40.0GB:35.3GB:ext3::;


BYT;
/dev/sdb:4037MB:scsi:512:512:msdos:Generic Flash Disk:;
1:32.3kB:2114MB:2114MB:fat16::boot, lba;


BYT;
/dev/zram0:1587MB:unknown:4096:4096:loop:Unknown:;
1:0.00B:1587MB:1587MB:linux-swap(v1)::;


=================== lsblk:
KNAME TYPE FSTYPE SIZE LABEL
loop0 loop squashfs 642.9M
sda disk 74.5G
sda1 part ext3 2G
sda2 part swap 517.7M
sda3 part ext3 2G
sda4 part ext3 32.9G
sdb disk 3.8G
sdb1 part vfat 2G MULTIBOOT
sr0 rom 1024M
zram0 disk 1.5G


KNAME ROTA RO RM STATE MOUNTPOINT
loop0 1 1 0 /rofs
sda 1 0 0 running
sda1 1 0 0 /mnt/boot-sav/sda1
sda2 1 0 0 [SWAP]
sda3 1 0 0 /mnt/boot-sav/sda3
sda4 1 0 0 /mnt/boot-sav/sda4
sdb 1 0 1 running
sdb1 1 0 1 /cdrom
sr0 1 0 1 running
zram0 0 0 0 [SWAP]




=================== mount:
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=1524216k,nr_inodes=204042,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=309904k,mode=755)
/dev/sdb1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
/cow on / type overlay (rw,relatime,lowerdir=//filesystem.squashfs,upperdir=/cow/upper,workdir=/cow/work)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/unified type cgroup2 (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/rdma type cgroup (rw,nosuid,nodev,noexec,relatime,rdma)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=29,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=13462)
mqueue on /dev/mqueue type mqueue (rw,relatime)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime,pagesize=2M)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
configfs on /sys/kernel/config type configfs (rw,relatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev,relatime)
tmpfs on /run/user/999 type tmpfs (rw,nosuid,nodev,relatime,size=309904k,mode=700,uid=999,gid=999)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=999,group_id=999)
/dev/sda1 on /mnt/boot-sav/sda1 type ext3 (rw,relatime,data=ordered)
/dev/sda3 on /mnt/boot-sav/sda3 type ext3 (rw,relatime,data=ordered)
/dev/sda4 on /mnt/boot-sav/sda4 type ext3 (rw,relatime,data=ordered)




=================== ls:
/sys/block/sda (filtered): alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro sda1 sda2 sda3 sda4 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered): alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/sys/block/sdc (filtered): alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdd (filtered): alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sde (filtered): alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdf (filtered): alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered): alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered): agpgart autofs block bsg btrfs-control bus cdrom cdrw char console core cpu_dma_latency cuse disk dri dvd dvdrw ecryptfs fb0 fd full fuse hidraw0 hidraw1 hidraw2 hpet hugepages hwrng i2c-0 i2c-1 i2c-2 i2c-3 i2c-4 i2c-5 initctl input kmsg lightnvm log mapper mcelog mem memory_bandwidth mqueue net network_latency network_throughput null parport0 port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda3 sda4 sdb sdb1 sdc sdd sde sdf sg0 sg1 sg2 sg3 sg4 sg5 sg6 shm snapshot snd sr0 stderr stdin stdout uhid uinput urandom userio vfio vga_arbiter vhci vhost-net vhost-vsock zero
ls /dev/mapper: control


=================== df -Th:


Filesystem Type Size Used Avail Use% Mounted on
udev devtmpfs 1.5G 0 1.5G 0% /dev
tmpfs tmpfs 303M 5.0M 298M 2% /run
/dev/sdb1 vfat 2.0G 1.7G 369M 82% /cdrom
/dev/loop0 squashfs 643M 643M 0 100% /rofs
/cow overlay 1.5G 4.2M 1.5G 1% /
tmpfs tmpfs 1.5G 0 1.5G 0% /dev/shm
tmpfs tmpfs 5.0M 4.0K 5.0M 1% /run/lock
tmpfs tmpfs 1.5G 0 1.5G 0% /sys/fs/cgroup
tmpfs tmpfs 1.5G 164K 1.5G 1% /tmp
tmpfs tmpfs 303M 4.0K 303M 1% /run/user/999
/dev/sda1 ext3 1.9G 1.4G 411M 78% /mnt/boot-sav/sda1
/dev/sda3 ext3 1.9G 60K 1.8G 1% /mnt/boot-sav/sda3
/dev/sda4 ext3 33G 24G 7.2G 77% /mnt/boot-sav/sda4


=================== fdisk -l:
Disk /dev/loop0: 642.9 MiB, 674103296 bytes, 1316608 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes








Disk /dev/sda: 74.5 GiB, 80030957056 bytes, 156310463 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x000dfc89


Device Boot Start End Sectors Size Id Type
/dev/sda1 * 63 4096574 4096512 2G 83 Linux
/dev/sda2 4096575 5156864 1060290 517.7M 82 Linux swap / Solaris
/dev/sda3 5156865 9253439 4096575 2G 83 Linux
/dev/sda4 9253440 78156224 68902785 32.9G 83 Linux




Disk /dev/sdb: 3.8 GiB, 4037017600 bytes, 7884800 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xbc65391c


Device Boot Start End Sectors Size Id Type
/dev/sdb1 * 63 4128704 4128642 2G e W95 FAT16 (LBA)




Disk /dev/zram0: 1.5 GiB, 1586708480 bytes, 387380 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Error: no package mgt for purge. Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]
Error: no package mgt for purge. Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]
Error: no package mgt for purge. Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]
Error: no package mgt for purge. Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]
Error: no package mgt for purge. Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]
Error: no package mgt for purge. Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]
Error: no package mgt for purge. Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]
Error: no package mgt for purge. Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]




=================== Suggested repair
The default repair of the Boot-Repair utility would reinstall the grub2 of sda1 into the MBR of sda.
Additional repair would be performed: unhide-bootmenu-10s




=================== User settings
The settings chosen by the user will not act on the boot.
```

---

### Post by oldfred on 2018-04-10
Moved to other OS since not Ubuntu.

Best not to clone Linux, but just do a new install and restore /home, apps and perhaps some other settings or files that are in your normal backup. Also good way to confirm your backup procedure is valid. And you still have old drive to fall back on.

If cloned, you cannot have both drives connected at same time on reboot as you have duplicated UUIDs.

Stage 1.5 is from grub now grub legacy, not grub2.
Boot-Repair only can fix grub2 on current version installs, so it can access repository. Do not know about SuSE.

Ubuntu converted from grub to grub2 with version 9.10 or almost 9 years ago.

---

