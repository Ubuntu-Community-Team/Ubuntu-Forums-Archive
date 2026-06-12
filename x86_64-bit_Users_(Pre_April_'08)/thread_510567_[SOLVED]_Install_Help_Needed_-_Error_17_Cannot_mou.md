---
title: "[SOLVED] Install Help Needed - Error 17: Cannot mount selected partition"
date: 2007-07-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by crjackson on 2007-07-26
Here's my issue.  I have 4 SATA drives in my system as follows.

[B]SATA0 - Winxp
SATA1 - Storage
SATA2 - Storage
SATA3 - Ubuntu[/B]

I booted from the live CD and selected install.  I set my Ubuntu target to an empty drive (SATA3).  In the advanced tab, I selected to install GRUB onto HD3 (SATA3).  The install completed without errors, GERUB installed without errors.

When finished it gave me options of 1- Continue using LiveCD 2-Reboot.  I selected 2 and it started shuting down.  It told me to remove the CD and press enter.  I did that.

**Nothing happend...  I tried several times and still nothing, so I hit the reset button.  When rebooting, I got Error 17: Cannot mount selected partition**

Windows still boots fine, as I didn't mess with the MBR on that drive.  I select my boot drive by using the F11 key and telling the BIOS which drive to boot.

This was working perfectly on a previous install but I upgraded that drive from and IDE to an SATA Raptor.  Windows didn't know about ubuntu.  Ubuntu knew about Windows but didn't jack up it's MBR.  I have a good reason for doing it this way - I won't go into detail for brevity reasons, but I know it can work this way, I just can't duplicate making it work as my previous install did.

Now I get Error 17: Cannot mount selected partition.  GRUB Loads but can't mount the ubuntu volume.

Tell me how to make this work please.  I don't want the GRUB on the Windows drive.

Would disconnecting all other drives from the couputer during the install, then reconnecting them be my only option?

Please tell me how to make a clean ubuntu install on the desired drive, without mucking up the WinXP MBR.

Thanks...

---

### Post by crjackson on 2007-07-26
Does this make any sense?

When I installed and hit advanced for where to load the grub, the default is HD0, on my firtst attempt the install completed but couldn't install a grub because I changed it to SDD which I thought would be correct.

On the second attempt, I changed it to HD3 since it's the 3rd device.

Could it be that the proper entry is SD3?  Or is this even valid at all?

Please advise before my next attempt....

---

### Post by crjackson on 2007-07-26
I'm getting ready to leave work and when I get home I plan to try again.

Any suggestions before I give it another go?

---

### Post by crjackson on 2007-07-27
Well, it seems that SD3 isn't a valid option for the boot loader.  It got all the way through the install and then when it tried to install the boot loader and/or Grub...  It said fatal error.

Now I'm trying again with the HD3 option hoping that it would have worked before were it not for me hitting the hard reset.

I sure am glad to be getting so much help from myself.  I don't know what I would do without me:)

---

### Post by oldlucky on 2007-07-27
> **crjackson said:**
> Here's my issue.  I have 4 SATA drives in my system as follows.

[B]SATA0 - Winxp
SATA1 - Storage
SATA2 - Storage
SATA3 - Ubuntu[/B]

Windows still boots fine, as I didn't mess with the MBR on that drive.  I select my boot drive by using the F11 key and telling the BIOS which drive to boot.

Thanks...

What i would try would be put sata0 to sata3 (just swap them around windows and Ubuntu) and see if you can still boot windows (sata3) with the F11 key . Now if that boots into windows and it works i would then proceed to install Ubuntu on sata0 it should pick up that windows is on sata3 and put an option there on the Ubuntu mbr to either boot Winxp or Ubuntu and it will not touch the mbr from the windows disk.

cheers

---

### Post by logos34 on 2007-07-27
Grub uses 'hd0, 'hd1'...etc to designate drives, regardless of whether they're sata, scsi, ide/pata, usb or whatnot.  The OS uses the hda, sda terminology.  So after hitting the 'Advanced' button for the grub install dialog box you should have entered either '(**hdx)**' or used the format '/**dev/sdy**' (where x=0-3 and y=a,b,c or d).  But the ubuntu drive, 'sata3' as you call it (the sata channel it's on?) may or may not be last in the bios (hd3). (edit: that is, at the time of install)

You might want to post your menu.lst. 

Boot from the live cd, go to the desktop, click on your ubuntu root partition (it should mount), open up /boot/grub/**menu.lst** and **device.map**.

Post it along with the output of:

**sudo fdisk -l**

---

### Post by crjackson on 2007-07-27
> **logos34 said:**
> Grub uses 'hd0, 'hd1'...etc to designate drives, regardless of whether they're sata, scsi, ide/pata, usb or whatnot.  The OS uses the hda, sda terminology.  So after hitting the 'Advanced' button for the grub install dialog box you should have entered either '(**hdx)**' or used the format '/**dev/sdy**' (where x=0-3 and y=a,b,c or d).  But the ubuntu drive, 'sata3' as you call it (the sata channel it's on?) may or may not be last in the bios (hd3). (edit: that is, at the time of install)

You might want to post your menu.lst. 

Boot from the live cd, go to the desktop, click on your ubuntu root partition (it should mount), open up /boot/grub/**menu.lst** and **device.map**.

Post it along with the output of:

**sudo fdisk -l**

Thank you for helping.  I tried HD3 and that didn't work.  I got the same error.  The drive is the last one in the chain and is seen the same way in BIOS.  Here is my output from the terminal.

[B]charles@MSI-K8N-Neo4-SLI-Platinum:~$ sudo fdisk -l

Disk /dev/sda: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9039    72605736    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
16 heads, 63 sectors/track, 484521 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      484518   244197040+   7  HPFS/NTFS

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
16 heads, 63 sectors/track, 484521 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1      484520   244198048+   7  HPFS/NTFS

Disk /dev/sdd: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        8666    69609613+  83  Linux
/dev/sdd2            8667        9039     2996122+   5  Extended
/dev/sdd5            8667        9039     2996091   82  Linux swap / Solaris
charles@MSI-K8N-Neo4-SLI-Platinum:~$ [/B]

I got it installed but not the way I want.  I was forced to let it re-write the MBR on the XP drive.  I would like to get this installed so that it doesn't look to the XP drive for the boot record and/or grub.

I really need some help with this.  I've been trying for hours and hours now.

[B]# menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=5d2e3666-905e-4795-b1f2-701bfbf92ad1 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd3,0)

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
# defoptions=quiet nosplash

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=5d2e3666-905e-4795-b1f2-701bfbf92ad1 ro quiet nosplash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=5d2e3666-905e-4795-b1f2-701bfbf92ad1 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=5d2e3666-905e-4795-b1f2-701bfbf92ad1 ro quiet nosplash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=5d2e3666-905e-4795-b1f2-701bfbf92ad1 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd3,0)
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
root		(hd0,0)
savedefault
makeactive
chainloader	+1
[/B]

[B](hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc
(hd3)	/dev/sdd[/B]

---

### Post by logos34 on 2007-07-27
Nice to have all those drives except when it comes to dual booting!  But there should be a way to fix this without reinstalling.  Here's what I'd try:

Go into the bios and swap your raptors in the the hard disk boot priority:

> 1. sdd (ubuntu)
2. sdb 
3. sdc 
4. sda (windows)

Then boot the Ubuntu live cd, click on root partition to mount it, and edit menu.lst and device.map:

**cd /media/disk/boot/grub**

**sudo cp menu.lst menu.lst_backup**

**gksudo gedit menu.lst **

change all instances of **(hd3,0)** to **(hd0,0)**

Edit device.map by switching the first and last:
[B]
sudo cp device.map device.map_backup[/B]

> (hd0) **/dev/sdd**
(hd1) /dev/sdb
(hd2) /dev/sdc
(hd3) **/dev/sda**

Now reinstall grub to the MBR of sdd:

> **sudo grub**
**find /boot/grub/stage1**
(this should return '(hd0,0)'--enter in next command)
**root (hd0,0)**
**setup (hd0)**
**quit**

See if that works.  If it does, then you can try changing the entry for windows to get it to boot from grub too (and then restore the windows bpotloader to sda so you can boot to it directly if need be)

A new windows entry might look like this:

> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows XP Professional
root (hd3,0)
map (hd3) (hd0)
map (hd0) (hd3)
savedefault
makeactive
chainloader +1

---

### Post by crjackson on 2007-07-27
I don't mind reinstalling so do you think this MIGHT work...

What if I unplug my 3 NTFS drives, Leave the Ubunt drive plugged in to the same connector,  then boot (I hope) to the liveCD and install to that drive.

If it all installs, will there be a problem when I plug in my other drives?  Will I still be able to boot to ubuntu or will the grub be messed up and still not boot?

What do you think?

---

### Post by logos34 on 2007-07-27
If you want, go ahead.  Grub will instal to the MBR, and then reboot and test it.  Then connect your other disks.  The only thing is you will have to add fstab entries for the other drives manually if you want them to automount  in linux.  And you could still try adding a boot entry for windoes to grub even if you plan to boot straight to windows' own bootloader on that disk.  Restore the windows bootloader using the windows install cd by going into recovery console and tying fixboot or fixmbr.

---

### Post by crjackson on 2007-07-27
it seems there's just no easy way to install ubuntu on any drive but the 1st one.  Well atleast not on an SATA drive anyway.

It was so easy on the ide drive.  I may just sell the raptor and forget the whole idea.  I liked it worked on the ide drive and just wanted more performance.

---

### Post by crjackson on 2007-07-27
Okay, here's what I did and it worked.

I put drive numbe 4 on port 1 - Ubuntu Boot
       drive number 1 on port 2 - Windows Boot
       drive number 2 on port 3 - Storage
       drive number 3 on port 4 - Storage

I wiped out the partitions on the Ubuntu/Windows drives, and reinstalled.

Ubuntu now boots w/grub loaded on same disk.
XP now boots with the MS MBR not touched by Linux.

My conclusion is that ubuntu is more picky about drive placement than XP.  That's disappointing.  I though it was supposed to be more flexible than MS, but in this case it seems not.

Thanks for all the suggestions...

---

### Post by logos34 on 2007-07-27
In my experience it's just the reverse--windows is more picky than linux about the boot/drive order.  What I don't understand is why you were having so much trouble--I could see it if you had a mixed ide-sata setup (in which case grub prioritizes ide), but this is straight sata.  hmm.  The main trick in multidrive arrangements like yours is to figure out what drive MBR grub installed and and boot to that--it doesn't always go on the ubuntu install drive.  

Glad you got it working--that's the important thing.  Try something, though, if you would: viz. what I suggested above about editing the windows entry in menu.lst with the 'map' lines.  Hopefully that will permit you to boot windows directly from the grub. Of course you can always just enter the bios each time and switich the boot order, but the grub way would at least save you that extra step.  It won't mess anything up if it doesn't work. 

Did you do the ubuntu install with the other drives connected?

---

### Post by crjackson on 2007-07-27
> **logos34 said:**
> Did you do the ubuntu install with the other drives connected?

Yes, all drives were ooperational but the SCSI1(sdb1) was unpartitioned at the time.  I then restored an image of my xp drive to the empty partition.

I'll check this weekend and see if grub sees the XP drive.

---

### Post by logos34 on 2007-07-27
> **crjackson said:**
> Yes, all drives were ooperational but the SCSI1(sdb1) was unpartitioned at the time.  I then restored an image of my xp drive to the empty partition.

I'll check this weekend and see if grub sees the XP drive.

I'm getting a little confused now by the drive desgnations, but if you reinstalled ubuntu to sdd (in first bios position), and the windows drive (the one that is now in second place) was wiped clean/unpartitioned at the time, then the linux installer could not have detected it.  You'll have the add entries for it to menu.lst and fstab.

---

### Post by crjackson on 2007-07-27
> **logos34 said:**
> I'm getting a little confused now by the drive desgnations, but if you reinstalled ubuntu to sdd (in first bios position), and the windows drive (the one that is now in second place) was wiped clean/unpartitioned at the time, then the linux installer could not have detected it.  You'll have the add entries for it to menu.lst and fstab.


[B]Previously:

HD0 - Windows (Raptor)
HD1 - DATA      (Hitachi)
HD2 - DATA      (Hitachi)
HD3 - Ubuntu   (Raptor)[/B]

Basically what I did was wipe my to raptor drives clean and put them in positions as follows:

[B]
HD0 - UBUNTU       (Raptor)
HD1 - WINDOWS   (Raptor)
HD2 - DATA           (Hitachi)
HD3 - DATA           (Hitachi)[/B]

Then I installed ubuntu on a clean HD0 Raptor, tested and all was okay.
Then I restored my disk image of XP to HD1 Raptor, tested and all was well

Changed my boot order so that HD1 boots by default (for the wife who won't be bothered with menu booting)

I restart hit F11 boot menu from BIOS, select HD0 and Ubuntu boots without isses.  It mounts HD1 just fine, but I don't know if it shows Windows in the Grub menu (which is fine).  I would like to know how to put it there if it doesn't though.  I think you may have posted it above, I'll check on it this weekend.

---

### Post by logos34 on 2007-07-27
> Changed my boot order so that HD1 boots by default (for the wife who won't be bothered with menu booting)

I restart hit F11 boot menu from BIOS, select HD0 and Ubuntu boots without isses. It mounts HD1 just fine, but I don't know if it shows Windows in the Grub menu (which is fine). I would like to know how to put it there if it doesn't though. I think you may have posted it above, I'll check on it this weekend.

Ok, so it's for the convenience of your wide that you want that particular boot setup. 

I'm still not used to how easily everything mounts easily and automatically in Feisty...Windows is probably showing up generically as /media/disk or something...You might want to add a custom mountpoint like /media/windows to fstab.  You can also add write capability to ntfs with ntfs-3g, something to consider. (using ntfs-config will edit any prexisting fstab entry for you).  But windows on the second raptor shouldn't be listed in menu.lst.

---

### Post by crjackson on 2007-07-28
Grub search my drives on 1st boot and added Windows boot to the grub menu.  It's all working perfectly as I need it to at this point, except I can't get the ATI video card driver installed properly like it was before.  I haven't given up, I'll get it sooner or later....

---

### Post by crjackson on 2007-07-28
This really sucks.  I couldn't get my video card driver to ever work again on a clean install...

Good news is that I was able to clone the install (via diskimage) from the IDE drive to the SATA drive.

IT WORKED!

Just two minor tweaks needed, but I need hand holding here.

When it boots, it looks for the original drive (IDE) and of course it fails to load as indicated in red during the boot up process - What file do I edit to remove the old entry?  CODE PLEASE....

Next,  It fails to mount (automatically) the drive that was placed onto the 4th SATA port (it had nothing there before).

It mounts when I click on the drive, but not on boot up.  It's an NTFS drive, and I have the 3G software installed.

I'm guessing I need to add the drive to the boot up file, but I don't know what file that is and how to edit it.

Please Help...  I have an image of a clean install that would have been great, but I can't get the ATI driver to install properly.

Strange - It worked like a charm 1st try on this install.  I just don't understand those damned ATI drivers.

Thanks

---

### Post by logos34 on 2007-07-28
copy /etc/fstab file and all of /boot directory over to the imaged ubuntu.  (maybe just rename the existing fstab and /boot for the time being). see if that works

---

### Post by logos34 on 2007-07-28
or if you overwrot ethe existing ubuntu (re)install on that sata drive and didn't save the grub files or fstab, you have to edit menu.lst and device.map in /boot/grub, and /etc/fstab to reflect the new arrangement.

---

### Post by crjackson on 2007-07-29
> **logos34 said:**
> or if you overwrot ethe existing ubuntu (re)install on that sata drive and didn't save the grub files or fstab, you have to edit menu.lst and device.map in /boot/grub, and /etc/fstab to reflect the new arrangement.

Sadly that didn't work - I may be heading back to xp only.  If I can't get my video driver / screen settings back on normal from a clean install, and I can't get my boot working properly from the old install, I seem to have little choice.

---

### Post by crjackson on 2007-07-29
How can I tell if the swap file is being used.  I got a error related to the swap file and it looked like it was disabled.

---

