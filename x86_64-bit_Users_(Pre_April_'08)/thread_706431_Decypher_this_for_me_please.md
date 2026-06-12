---
title: "Decypher this for me please?"
date: 2008-02-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by gfahey on 2008-02-24
I made mention in another post about my Dell Vostro 1000 needing several (or more) hard reboots to boot into the login screen. I am still having this same issue.

It boots to BIOS>Grub and then I get this:

"Starting up.....

You passed an undefined mode number.

Press <RETURN> to see video modes available, <SPACE> to continue or wait 30 seconds."


I choose to wait and upon several hard reboots, I eventually get to login screen and things work great. Proper screen res of 1280x800, video and audio working great, no problems otherwise.

But....this is a major annoyance to say the least. Could someone please help me with this?

---

### Post by jeffus_il on 2008-02-24
The vga mode passed to the kernel in the file /boot/grub/menu.lst is not valid for your setup. Edit the file and look for "vga=", the number following this is not valid.
> Here is a table of VESA video modes (VGA codes):
         640x480   800x600   1024x768   1280x1024   1600x1200   Ask user at boot.
8 bits      vga=769   vga=771   vga=773    vga=775     vga=796     vga=ask
16 bits    vga=785   vga=788   vga=791    vga=794     vga=798     vga=ask
32 bits    vga=786   vga=789   vga=792    vga=795     vga=799     vga=ask

---

### Post by gfahey on 2008-02-24
> **jeffus_il said:**
> The vga mode passed to the kernel in the file /boot/grub/menu.lst is not valid for your setup. Edit the file and look for "vga=", the number following this is not valid.

How to edit?

---

### Post by jeffus_il on 2008-02-24
Open a terminal and type ```
gedit /boot/grub/menu.lst
```

---

### Post by gfahey on 2008-02-24
> **jeffus_il said:**
> Open a terminal and type ```
gedit /boot/grub/menu.lst
```

I do this and it brings up a blank document.

---

### Post by jeffus_il on 2008-02-24
Which version of Ubuntu are you running?

---

### Post by gfahey on 2008-02-24
> **jeffus_il said:**
> Which version of Ubuntu are you running?

Gutsy 7.10

---

### Post by ajgreeny on 2008-02-24
For now just use nautilus to navigate to the /boot/grub/menu.lst file and open it by double clicking on it.  It should then open in gedit, but you will not be able to save any changes.  To make permanent changes you will need to open it as root so in a terminal type ```
gksudo gedit /boot/grub/menu.lst
```  If it is an empty file, you have a problem and will not be able to reboot your computer, but unless you've somehow deleted that file, which you can also only do as root, it should contain a lot of text with a list of OSs at the bottom.  Copy and paste that list back here.

---

### Post by gfahey on 2008-02-24
> **ajgreeny said:**
> For now just use nautilus to navigate to the /boot/grub/menu.lst file and open it by double clicking on it.  It should then open in gedit, but you will not be able to save any changes.  To make permanent changes you will need to open it as root so in a terminal type ```
gksudo gedit /boot/grub/menu.lst
```  If it is an empty file, you have a problem and will not be able to reboot your computer, but unless you've somehow deleted that file, which you can also only do as root, it should contain a lot of text with a list of OSs at the bottom.  Copy and paste that list back here.

Thanks, here you go:

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=b54fd9cd-0e8c-452d-a53e-2a0680398f2b ro

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
# defoptions=quiet splash vga=758

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
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=b54fd9cd-0e8c-452d-a53e-2a0680398f2b ro quiet splash vga=758
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=b54fd9cd-0e8c-452d-a53e-2a0680398f2b ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by ajgreeny on 2008-02-24
>  title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=b54fd9cd-0e8c-452d-a53e-2a0680398f2b ro quiet splash** vga=758**
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=b54fd9cd-0e8c-452d-a53e-2a0680398f2b ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
OK, now open the file in gedit with ```
gksudo /boot/grub/menu.lst
``` and then delete the vga=758 that I've highlighted in the quote, save the file and try booting again.

---

### Post by gfahey on 2008-02-24
Thanks so much for your time.

I did that and while it took care of this:
[COLOR="Red"]
"Starting up.....

You passed an undefined mode number.

Press <RETURN> to see video modes available, <SPACE> to continue or wait 30 seconds."[/COLOR]

I am still having the same problem of having to hard reboot several times for it to boot to login. It loads GRUB and then I wait a few seconds for what (I usually see in the past) is an Ubuntu splash screen. I never see that even upon successful boot to login. 

Any idea what this is? Is it trying to load a splash screen and then getting hung up?

---

### Post by gfahey on 2008-02-24
OK, here's what I did;

I looked around and went to System>Preferences>Splash Screen. There, I found a splash screen that I must have downloaded into that directory/app. I highlighted it and deleted it. 

I rebooted.

Now the old screen mode error text was appearing again. I figured it was reverting to the original file after I had removed the splash screen. So, I opened the /boot/grub/menu.lst file and sure enough, the line "vga=758" was back. I deleted that saved, closed and rebooted. 

Voila! Back to the original Ubuntu splash screen (man it looked great to see that) and rebooted 5 times in a row without incident.

Thanks. Thanks so much. Again.

---

