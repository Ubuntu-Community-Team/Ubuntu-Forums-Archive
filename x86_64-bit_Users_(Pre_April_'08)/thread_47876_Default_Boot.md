---
title: "Default Boot"
date: 2005-07-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by Irony on 2005-07-10
I've been looking at the instructions at [http://amd64.ubuntuguide.org/#changedefaultosgrub](http://amd64.ubuntuguide.org/#changedefaultosgrub) to change the boot default.

I want the default to be XP rather than Ubuntu, the instructions say to change;

default         0

to

default         X_sequence

in the /boot/grub/menu.lst file. The sample given shows the change - I'm assuming that this change actually makes XP the default boot (because I can't actually see how the 'X_sequence' instruction relates to anything). Is this correct and is it all I have to do?

Also what does sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup actually do, I assume it is a backup but how is it recovered?

---

### Post by sean_worker on 2005-07-10
in place of X_sequence you need to put the number of the XP entry in your menu.lst file. you start counting at zero, so if you have a menu.lst file like mine:

```

default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		7

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

*SNIP*

title		Ubuntu, kernel 2.6.10-5-686 
root		(hd0,2)
kernel		/vmlinuz-2.6.10-5-686 root=/dev/hda6 ro quiet splash
initrd		/initrd.img-2.6.10-5-686
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-686 (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.10-5-686 root=/dev/hda6 ro single
initrd		/initrd.img-2.6.10-5-686
savedefault
boot

title		Ubuntu, kernel memtest86+ 
root		(hd0,2)
kernel		/memtest86+.bin  
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```


you will want to change the zero after default to 4 (the "Other operating systems" line counts).

Also, if you have not already done so (or it wasn't done during your install), you will probably want to comment out the "hiddenmenu" line like I have done (see right before the snip), so that you can change to boot to ubuntu easily when your system is starting up.

As for the command:

```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup

```

there are actually 2 commands on the line.

The first is [FONT=Courier New]sudo[/FONT], it means "super user do" and will execute the second command [FONT=Courier New]cp[/FONT] as the super, or root, user.  The [FONT=Courier New]cp[/FONT] command makes a copy of the file "[FONT=Courier New]/boot/grub/menu.lst[/FONT]" and saves it as "[FONT=Courier New]/boot/grub/menu.lst_backup[/FONT]".  You can restore this backup by doing the same command but switching the order of the file names:

```

sudo cp /boot/grub/menu.lst_backup /boot/grub/menu.lst

```

Of course that will destroy your current menu.lst file.  If you don't want to do that, move or copy it somewhere else as well.  Using the [FONT=Courier New]mv[/FONT] (move) command you might switch out your current menu.lst file with your backup with the following sequence:
```

sudo mv /boot/grub/menu.lst /boot/grub/menu.lst_backup2
sudo mv /boot/grub/menu.lst_backup /boot/grub/menu.lst
sudo cp /boot/grub/menu.lst_backup2 /boot/grub/menu.lst_backup

```

---

### Post by Irony on 2005-07-10
Thanks sean_worker, should my file therefore be like this to default load XP after 10 seconds;

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
default		6

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
## by the debian update-grub script except for the default optons below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hdb1 ro console=tty0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.10-5-amd64-generic Default 
root		(hd1,0)
kernel		/boot/vmlinuz root=/dev/hdb1 ro console=tty0 quiet splash
initrd		/boot/initrd.img
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-amd64-generic Default (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz root=/dev/hdb1 ro console=tty0 single
initrd		/boot/initrd.img
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-amd64-generic 
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.10-5-amd64-generic root=/dev/hdb1 ro console=tty0 quiet splash
initrd		/boot/initrd.img-2.6.10-5-amd64-generic
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-amd64-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.10-5-amd64-generic root=/dev/hdb1 ro console=tty0 single
initrd		/boot/initrd.img-2.6.10-5-amd64-generic
savedefault
boot

title		Ubuntu, kernel memtest86+ 
root		(hd1,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

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
chainloader	+1[/PHP]

In other words, I change 0 to 6.

What do you mean by hidden menu? Are you referring to the list of boot options. Currently when I boot up, if I want to change the boot option I use the up down arrow keys when I see these options.

---

### Post by Irony on 2005-07-10
Thanks sean_worker it works! I simply changed 0 to 6.

---

### Post by sean_worker on 2005-07-11
I'm glad this got it working for you.

> 
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu


This was the hiddenmenu option I was talking about (from your menu.lst) file.
It was already commented out, so that's why you had the boot menu you can navigate with your arrow keys.

Sean.

---

