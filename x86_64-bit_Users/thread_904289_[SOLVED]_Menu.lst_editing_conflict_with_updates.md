---
title: "[SOLVED] Menu.lst editing conflict with updates"
date: 2008-08-29
forum: x86 64-bit Users
---

### Post by alt3rn1ty on 2008-08-29
Hi this is probably not just x64 specific but it is the OS I am using so can anyone help get me straight on the following...

I have the family desktop setup with ubuntu 8.04 OS as a back-up OS to XP, so if there are any problems whilst I am away from home at least they have email support from me and internet access. My own laptop uses Ubuntu as its default OS so no problem there.

The problem raised its head after a kernel update a few days ago, because I changed the order of menu.lst on the desktop to have XP as the top item in grub selection, the update wanted to change a few lines in menu.lst and recognised the non-standard changes I had applied. I think I was given 6 options, the best I decided was replace with the installers recommendation (just in case there were menu.lst changes the update needed to do). On re-booting I no longer had XP as an option.

So not a problem I just re-edited the menu.lst to have an option to chain load XP and all works as it should again.... but

For future updates, if this happens again and I am away the family will be left with just Ubuntu and no access to their own user accounts on XP and games, so how do I write the menu.lst in such a way as not to be affected by updates but have XP as the default OS (I think - correct me if wrong - I should just have changed the default os entry to read 4 instead of keeping it at 0 and cut/pasting XP to the top of the list)
And having now re-edited the menu.lst does grub expect seperators and/or does it have a comparison back-up menu.lst which highlighted the change I had done to menu.lst to the update procedure in the first place, in which case I would need to know where/how to edit that also.

Thanks in advance.

---

### Post by ajgreeny on 2008-08-29
Instead of changing the order of the menu list items simply change the default boot number.  Near the top of the menu.lst is a stanza of text like this:-

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

Just change the 0 to the correct number for winXP, remembering to start from 0, and also to count the line "Other operating systems".A new kernel may mean that the number has to be revised again, but often the new kernel does not add a new line to menu.lst, as in the last update, where the old and new were both 2.6.24-19.  When the 19 changes to 20 a new line will be added and you will still need to edit menu.lst.

You could always lock the kernel version, of course, and then just check occasionally, when you are around, if a new one is available.  Then there will be no system edits of the file to mess up your default boot number.

---

### Post by alt3rn1ty on 2008-08-29
:) Thanks ajgreeny, good idea with locking the kernel version, my only concern with doing something like that would be if other updates depended on the new kernel, but then I presume a version check would prevent such installations happening until I unlocked/updated the old kernel. And I am not so concerned with updates happening as soon as released with Ubuntu as I was with XP. Off to play with the desktop. Thanks again :KS

---

### Post by alt3rn1ty on 2008-08-29
One further question, could a check for dual boot entries during updates be implemented to re-insert XP and the default os selection?, ie who  would we suggest such a thing to.

---

### Post by felker2 on 2008-08-29
Do you mean that with a new, extra kernel in the menu.lst, your default WindowsXP lower in the list is not default anymore?

If so: I had the same problem, and then played with "savedefault" in menu.lst: See [http://www.gnu.org/software/grub/manual/grub.html#savedefault](http://www.gnu.org/software/grub/manual/grub.html#savedefault)

HTH

---

### Post by alt3rn1ty on 2008-08-29
No, heres what I started with..
-------------------------------------------------------------------------
# array will desync and will not let you boot your system.
default		0

## timeout ... snip

.... true or false
# savedefault=false

## ## End Default Options ##

splashimage=(hd0,5)/boot/grub/soft-tux.xpm.gz

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=af72899f-8fc6-43d7-ad32-c370d3b1819a ro quiet vga=773 splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
lock
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=af72899f-8fc6-43d7-ad32-c370d3b1819a ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1
-----------------------------------------------------------------------

Which I changed to the following....

-----------------------------------------------------------------------
# array will desync and will not let you boot your system.
default		0

## timeout ... snip

.... true or false
# savedefault=false

## ## End Default Options ##

splashimage=(hd0,5)/boot/grub/soft-tux.xpm.gz

title		Microsoft Windows XP Home Edition          **<--- XP Moved**
root		(hd0,0)
savedefault
makeactive
chainloader	+1

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=af72899f-8fc6-43d7-ad32-c370d3b1819a ro quiet vga=773 splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
lock
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=af72899f-8fc6-43d7-ad32-c370d3b1819a ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

-----------------------------------------------------------

After the kernel update I had the following, no XP

-----------------------------------------------------------
# array will desync and will not let you boot your system.
default		0

## timeout ... snip

.... true or false
# savedefault=false

## ## End Default Options ##

splashimage=(hd0,5)/boot/grub/soft-tux.xpm.gz

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=af72899f-8fc6-43d7-ad32-c370d3b1819a ro quiet vga=773 splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
lock
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=af72899f-8fc6-43d7-ad32-c370d3b1819a ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

----------------------------------------------------------------
Noob mistake, followed by the kernel update detecting non-standard menu.lst pausing to give me 5 or 6 options as to what to do, having an idea this could really stuff up my installation I chose what seemed the safest bet to use the installers recommended menu.lst, which resulted in no XP option in grub at the next boot.

ajgreeny confirmed my suspicion that I should have in the first instance just changed default 0 to default 5 (in my case), instead of shifting the XP chainload up to first position in the list. But I did it this way so the family would be presented with XP as the top option. 

So my further question is for such noob linux adopters/plonkers (take your pick) as myself who want to keep XP first in the list, could kernel updates be made to recognise and preserve this after its necessary update/changes and who would we suggest that to.

P.S. Sorry about the long explanation on a resolved post but I am a bit green when it comes to explaining linux issues/terminology :)

---

