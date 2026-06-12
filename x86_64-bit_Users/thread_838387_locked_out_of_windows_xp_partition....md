---
title: "locked out of windows xp partition..."
date: 2008-06-23
forum: x86 64-bit Users
---

### Post by milan_82 on 2008-06-23
I recently updated to ubuntu studio 8.04 from 7.10. I am able to access both windows xp and ubuntu at startup.. I have had no problems with this until last night, when I downloaded some extra components for ubuntu amd_64 (to get flash working). I closed my computer down, woke up this morning and tried to go into windows... it gives me a quick flash of the blue screen and restarts the system over again. I try going into windows in safe mode, and it restarts as well. I was able to access my windows partition from ubuntu before and now when I click on the partition to open, it says CANNOT MOUNT VOLUME: You are not privileged to mount this volume. I cannot afford to be locked out of this!!  I got files I need in there!  How did this happen and what can I do???!!?!!!!

---

### Post by kuja on 2008-06-23
Here's my thoughts on what it might be related to: If it gives you the bsod right away, then the partition might have been, in a worst case scenario, corrupted. Other bad scenarios might include windows viruses (not from within ubuntu, of course, but the last time you ran windows ... just saying it's possible that one of the important boot files could have say, disappeared, or something.) Another thing to double check .. hmmm, check your /boot/grub/menu.lst and verify that the entry for WindowsXP is correct, if Windows is installed on any partition other than the first partition on the first hard drive, you'll need two additional map lines to trick windows insto thinking it is.

With regards to it not wanting to mount in ubuntu, that might because you need [root privileges](https://wiki.ubuntu.com/RootSudo). Try again to mount it via ubuntu and see that all files still exist.

Plenty of possibilies out there, which one it is ..... it's hard to say with the amount of information given :)

---

### Post by milan_82 on 2008-06-23
HERE IS WHAT I SEE IN menu.lst

examples
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
# kopt=root=UUID=315ec85e-0315-4c02-a490-ed1e8f7b5f99 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

title		Ubuntu 8.04, kernel 2.6.24-19-rt
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-rt root=UUID=315ec85e-0315-4c02-a490-ed1e8f7b5f99 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-rt
quiet

title		Ubuntu 8.04, kernel 2.6.24-19-rt (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-rt root=UUID=315ec85e-0315-4c02-a490-ed1e8f7b5f99 ro single
initrd		/boot/initrd.img-2.6.24-19-rt

title		Ubuntu 8.04, kernel 2.6.22-14-rt
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-rt root=UUID=315ec85e-0315-4c02-a490-ed1e8f7b5f99 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-rt
quiet

title		Ubuntu 8.04, kernel 2.6.22-14-rt (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-rt root=UUID=315ec85e-0315-4c02-a490-ed1e8f7b5f99 ro single
initrd		/boot/initrd.img-2.6.22-14-rt

title		Ubuntu 8.04, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by kuja on 2008-06-23
Try removing the savedefault line (third line from the bottom of your paste) and see if it works afterwards ... I don't know why but sometimes savedefault can give grub trouble.

---

### Post by milan_82 on 2008-06-23
how do I change that?  I delete the line and save, but it says I don't have the privilege to do so cause I am not the owner. I need to be root.  How do I do that

---

### Post by kuja on 2008-06-23
Ah, yes, you'll need [admin privileges](https://wiki.ubuntu.com/RootSudo) to do so. You'll need to prepend kdesudo or gksudo to the beginning of the editor command. (ie: kdesudo kate or gksudo gedit ... etc)

---

### Post by milan_82 on 2008-06-24
removed savedefault, and still no success. 
this is what I see when I type sudo fdisk -l 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6f0a675f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9119    73248336    7  HPFS/NTFS
/dev/sda2   *        9120       19270    81537907+  83  Linux
/dev/sda3           19271       19457     1502077+   5  Extended
/dev/sda5           19271       19457     1502046   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    c  W95 FAT32 (LBA)

Everything was working great, I could access all partitions and log into windows until I installed these programs:

sudo apt-get purge nspluginwrapper
sudo apt-get purge flashplugin-nonfree
sudo rm -rfd /usr/lib/nspluginwrapper
sudo rm -f /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo apt-get install nspluginwrapper flashplugin-nonfree lib32nss-mdns
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-addons/plugins/
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-3.0/plugins/
flashplayer10_install_linux_051508.tar.gz

as well as many flash components from synaptic. you think this could have done it? or was it a sheer coincidence?

---

