---
title: "Black Screen After Grub"
date: 2008-01-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by ronb94 on 2008-01-25
Hello
I have a problem in ubuntu 7.10 64bit.After ther grub screen wherei choosed ubuntu i am getting a black screen until the login screen.I am not getting this loading picture:
[IMG]http://www.dsl.sk/images/articles/2007-05-06-ubuntu-1.png[/IMG]
I tried some thing like change the kernel line in /boot/grub/menu.lst but it didnt helped. Now i am  getting after the grub running comands but i am not get the loading picture.
How can i do after grub i'll see the loading picture.
Thanks

---

### Post by rosegarden78 on 2008-01-25
I know it sounds pedantic but you could try a fresh install of Ubuntu GG 7.10 as described [here]("http://ubuntuforums.org/showthread.php?t=677959") and [here]("http://ubuntuforums.org/showthread.php?t=385981").  Good luck!  You might need to mount your partition and USB drive from the terminal to backup your /home folder.

---

### Post by ronb94 on 2008-01-26
Thanks for reply.
I just reinstalled ubuntu but still i am not getting the loading screen.while using the livecd there is no loading screen too.

---

### Post by rabbit73 on 2008-01-26
I have the exact same issue. When I installed 64bit it disappeared. I totally hosed my system and had to do a totally fresh install and it didn't come back then either. When I upgraded my computer and moved over the hard drive it showed up (was running 32bit 7.04), but under 64bit it's gone. Monitor turns off too. nvidia 8400GS if that helps.

---

### Post by prince_niceguy on 2008-01-27
seems like usplash issue.

install sysv-rc-conf from synaptic

and in the terminal run the command

$ sudo sysv-rc-conf

make sure usplash is having a check mark for 2, 3, 4, and 5.

---

### Post by ronb94 on 2008-01-27
I did:
> install sysv-rc-conf from synapticin the usplash line the 2,3,4,5 are marked.But still not working

---

### Post by prince_niceguy on 2008-01-27
install startupmanager from synaptic. it will come as one option under system --> aministration. Use that and try changing the desktop back grounds. post your /boot/grub/menu.lst. will help in knowing where the problem is.

---

### Post by Ravanous on 2008-01-27
Are you using an ATI video card? 

If youd do, then try installing the officilal ATI drivers by downloading the latest version from AMD and following the instructions on the cchtml wiki.

I too was having the same problem, doing so fixed it.

---

### Post by skapocalyptic on 2008-01-27
I was having the same trouble after I switched from Ubuntu Studio to Gutsy 7.10

I loaded the Startup-Manager from synaptics, and changed the color depth from 8bits to 24, and adjusted the resolution from 800x600 to 1024x768

Once I made these adjustments, the splash screen once again displayed.

Hope this works for you.

---

### Post by ronb94 on 2008-01-28
> Are you using an ATI video card?

Nope i am using Nvida and the drivers are installed.
> I loaded the Startup-Manager from synaptics, and changed the color depth from 8bits to 24, and adjusted the resolution from 800x600 to 1024x768
I did, its not helping me.
Here is my /boot/grub/menu.lst:
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
# kopt=root=UUID=349c3a0c-ac74-4639-8651-43e31e30c5bd ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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
# defoptions=quiet splash vga=795

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
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=349c3a0c-ac74-4639-8651-43e31e30c5bd ro quiet splash vga=795
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=349c3a0c-ac74-4639-8651-43e31e30c5bd ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,2)
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

```
And again its not the splash screen. Its the laoding screen that comes after the grub menu.
Thanks

---

### Post by prince_niceguy on 2008-01-28
have you tried reinstalling the usplash package? if not try doing that. also add some more usplash and using startup manager change the usplash to newly downloaded one and then try to see if it is working or not.

---

### Post by themusicwave on 2008-01-28
This is really simple, but do you have a CD in the drive?

I notice this happens to me sometimes when I leave a cd in at bootup.  Ejecting it and hitting CTR-ALT_DEL fixes it....weird...

I have a dell Insprion E1505 with Nvidia card.  Just thought it might help.

---

### Post by ohmycar on 2008-01-29
I had the same problem, this is what I did


Boot into the Ubuntu recovery mode so you get a terminal, then type

```
sudo nano gedit /boot/grub/menu.lst
```

sometimes at first it is a black document, just press CTRL+X and it should take you to your menu.lst

in there look for where it says

```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=349c3a0c-ac74-4639-8651-43e31e30c5bd ro quiet splash vga=795
```


delete the "quiet splash vga=795" part and press CTRL+X to save it.

hope that helps! let me know.

---

### Post by hajk on 2008-01-29
Guys, guys... doesn't anybody think of checking the bugs in Launchpad? The problem with GeForce 8xxx series cards and Ubuntu AMD64 splash (in Gutsy, but also earlier in Feisty) has been around for a while, see e.g. bugs #140759 and #179642. Let's hope that it will be solved in the upcoming Hardy release, but until then changing "splash" to "nosplash" in the boot options at least provides some boot messages to look at before the gdm login page appears... Reinstalling Ubuntu? Geez, what a waste of time...

---

### Post by skapocalyptic on 2008-01-30
comparing your menu.lst to mine, there seems to be only one difference...

i have a line which reads like this:
```
# defoptions=quiet splash vga=792
```

whereas yours look like this:
> # defoptions=quiet splash vga=795

I'm not confident that this is the source of your problem, and I am using an ATI integrated graphics card, but that is the only difference I could see.

---

### Post by yellowbread on 2008-02-02
Here's what has worked for me:

1. Edit /etc/initramfs-tools/modules.
Add the lines:

fbcon
vesafb

2. Edit /etc/modprobe.d/blacklist-framebuffer.
Comment out the line vesafb by putting # at the beginning of the line:

#vesafb

3. Edit /etc/usplash.conf to match the resolution you have specified with vga=*** in menu.lst.
For example with vga=795 you want usplash.conf to have the lines:

xres=1280
yres=1024

Here's a chart giving many of the codes:

```
Colours   640x400 640x480 800x600 1024x768 1152x864 1280x1024 1600x1200
--------+--------------------------------------------------------------
 4 bits |    ?       ?      770       ?        ?        ?         ?
 8 bits |   768     769     771      773      353      775       796 
15 bits |    ?      784     787      790      354      793       797 
16 bits |    ?      758     788      791      355      794       798 
24 bits |    ?      786     789      792       ?       795       799 
32 bits |    ?       ?       ?        ?       356       ?
```

4. In a terminal run:

sudo update-initramfs -u

5. Reboot.

---

### Post by pyxu619 on 2008-02-03
> I was having the same trouble after I switched from Ubuntu Studio to Gutsy 7.10

I loaded the Startup-Manager from synaptics, and changed the color depth from 8bits to 24, and adjusted the resolution from 800x600 to 1024x768

Once I made these adjustments, the splash screen once again displayed.

Hope this works for you.

that method worked for me too!

---

### Post by GhostlyLeech on 2008-02-04
I'm having this exact same problem. 
Did the original poster fix this problem?

---

### Post by Bear on 2008-02-04
> **pyxu619 said:**
> that method worked for me too!

Worked for me too. Thanks.

---

