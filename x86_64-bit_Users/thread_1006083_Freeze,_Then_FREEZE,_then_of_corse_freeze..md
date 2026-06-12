---
title: "Freeze, Then FREEZE, then of corse freeze."
date: 2008-12-08
forum: x86 64-bit Users
---

### Post by eweb100 on 2008-12-08
Specs - Ubuntu 8.10 64 bit

At random times my ubuntu will just FREEZE for no reason. I will be on pigen and scrowling down my budy list and FREEZE, I will be chaning music on rhythmbox and FREEZE. And so forth, it seems that this happins ever 2 hours or so. I am about to go back to vita because i dont want to have to right my language arts essay over for the 3th time.. PLEASE HELP!

---

### Post by crazyness003 on 2008-12-08
which kernel are you running?

To check, run the terminal (Applications -> Accessories -> Terminal)
and c/p this in there ```
uname -a
```
That will give all sorts of info (inc. the kernel number)

---

### Post by eweb100 on 2008-12-09
Linux eric-desktop 2.6.27-9-generic #1 SMP Thu Nov 20 22:15:32 UTC 2008 x86_64 GNU/Linux

And its about every 30 minunites now...its getting worse

---

### Post by wfp on 2008-12-09
Try disabling compiz-fusion see if that helps. Turn desktop effects off if you have it enabled.

---

### Post by crazyness003 on 2008-12-10
Actually, i havent heard many good things about the 2.6.27-9 kernel. If you allow proposed updates in the Sources, you'll be able to upgrade to 2.6.27-10 (the one i have at the moment). This ***MIGHT*** be the culprit.

to enable proposed packages do this
System -> Administration -> Software Sources, enter you password in the gksu box Click the 'Updates' tab, and in the 'Ubuntu Updates' section, its the 3rd option: "Pre-Released Updates (intrepid proposed)." Im sure theres an easier terminal way to do it without typing in vim or gedit too (I think it uses sed and something else), but i dont know how to do it. this is the easiest way i can think of.

Then, run the update manager, and you'll get bombarded with an array of new, pre-released updates (including the new kernel). If you want install them all or just the kernel. When when you're dont, you can either disable the interpid-proposed again, or just keep them (this allows you to be a sort of 'beta tester')

Let us know what happens

---

### Post by eweb100 on 2008-12-10
I did what you said... the upgrade thing..

BUT when i did uname -a again it stil says 2.6.27-9-generic..

---

### Post by crazyness003 on 2008-12-10
you may have installed the new kernel, but have you loaded into it?
To do so, you must restart your computer. 
At the GRUB menu, you should see an extra 2 entries (one is regular boot, the other is recovery) with the new kernel number. 
Select the regular one with tne new kernel. 
If everything goes as should, you should boot into the new kernel and might not face freezes anymore.

If you dont see a GRUB list, hit Esc when you see "GRUB stage 1.5 loading"

---

### Post by eweb100 on 2008-12-10
I updated... But it seems that NOTHING has changed.... and it did to ask for a restart. is there a way that i can see that is it insatled and not wokring for some reson.. I did do alot of eding to the grub menue..Like chaning the normal names to like. ownage, and prownage.. Not shure if that matters

---

### Post by crazyness003 on 2008-12-10
to see if you've installed it, search for 2.6.27-10 in synaptic and see if any of the modules with that kernel number are installed. if not, select "linux-image-2.6.27-10" for install (it will ask you to install all other necessary packages).

So, heres a question, when you restarted, and logged into the 2.6.27-10 kernel, then issued the "uname -a" command, it still gave you the -9 kernel?

Can you post your /boot/grub/menu.lst?

---

### Post by eweb100 on 2008-12-10
YEs it still gave me, i reinsatled linux-image-2.6.27-10 and even after reinsaling and rebooting nothing happins

Linux eric-desktop 2.6.27-9-generic #1 SMP Thu Nov 20 22:15:32 UTC 2008 x86_64 GNU/Linux



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
# kopt=root=UUID=ecbf58ce-e26c-4dc3-8b2c-1ad0857f74f7 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=ecbf58ce-e26c-4dc3-8b2c-1ad0857f74f7

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

title		Ownage
uuid		ecbf58ce-e26c-4dc3-8b2c-1ad0857f74f7
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=ecbf58ce-e26c-4dc3-8b2c-1ad0857f74f7 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Phail ownage
uuid		ecbf58ce-e26c-4dc3-8b2c-1ad0857f74f7
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=ecbf58ce-e26c-4dc3-8b2c-1ad0857f74f7 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		R.A.M??
uuid		ecbf58ce-e26c-4dc3-8b2c-1ad0857f74f7
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		noob...
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by crazyness003 on 2008-12-11
ok, hang on im not understanding you. You reinstalled the linux-image-2.6.27-10 with the rest (linux-headers), but it didnt update your /boot/grub/menu.lst. Or did it just completely fail? 
If you have the new kernel installed (you can also check if you have this file: /boot/initrd.img-2.6.27-10-generic) then just make a new entry in yoru grub/menu.lst, copy everything of your old kernel entry, and just replace the "2.6.27-9" with "2.6.27-10"

Otherwise, i have a feeling you may have some issues with your install altogether. That first update i told you to do should have taken care of everything. Im not sure why it didnt.

---

### Post by eweb100 on 2008-12-11
Here is my DIR of /boot

eric@eric-desktop:~$ dir /boot
abi-2.6.27-10-generic	      memtest86+.bin
abi-2.6.27-7-generic	      System.map-2.6.27-10-generic
abi-2.6.27-9-generic	      System.map-2.6.27-7-generic
config-2.6.27-10-generic      System.map-2.6.27-9-generic
config-2.6.27-7-generic       vmcoreinfo-2.6.27-10-generic
config-2.6.27-9-generic       vmcoreinfo-2.6.27-7-generic
grub			      vmcoreinfo-2.6.27-9-generic
initrd.img-2.6.27-10-generic  vmlinuz-2.6.27-10-generic
initrd.img-2.6.27-7-generic   vmlinuz-2.6.27-7-generic
initrd.img-2.6.27-9-generic   vmlinuz-2.6.27-9-generic
eric@eric-desktop:~$ 

I fixed it by just chaning the 9 to a 10.. THANKS FOR YOUR HELP

SHould i delte some of the files listed above??

---

### Post by crazyness003 on 2008-12-12
[COLOR=Red][B]NO! 
[/B][/COLOR]The best way to get rid of some those is to use synaptic. You have to "remove" the options in synaptic.  Or you can check this out: [http://sandakith.wordpress.com/2007/11/25/remove-the-old-kernel-from-ubuntu/](http://sandakith.wordpress.com/2007/11/25/remove-the-old-kernel-from-ubuntu/)

Basically, type ```
sudo apt-get remove --purge 2.6.27-9-*
``` This will remove all the related packages that have to do with the "-9" kernel instance.

Its recomended you keep at least one old kernel (in your case the one that worked: 2.6.27-7). So removing the -9 would be your best viable option.

PS: if your problem is solved, please use the  	 	 		[Thread Tools]("http://ubuntuforums.org/showthread.php?t=1006083&nojs=1#goto_threadtools") 		 [IMG]http://ubuntuforums.org/images/misc/menu_open.gif[/IMG] at the top-right corner of this page and mark this thread as [SOLVED]. Thanks for playing and you're welcome. 

Join us next time for: z0mg, c0MP00t3R !Z t3h bR0K3Nz! :)

---

