---
title: "Gusty Woes"
date: 2007-10-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by chrism66 on 2007-10-10
Have poted on the gusty forum but have not received much help. I was wondering if any one on this forum may have a fix. Ever since the upgraded to the 2.6.22-** kernels I can not boot in normal or recovery mode. Also none of the live cd's work for gusty, (I did an upgraded via the net).  I get the following message's before the Ubuntu splash screen come on:

[COLOR="Red"]"No filesystem could mount root, tried cramfs"
"Kernel Panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)"[/COLOR]

Here are all the commands that I have run from what I could find on the forums to correct this:

[COLOR="Red"]Apt-get update, apt-get upgrade, apt-get dist-upgrade, sudo dpkg --configure -a, change the root to look like this root=/dev/hda1 from that UUID stuff grub boot menu, sudo mkinitramfs -o /boot/initrd.img-2.6.22-13-generic 2.6.22-13-generic.[/COLOR]

Finally here are some files that may help:

Here is etc/fstab:

[COLOR="DarkGreen"]# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/hda1
UUID=74da83bd-a4bc-4e98-8cd1-ffb04cbc2039 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda2
UUID=5db8676e-3b8a-4fde-9218-468b50f696e5 /home ext3 defaults 0 2
# /dev/hda3
UUID=e6729450-7fd8-4652-bf11-85c492df6591 none swap sw 0 0
/dev/hdd /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdc /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0[/COLOR]

Aslo here is:

[COLOR="Green"]sudo fdisk -l /dev/hda1

Disk /dev/hda1: 10.7 GB, 10733958144 bytes
255 heads, 63 sectors/track, 1304 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/hda1 doesn't contain a valid partition table[/COLOR]

Any help  would be greatly appreciated!

Chris

---

### Post by dabl on 2007-10-10
Any chance that your filesystem is full?  It's a ```
du -
``` command -- I'm away from my system and don't remember the options, but "man du" will bring them up for you.  A full filesystem will cause a kernel panic upon booting.

Also, ```
blkid
``` output would be interesting, just to make sure that nothing funny has happened with the correlation of /dev/sd# devices to UUIDs.

Then it would be good to see the "Debian Automagic Kernels" section of your /boot/grub/menu.lst file, to make sure that it is a match to the /etc/fstab table for disk ID where the kernel is located.

Finally "no valid partition table" is a serious problem if it's true.  Can you run gparted -- does it show the drive and partitions correctly? :)

---

### Post by Kilz on 2007-10-10
I would like to know the boot parameters. I wonder where its looking (what partition). There may have been an error in writing the /boot/grub/menu.list

---

### Post by chrism66 on 2007-10-10
All right: Could not figure out the du but the in the System monitor it says that I have only used 46% of the disc space.

Here is a copy of blkid:

/dev/hda1: UUID="74da83bd-a4bc-4e98-8cd1-ffb04cbc2039" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hda2: UUID="5db8676e-3b8a-4fde-9218-468b50f696e5" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hda3: TYPE="swap" UUID="e6729450-7fd8-4652-bf11-85c492df6591"

---

### Post by chrism66 on 2007-10-10
Here is a copy of /boot/grub/menu.lst

[PHP]# menu.lst - See: grub(8), info grub, update-grub(8)
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
timeout		3

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
# kopt=root=UUID=74da83bd-a4bc-4e98-8cd1-ffb04cbc2039 ro

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=74da83bd-a4bc-4e98-8cd1-ffb04cbc2039 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=74da83bd-a4bc-4e98-8cd1-ffb04cbc2039 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, kernel 2.6.22-13-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-13-generic root=UUID=74da83bd-a4bc-4e98-8cd1-ffb04cbc2039 ro quiet splash
initrd		/boot/initrd.img-2.6.22-13-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-13-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-13-generic root=UUID=74da83bd-a4bc-4e98-8cd1-ffb04cbc2039 ro single
initrd		/boot/initrd.img-2.6.22-13-generic

title		Ubuntu 7.10, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=74da83bd-a4bc-4e98-8cd1-ffb04cbc2039 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=74da83bd-a4bc-4e98-8cd1-ffb04cbc2039 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 7.10, kernel 2.6.20-9-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-9-generic root=UUID=74da83bd-a4bc-4e98-8cd1-ffb04cbc2039 ro quiet splash
initrd		/boot/initrd.img-2.6.20-9-generic
quiet

title		Ubuntu 7.10, kernel 2.6.20-9-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-9-generic root=UUID=74da83bd-a4bc-4e98-8cd1-ffb04cbc2039 ro single
initrd		/boot/initrd.img-2.6.20-9-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST[/PHP]

---

### Post by dabl on 2007-10-10
It all looks correct (the fstab and menu.lst files) -- which I think translates to "bad news -- something wrong with hdd partition table".

:(

Did you try to run gparted and see if it brings up the disk partitions correctly?

Is there any reason to suspect that an "unmanaged event" might have caused that hard drive to experience a sudden/momentary loss of power, or anything like that?

I don't know of any "on the fly" remedies for a messed up disk partition table, unfortunately.  I think the remedy starts with a pile of empty DVDs ....   :(

---

### Post by chrism66 on 2007-10-10
gparted is bringing up the partitions correctly. I am cureently using the 2.6.20-16-generic kernel and installed the nvidia drivers via Envy so I have a working system again Just looks like I will not be using any of the latest kernels maybe something will come down the road that works. I can only hope. Cant think of any events that would effected the hard drive.

---

### Post by chrism66 on 2007-10-11
I just used the Gparted live cd and there is no errors on the root partition. Do not know if that means any thing. 

Also I was not thinking but the 2.6.20-16 kernel was from my Feisty install. So I would assume that I did have a working 2.6.22-** kernel working at one time. I upgraded to Gutsy Beta on September 29, and the problem started on 10/3.

---

### Post by chrism66 on 2007-10-13
All right I fixed the partition tables on /dev/hda1 and /de/hda2 using the gparted live cd and fdisk. I am no getting the no valid partition table message. However I am still unable to boot the 2.6.22-** kernels or the Live CD's. Can I assume now that it is a hardware compatibility issue?

---

### Post by Kilz on 2007-10-14
> **chrism66 said:**
> All right I fixed the partition tables on /dev/hda1 and /de/hda2 using the gparted live cd and fdisk. I am no getting the no valid partition table message. However I am still unable to boot the 2.6.22-** kernels or the Live CD's. Can I assume now that it is a hardware compatibility issue?

Something is wrong, can you boot other kernels?

---

### Post by chrism66 on 2007-10-14
Yes I can use 2.6.20-16-generic which came from my old feisty install

---

### Post by tonywhelan on 2007-10-15
> **chrism66 said:**
> All right I fixed the partition tables on /dev/hda1 and /de/hda2 using the gparted live cd and fdisk. I am no getting the no valid partition table message. However I am still unable to boot the 2.6.22-** kernels or the Live CD's. Can I assume now that it is a hardware compatibility issue?

Not sure if you've checked this but ...

On my "test" machine (its not my 64bit machine) I could not get Live CDs to run properly till I removed a RAM chip and replaced it with one that more closely matched what was in there already. Seems Linux is rather intolerant of mixing RAM from different makers.

I also had trouble booting because of a spare Hard Disk that I had plugged into the IDE but without power as I wasn't using it. For some reason it upset things big time. Unplugged the IDE cable from the unused drive, and the boot worked fine.

---

### Post by chrism66 on 2007-10-15
Thanks for hint Tony! However I tried the memory when the problem first started.

---

### Post by chrism66 on 2007-10-18
> **Kilz said:**
> Something is wrong, can you boot other kernels?

Yes can boot 2.6.20-16-generic.

---

### Post by Kilz on 2007-10-18
> **chrism66 said:**
> Yes can boot 2.6.20-16-generic.

Have you tried to completely remove the non working kernel, purge the apt cache and then reinstall?

---

### Post by athos on 2007-10-18
Try to remove the evms package with "apt-get remove evms";
I've had a problem entering on gnome right after an update to the gutsy RC, the system informed that there was no home dir (the system couldn't find it), and after the removal of the package everything returned to normal; maybe your problem is the same. The problem ocurred with the new kernel, using the old one didn't gave the error.

---

### Post by chrism66 on 2007-10-18
> **Kilz said:**
> Have you tried to completely remove the non working kernel, purge the apt cache and then reinstall?

Tried it a few times, still not working

> **athos said:**
> Try to remove the evms package with "apt-get remove evms";
I've had a problem entering on gnome right after an update to the gutsy RC, the system informed that there was no home dir (the system couldn't find it), and after the removal of the package everything returned to normal; maybe your problem is the same. The problem ocurred with the new kernel, using the old one didn't gave the error.

evms, was not installed. Installed evms still no go, removed it still no go.

---

### Post by kleeman on 2007-10-18
One possibility is that there is a kernel bug with one of the modules controlling the hard disk. When you boot with the 2.6.20 kernel what does lsmod give? Also please show the output of lspci

---

### Post by chrism66 on 2007-10-18
> **kleeman said:**
> One possibility is that there is a kernel bug with one of the modules controlling the hard disk. When you boot with the 2.6.20 kernel what does lsmod give? Also please show the output of lspci

lsmod:
[PHP] lsmod
Module                  Size  Used by
binfmt_misc            14604  1 
rfcomm                 45352  2 
l2cap                  28160  11 rfcomm
bluetooth              62468  4 rfcomm,l2cap
capability              7048  0 
ppdev                  11272  0 
ipv6                  307456  18 
cpufreq_conservative     9736  0 
cpufreq_ondemand       10640  0 
cpufreq_powersave       3072  0 
cpufreq_stats           8416  0 
freq_table              6336  2 cpufreq_ondemand,cpufreq_stats
cpufreq_userspace       6176  0 
dev_acpi               17028  0 
pcc_acpi               15616  0 
tc1100_wmi              9224  0 
sony_acpi               7064  0 
ac                      6920  0 
container               6144  0 
button                 10016  0 
video                  19080  0 
dock                   11992  0 
sbs                    17856  0 
i2c_ec                  6912  1 sbs
asus_acpi              19756  0 
backlight               8448  1 asus_acpi
battery                12040  0 
af_packet              27020  2 
lp                     15048  0 
fuse                   51888  1 
snd_emu10k1_synth       9216  0 
snd_emux_synth         39936  1 snd_emu10k1_synth
snd_seq_virmidi         9216  1 snd_emux_synth
snd_seq_midi_emul       8960  1 snd_emux_synth
snd_emu10k1           133024  2 snd_emu10k1_synth
snd_ac97_codec        117848  1 snd_emu10k1
ac97_bus                3968  1 snd_ac97_codec
snd_pcm_oss            49408  0 
snd_mixer_oss          19840  1 snd_pcm_oss
snd_pcm                92808  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         11792  2 snd_emu10k1,snd_pcm
snd_util_mem            6656  2 snd_emux_synth,snd_emu10k1
snd_hwdep              12168  2 snd_emux_synth,snd_emu10k1
snd_seq_dummy           5380  0 
snd_seq_oss            36608  0 
snd_seq_midi           11008  0 
snd_rawmidi            29696  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event      9856  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                61856  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26632  3 snd_emu10k1,snd_pcm,snd_seq
wlan_wep                8576  1 
snd_seq_device         10260  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    68904  15 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wlan_scan_sta          16128  1 
ath_rate_sample        15360  1 
xpad                   11272  0 
ath_pci               102448  0 
wlan                  219592  5 wlan_wep,wlan_scan_sta,ath_rate_sample,ath_pci
nvidia               7016692  24 
soundcore              10272  1 snd
ath_hal               220016  3 ath_rate_sample,ath_pci
parport_pc             40104  1 
parport                43404  3 ppdev,lp,parport_pc
i2c_ali1563             9348  0 
i2c_ali15x3             9988  0 
i2c_ali1535             9092  0 
shpchp                 37404  0 
pci_hotplug            36228  1 shpchp
pcspkr                  4736  0 
psmouse                43536  0 
k8temp                  7552  0 
i2c_core               26496  5 i2c_ec,nvidia,i2c_ali1563,i2c_ali15x3,i2c_ali1535
serio_raw               9092  0 
joydev                 12928  0 
tsdev                  10112  0 
evdev                  13056  4 
ext3                  143760  2 
jbd                    68208  1 ext3
mbcache                11400  1 ext3
ide_disk               18304  3 
ide_cd                 35104  0 
cdrom                  40744  1 ide_cd
usbhid                 29088  0 
hid                    34048  1 usbhid
sata_uli               10372  0 
alim15x3               14104  0 [permanent]
generic                 6532  0 [permanent]
floppy                 67944  0 
ehci_hcd               37004  0 
ata_generic            10628  0 
ohci_hcd               24196  0 
libata                137000  2 sata_uli,ata_generic
scsi_mod              166968  1 libata
usbcore               154416  5 xpad,usbhid,ehci_hcd,ohci_hcd
thermal                16912  0 
processor              34952  1 thermal
fan                     6536  0 
fbcon                  44416  0 
tileblit                4096  1 fbcon
font                    9856  1 fbcon
bitblit                 7296  1 fbcon
softcursor              3712  1 bitblit
vesafb                 10376  0 
cfbcopyarea             5120  1 vesafb
cfbimgblt               4096  1 vesafb
cfbfillrect             5632  1 vesafb
commoncap               9472  1 capability
[/PHP]

lspci:
[PHP]00:00.0 Host bridge: ALi Corporation M1689 K8 Northbridge [Super K8 Single Chip]
00:01.0 PCI bridge: ALi Corporation AGP8X Controller
00:02.0 PCI bridge: ALi Corporation M5249 HTT to PCI Bridge
00:03.0 ISA bridge: ALi Corporation M1563 HyperTransport South Bridge (rev 70)
00:03.1 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:0e.0 IDE interface: ALi Corporation M5229 IDE (rev c7)
00:0e.1 IDE interface: ALi Corporation ULi 5289 SATA (rev 10)
00:0f.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:0f.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:0f.2 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:0f.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7800 GS] (rev a2)
02:08.0 Ethernet controller: Atheros Communications, Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
02:09.0 Multimedia audio controller: Creative Labs SB0400 Audigy2 Value
[/PHP]

---

### Post by tuberculo on 2007-10-20
chrism66, is it working now?

---

### Post by DSK on 2007-10-20
> **dabl said:**
> It all looks correct (the fstab and menu.lst files) -- which I think translates to "bad news -- something wrong with hdd partition table".

:(

Did you try to run gparted and see if it brings up the disk partitions correctly?

Is there any reason to suspect that an "unmanaged event" might have caused that hard drive to experience a sudden/momentary loss of power, or anything like that?

I don't know of any "on the fly" remedies for a messed up disk partition table, unfortunately.  I think the remedy starts with a pile of empty DVDs ....   :(

I hosed my boot and partians when I was adding Gutsy to my dual booting XP and Vista box.  I wanted to compare all the OS's.  Well, when I lost it all this fixed everything!

[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

This is a great live CD.  Not sure if it will help with the problem in my thread but its a great tool that everyone should have.

---

### Post by chrism66 on 2007-10-20
No! Still only able to boot the older kernels.

---

