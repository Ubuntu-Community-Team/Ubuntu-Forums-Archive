---
title: "Problem booting to Hardy Heron 8.04, Help please :("
date: 2008-08-22
forum: x86 64-bit Users
---

### Post by mmzdaniel on 2008-08-22
EDIT: read page 2, I resolved the first issue, and screwd i up again, this time it gives me Busybox and the following error:
```
error while loading shared libraries: libfuse.so.2
```
Help Please :D

End of edit :O

Hello,
I have been using Ubuntu 64Bit on My AMD for about a month now,
and yesterday i wanted to costumize it, everything went well until
I tried to install [Fingerprint]("http://www.gnome-look.org/content/show.php?content=50468"). I carefully followed the instructions, rebooted, and when the machine was rebooting it suddenly stop with all the lines of code on the screen. 
i waited for about 5 minutes and nothing changed, so i just hit the reset button, booted it into Ubuntu but it didn't load.
all I got was "BusyBox" and "initramfs". I then tried to press Ctrl+Alt+F1 and it said i should boot into windows, and run Chkdsk /r. i did, but it didn't help. I booted into windows, started playing with My "menu.lst" file, in the grub directory, but didn't help much. Could you people please help me? otherwise ill have to switch and stay with XP, and i believe you guys know why thats a bad thing :(

Here's My "menu.lst" file:
```
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
# kopt=root=UUID=C2F8D0A0F8D0944F loop=/ubuntu/disks/root.disk ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)/ubuntu/disks

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

title           Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=C2F8D0A0F8D0944F loop=/ubuntu/disks/root.disk ro quiet splash locale=en_EN	 
initrd          /boot/initrd.img-2.6.24-19-generic
boot

title           Ubuntu 8.0.4.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=C2F8D0A0F8D0944F loop=/ubuntu/disks/root.disk ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,0)/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=C2F8D0A0F8D0944F loop=/ubuntu/disks/root.disk ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=C2F8D0A0F8D0944F loop=/ubuntu/disks/root.disk ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)/ubuntu/disks
kernel		/boot/memtest86+.bin

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
chainloader	+1

```
Sorry about the amounts of code but I figured no one would download it, lol...
One last thing, i installed ubuntu with Wubi, alongside Xp. 
Thanks again.

---

### Post by Ehtetur on 2008-08-22
> **mmzdaniel said:**
> 

title           Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)/ubuntu/disks

title		Microsoft Windows XP Home Edition
root		(hd0,0)

Hi mmzdaniel,

I've heard of, but I'm not familiar, with wubi... so maybe it's just that wubi did the weird thing I see in /boot/grub/menu.lst...

The issue I see is that it's telling grub that both the linux kernel and windows are on the same partition... 

If you modified root (hd0,0) in ubuntu's title, then you'll need to change it back..

---

### Post by mmzdaniel on 2008-08-22
i didnt modify... should i try to use it as first hdd (only got 1)
and second partition? would be like, (0,1)?

---

### Post by Ehtetur on 2008-08-22
> **mmzdaniel said:**
> i didnt modify... should i try to use it as first hdd (only got 1)
and second partition? would be like, (0,1)?

Yup, that's right...  if you didn't mod the line, then wubi must of... strange, but maybe wubi puts the kernel onto the windows partition...?

You could change menu.lst just to check.. If it's wrong, the "only" thing that will happen is that the kernel doesn't load and ubuntu doesn't start...
I say "only" because it won't corrupt your install...

Before you make the change though, I would run this command to see all your partitions... look for /boot or /
> sudo fdisk -l

---

### Post by mmzdaniel on 2008-08-23
ill try, remember i cant access a terminal, just busybox...
ill try from a LiveCD session too, and see if it works.

EDIT: Fail. it seems ubuntu and Xp ARE on the same partition,
i do find it logical because, to access the grub files i go to
"C:\ubuntu\disks\boot\grub".
Help :(

---

### Post by mmzdaniel on 2008-08-23
Sorry. BUMP.

---

### Post by Sef on 2008-08-23
> EDIT: Fail. it seems ubuntu and Xp ARE on the same partition,

Wubi is just a file on Windows, so that would be normal.

Also do not bump unless 24 hours has gone by.  Threads may get answered very quickly or very slowly.

---

### Post by unca.paka on 2008-08-23
The way I understand it, Wubi installs Ubuntu onto a virtual disk on the same partition, unless another drive is specified.

I have been seeing some posts where it likes to jack menu.lst though.

---

### Post by mmzdaniel on 2008-08-24
> **Sef said:**
> Wubi is just a file on Windows, so that would be normal.

Also do not bump unless 24 hours has gone by.  Threads may get answered very quickly or very slowly.

Right, thanks for not locking / warning... its just that I'm with this problem for quite a lot of time and I couldent solve it, I'm not very experienced with Ubuntu but I did use my common sense.
Oh and btw, 
Help guys :(

---

### Post by mmzdaniel on 2008-08-25
ok now a day has passed so... Uber bump.:(

---

### Post by Ehtetur on 2008-08-25
> **mmzdaniel said:**
> ok now a day has passed so... Uber bump.:(

mmzdaniel - I would suggest that you boot to runlevel 1 and change your usplash from fingerprint back to the ubuntu default.

First boot into ubuntu and at grub's kernel selection menu, arrow down to the recovery stanza and press the letter **e**
> Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)

next, arrow down to the kernel line (yours may look a bit different) and press the letter **e** :
> kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=62020ee0-ad36-45c3-84c1-6f5e3c690855 ro single

Now you should be in edit mode. Add a space and the word **nosplash** to the very end of the line so it looks like this:
> kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=62020ee0-ad36-45c3-84c1-6f5e3c690855 ro single **nosplash** 

Press the letter **b** to boot into runlevel 1

Your screen should have a bunch of text zooming by.. but then eventually, you'll see a menu. Select the following and press enter:
> Root          Drop to root shell

You should (hopefully) now be staring at a root prompt.
Note: everything you did up 'til now is temporary. But the following step permanent.. or at least until you decide to change usplash again :twisted:
Enter this text at the prompt and press enter:
> update-usplash-theme usplash-theme-ubuntu

Change to graphical mode and you should get the login prompt GUI
> telinit 5

dude... I really really hope this works for you because I'm kinda thinking that if it doesn't, your next step may be to reload.

Good luck!!

---

### Post by mmzdaniel on 2008-08-27
Thank you so much, i think this will work!
Problem is, how do I get to the Grub menu? I'm using Wubi. anyways, I'll try changing these in My menu.lst from windows, and then from slax. If those fail, I'll edit this post.
This worked! it actually worked! all  i had to do myself is find out that by pressing Esc i get to grub... THANKS!
now ill still try to install that splash, and if i fail, ill have a backup :D
EDIT: ok now i screwd up... this time i tried to install Fingerprint with
StartUp Manager, and now it boots into busybox again. it doesnt complain about the usplash anymore, but now it says "error while loading shared libraries: libfuse.so.2" also i tried to use your solution again, didn't work...

---

### Post by mmzdaniel on 2008-08-28
Sorry but i guess I'll have to bump again... or open a new topic.

---

