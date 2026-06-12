---
title: "how to add grub boot picture?"
date: 2007-12-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by Lukasz Tarkowski on 2007-12-28
Dear Support
How can I add a theme to boot grub menu?
Is there a tutorial for it?

---

### Post by chewearn on 2007-12-28
Here is one:
[http://ubuntuforums.org/showthread.php?t=208855](http://ubuntuforums.org/showthread.php?t=208855)

---

### Post by Lukasz Tarkowski on 2007-12-28
Where do I put in menu.lst gfxmenu /boot/grub/message.suse
Can someone give me their code? so I can put it in menu.lst

---

### Post by chewearn on 2007-12-29
> **Lukasz Tarkowski said:**
> Where do I put in menu.lst gfxmenu /boot/grub/message.suse
Can someone give me their code? so I can put it in menu.lst

Put it as the first line of menu.lst.

---

### Post by Lukasz Tarkowski on 2007-12-29
I will do that soon :)

---

### Post by Lukasz Tarkowski on 2007-12-29
Im gonna past this code again heh

---

### Post by chewearn on 2007-12-29
> **Lukasz Tarkowski said:**
> still don't get it I put before still doesn't work
do I have to remove the word gfxmenu?


No, the gfxmenu is needed.
Actually, I haven't try the howto; let me do that then I can better answer.

---

### Post by chewearn on 2007-12-29
Ok, gone thru the steps meself.  Except for one minor correction, where I have to find the amd64 version of gfxboot, it works.
:popcorn:

If you still have problem, could you go thru the steps one more; then post everything from your terminal.  Also, post your menu.lst

---

### Post by Lukasz Tarkowski on 2007-12-30
Hey 
Here is my menu.lst

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
#      password --Security Reasons
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
# kopt=root=UUID=Security Reasons ro

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=Security Reasons
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=Security reasons ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd1,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by chewearn on 2007-12-30
So, you need to add:
gfxmenu /boot/grub/message.suse

at the top of menu.lst (line 1)

I also see that you have two harddisks, primary HD is WinXP and secondary HD is ubuntu.  Where is your grub installed?

Have you gone thru the steps again?  Can you post everything on your terminal?

---

### Post by Lukasz Tarkowski on 2007-12-30
_My boot is installed on The Internal Disk Mbr _
_Ubuntu_ is installed on _External Usb_ 

_Hd1 grub_
_message.Ubuntu is on stage 2_ and I got stage 1.5 enabled how do i enable stage2
_Stage 1.5 loads instead of 2 :(_

---

### Post by chewearn on 2007-12-31
> **Lukasz Tarkowski said:**
> _My boot is installed on The Internal Disk Mbr _
_Ubuntu_ is installed on _External Usb_ 

_Hd1 grub_
_message.Ubuntu is on stage 2_ and I got stage 1.5 enabled how do i enable stage2
_Stage 1.5 loads instead of 2 :(_

I don't quite understand.  Are you now unable to boot into ubuntu or WinXP?  Or just the grub menu is still not change to graphical?

What do you get for this:
```
sudo grub
grub> find /boot/grub/stage1
(hdx,y) # this will be the output
grub> root (hdx,y)
grub> setup (hdx)
```

Did you also try the additional/alternative steps specified somewhere in the thread:
```
sudo fdisk -l
grub-install /dev/X
```

Note:
In the above two parts, you need to change x, y and X to match your system.

---

### Post by Lukasz Tarkowski on 2008-01-14
It works now
I'm trying to make my own theme
[U]I tried using sudo ls . |cpio -o > /boot/grub/message.new
It didn't work
said Permission denied[/U]

---

### Post by Jouke74 on 2008-01-14
My way:

- To install the bootsplash image at startup from myself:

1. Make an image with size 640x480 and max 14 colors (in Gimp).
2. Save the image as XPM.
3. Tar the image to splash.xpm.gz.
4. Open a terminal.

> sudo mv splash.xpm.gz /boot/grub  (or copy if you to keep it somewhere else)
> sudo update-grub

It leaves the text menu over the image. And also does not change when Kernels are updated. It just adds the background splash.
But also no "funny" Suse programs in my bootlader...

---

### Post by chewearn on 2008-01-14
> **Jouke74 said:**
> My way:

- To install the bootsplash image at startup from myself:

1. Make an image with size 640x480 and max 14 colors (in Gimp).
2. Save the image as XPM.
3. Tar the image to splash.xpm.gz.
4. Open a terminal.

> sudo mv splash.xpm.gz /boot/grub  (or copy if you to keep it somewhere else)
> sudo update-grub

It leaves the text menu over the image. And also does not change when Kernels are updated. It just adds the background splash.
But also no "funny" Suse programs in my bootlader...

Sure, I have done this before.  But the results were unbearably ugly, I rather have plain text.:lol:

---

### Post by Jouke74 on 2008-01-15
Yup I agree you need to be very creative with just 14 colors under 64 bit :lolflag:

---

### Post by Lukasz Tarkowski on 2008-01-22
Thank You  Jouke74
I will do that soon since I reinstalled Ubuntu heh

---

