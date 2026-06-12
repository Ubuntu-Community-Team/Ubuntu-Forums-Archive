---
title: "The first post - total noob - some noob problems"
date: 2008-02-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by ZoxX on 2008-02-10
I installed Ubuntu v7.10 amd64 with no problems. Dual boot, Windows XP Home SP1 and Ubuntu (25 GB + 800 MB swap). CPU is Athlon64 3000+, MSI MB. HDD 120 GB (Windows System partition) + 320 GB (Ubuntu nad Windows data). 1.5 GB RAM. ATI Radeon Sapphire graphics, 256 MB. E-MU 0404 PCI audio interface.
Internet connections works fine. Firefox restore (via FEBE from Windows) was very easy.
OpenOffice works fine.
Now I have some stupid noob problems.
1. GRUB
I would like to configure the boot. Put Windows at the beginning as my default. I tried to edit /boot/grub/menu.lst but I wasn't able to do it (GUI Text Editor and vi). However I made a copy of my menu.lst in the /. Tried command line
[FONT="Courier New"]cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
cp /menu.lst /boot/grub/menu.lst[/FONT]
It didn't work.
[FONT="Courier New"]ls -asli /boot/grub/menu.lst[/FONT]
shows that the user who can w is root. Tried
[FONT="Courier New"]su root[/FONT]
but I don't know the password (administrator password doesn't work).

2. Installing Thunderbird
I downloaded the program, unpack it. Now what? I found Readme file, but there is nothing of concern there. Tried to start run-mozilla.sh (both Run and Run in terminal) but nothing happened. What am I supposed to do?

3. Audio
The previous problems are very simple I guess. As far I found so far there is no way to use E-MU audio interface within Ubuntu. I don't expect to record, mix, and master audio just to listen the music.

Note: I'm new to Ubuntu but I have some 20 years of experience with Unix (SCO and AIX) so I can write scripts and use vi.

---

### Post by solar george on 2008-02-10
Under ubuntu you must use sudo instead of su - it will only require your password not the superuser one.

---

### Post by luctor on 2008-02-10
welcome to Ubuntu !

you don' t need to change the order of the grub entries. you can edit the first boot option.
look for "default 0" change that to the desired boot entry (probably 2 in your case)
also handy is to change to timeout and to the disable hiddenmenu

here's my /boot/grub/menu.lst 
```

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
**default         0**

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         30

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
**#hiddenmenu**

#A splash image for the menu
splashimage=(hd0,1)/boot/grub/splashimages/fiesta.xpm.gz


## ## End Default Options ##

title           Ubuntu 7.10, kernel 2.6.22-14-rt
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-rt root=UUID=9e29dce3-d2b0-465a-8d0b-48d7532bacc8 ro quiet splash vga=791
initrd          /boot/initrd.img-2.6.22-14-rt
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-rt (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-rt root=UUID=9e29dce3-d2b0-465a-8d0b-48d7532bacc8 ro single
initrd          /boot/initrd.img-2.6.22-14-rt

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=9e29dce3-d2b0-465a-8d0b-48d7532bacc8 ro quiet splash vga=791
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=9e29dce3-d2b0-465a-8d0b-48d7532bacc8 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows Vista/Longhorn (loader)
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```

install thunderbird by installing mozilla-thunderbird (use Synaptic or commandline "sudo apt-get install mozilla-thunderbird") don' t bother downloading stuff :-)

---

### Post by raaki_88 on 2008-02-10
first of all as you are familiar with previous unix experience is an added advantage 

so download the following drivers from 

[http://www.alsa-project.org/main/index.php/Downloade](http://www.alsa-project.org/main/index.php/Downloade) site below

and you need to have a g++ library and curses library by synaptic

$sudo synaptic

and just search

you will find this

after this extract the downloaded packages and for every package execute the following commands

for extraction

$tar xjf alsa-<package name>

after extracting

cd to that

$cd alsa-<extracted package>

$./configure
$make
$sudo make install

that's it you can rock now

---

### Post by ZoxX on 2008-02-10
> **solar george said:**
> Under ubuntu you must use sudo instead of su - it will only require your password not the superuser one.
Thank you, I'll try this.

---

### Post by ZoxX on 2008-02-10
> **luctor said:**
> install thunderbird by installing mozilla-thunderbird (use Synaptic or commandline "sudo apt-get install mozilla-thunderbird") don' t bother downloading stuff :-)
Thank you, I did what you typed, and installed Thunderbird with no problem.
I'll try to play with the grub later.

---

### Post by logos34 on 2008-02-10
> **ZoxX said:**
> 
1. GRUB
I would like to configure the boot. Put Windows at the beginning as my default. I tried to edit /boot/grub/menu.lst but I wasn't able to do it...

If you just have the standard generic kernel, recovery kernel, and memtest, then for windows this will probably work:

**default 4**

(it's probably the fifth 'title' line down.  Grub starts counting from '0')

More on grub menu.lst options [here.]("http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc")

---

### Post by ZoxX on 2008-02-10
> **raaki_88 said:**
> first of all as you are familiar with previous unix experience is an added advantage 

so download the following drivers from 

[http://www.alsa-project.org/main/index.php/Download](http://www.alsa-project.org/main/index.php/Download) 

Thank you too. I'll try this later. I found a lot of drivers and everything at the link above.

---

