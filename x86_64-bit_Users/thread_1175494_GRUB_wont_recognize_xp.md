---
title: "GRUB wont recognize xp"
date: 2009-06-01
forum: x86 64-bit Users
---

### Post by DjordjeRnR on 2009-06-01
First of all sory if similar thread exist, I have done some searching and did not find anything useful for me.
Second please sory on my bad english
and finaly I must say that I am a beginer to Ubuntu.


So here is a problem. I must instal Ubuntu and widows XP on a 64 AMD coputer. The problem is I can only make one of them working, and I need them booth.
I have tryed it this way. Instaled XP, the hard disk was splited on 2 parts, on D is data and on C was xp, I have splited C on 3 parts, one for xp, second for ubuntu and third for swap. After I finished instaling xp, I instaled Ubuntu, Buth when I restart it, it loads GRUB and then counts for 3 seconds and if I dont pres esc it loads ubuntu, and if I pres esc it shows me the grub meny, and on it there is Ubuntu, Ubuntu recovery mode, and ubuntu memory test. No XP.

What to do?:(

---

### Post by munky99999 on 2009-06-01
[http://ubuntuforums.org/showthread.php?t=1174605](http://ubuntuforums.org/showthread.php?t=1174605)

Essentially you need to make sure the windoze boot is aimed at the correct hardrive-partition.

sudo gedit /boot/grub/menu.lst 

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/) may also help in situations in the future when perhaps you cant get on the net for help.

---

### Post by DjordjeRnR on 2009-06-01
when I tupe that comand in terminal it says



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
# kopt=root=UUID=8999c5a2-784f-45c6-90a7-32441dbfc20a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=8999c5a2-784f-45c6-90a7-32441dbfc20a

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

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

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

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		8999c5a2-784f-45c6-90a7-32441dbfc20a
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=8999c5a2-784f-45c6-90a7-32441dbfc20a ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		8999c5a2-784f-45c6-90a7-32441dbfc20a
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=8999c5a2-784f-45c6-90a7-32441dbfc20a ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		8999c5a2-784f-45c6-90a7-32441dbfc20a
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by DjordjeRnR on 2009-06-01
I dont know what to do next ?

 :popcorn:

---

### Post by munky99999 on 2009-06-01
Essentially you can ignore the majority of the file. the very end is where it matters.

Put something like.

```
title Microsoft Windoze
rootnoverify (hd0,0)
savedefault
makeactive
chainloader +1 
```

```
title Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid 8999c5a2-784f-45c6-90a7-32441dbfc20a
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=8999c5a2-784f-45c6-90a7-32441dbfc20a ro single
initrd /boot/initrd.img-2.6.28-11-generic

title Microsoft Windoze
rootnoverify (hd0,0)
savedefault
makeactive
chainloader +1 

title Ubuntu 9.04, memtest86+
uuid 8999c5a2-784f-45c6-90a7-32441dbfc20a
kernel /boot/memtest86+.bin
quiet
```

The main concern is the rootnoverify (hd0,0)

hd0,0 is the location of the windoze hardrive.
It could be hd1,0 or hd2,0


The thread I linked has a method of figuring out which.

---

### Post by DjordjeRnR on 2009-06-01
Do you say I should modify that list with that string and save it ?

---

### Post by DjordjeRnR on 2009-06-01
is it ok like this ?

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
# kopt=root=UUID=8999c5a2-784f-45c6-90a7-32441dbfc20a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=8999c5a2-784f-45c6-90a7-32441dbfc20a

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

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

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

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		8999c5a2-784f-45c6-90a7-32441dbfc20a
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=8999c5a2-784f-45c6-90a7-32441dbfc20a ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title Microsoft Windoze
rootnoverify (hd0,0)
savedefault
makeactive
chainloader +1

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		8999c5a2-784f-45c6-90a7-32441dbfc20a
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=8999c5a2-784f-45c6-90a7-32441dbfc20a ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		8999c5a2-784f-45c6-90a7-32441dbfc20a
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST



I hawe now microsoft windoze i the grub buth gwhen I pres enter it says: Eror 13 Invalid or unsuported excautable format pres any key to continue

---

### Post by DjordjeRnR on 2009-06-01
I have done this



 Re: Windows Booting Problem
Code:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows XP Professional
rootnoverify (hd0,0)
map          (hd0) (hd2)
map          (hd2) (hd0)
chainloader  +1

Open a terminal and run
Quote:
gksu gedit /boot/grub/menu.lst
Scroll down to the bottom and change your windows entry to the above.




And it does the same 13 eror

---

### Post by DjordjeRnR on 2009-06-01
""I think we're all trying to guess the partition containing GRUB.

Try the following:
1) sudo -i
2) grub
3) find /boot/grub/stage1
4) quit

Command 3) should return something like (hd1,0) or (hd2,0) or whichever "drives" have GRUB installed.""


It says (hd0,0)

---

### Post by msriram on 2009-06-01
You can check ```
df -h
``` and ```
fdisk -l
``` to give you the disk used for windows... once you find it out

change in the **menu.lst** or **grub.conf** file in **/boot/grub/** directory as follows






```
title Microsoft Windows
rootnoverify (hd0,0) #<<-- Change this part
savedefault
 
```

---

### Post by DjordjeRnR on 2009-06-01
df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              36G  2.6G   32G   8% /
tmpfs                 245M     0  245M   0% /lib/init/rw
varrun                245M  104K  245M   1% /var/run
varlock               245M     0  245M   0% /var/lock
udev                  245M  148K  245M   1% /dev
tmpfs                 245M  836K  244M   1% /dev/shm
lrm                   245M  2.7M  242M   2% /lib/modules/2.6.28-11-generic/volatile



?

---

### Post by DjordjeRnR on 2009-06-01
I am not so sure what next should I do ?

---

### Post by DjordjeRnR on 2009-06-03
Any help please :popcorn:

Will it help if I format the whole hard disk, or try it with some other xp cd ???

---

