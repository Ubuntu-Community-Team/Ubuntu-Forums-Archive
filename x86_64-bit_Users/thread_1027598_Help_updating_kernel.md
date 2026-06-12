---
title: "Help updating kernel"
date: 2009-01-01
forum: x86 64-bit Users
---

### Post by bonestonne on 2009-01-01
Alright, maybe i'm just being a complete idiot right now, but this is really not working too well.

I'm running a pretty nice system (specs in the sig) and right now, i'd love to get hardware acceleration out of my 9600GT. i went in and i found the most recent nvidia beta drivers 180.11, and i tried installing them.

well, during the boot process, it fails to initialize the driver, thus giving me crap for graphics. movies play well, i can't complain, but i have zero graphics acceleration for the OS. this is really annoying because it's just something i'd like to have on my nice graphics card (i didn't pay $120 for it to not work).

i get a GCC error during the nVidia install process about how the kernel was compiled with GCC 4.2 and now i'm running 4.3, and the newer version refuses to compile anything because of the old kernel.

right now i'm running 2.6.24-16-generic, and i guess if i want that damned nVidia install to work, i need to update the kernel.

what can i do to get this to work? i've googled it all day, and if i had found an answer i wouldn't have come here.

also, on a side note, i'm running dual monitors, so i'd prefer to not lose use of both heads on my graphics card, it's quite useful.

thanks in advanced for any help regarding this, no one has ever posted a tutorial on how to update the damn kernel. ever.

-bonestonne

---

### Post by drs305 on 2009-01-01
If you merely want to isntall a newer kernel, it is very simple. I'll stick to gui methods so you will use synaptic. Open synaptic, make sure you have the main repositories enabled, then look for "linux-image". If you select "linux-image" it will automatically download the most recent kernel. You could also look for a particular kernel. On my VM setup, Hardy's most recent generic kernel is linux-image-2.6.24-22-generic. You could mark that for installation or use the 'linux-image' option mentioned earlier.

Once you have the newest kernel on your machine, you have to make sure grub is set up to use it. My recommendation is to install and use StartUp-Manager. It's a gui app that edits grub's menu.lst without you having to manually edit the file and possibly make errors. 

To install StartUp-Manager (SUM):
```

sudo apt-get install startupmanager

```

To run it: System, Administration, StartUp-Manager (or 'startupmanager' in terminal).
In the first tab, select the kernel you wish to use by selecting "Default operating system". It will display all available kernels. Select the one you want to use. Reboot to start using the new kernel.  (Note: if you have manually altered the previous kernel or manually added certain drivers you may have to reinstall them with the new kernel).

To check which kernel you are running after rebooting:
```

uname -r

```

SUM has many other options. For a tutorial, refer to the link in my signature line.

---

### Post by bonestonne on 2009-01-01
well, i did all that, but the kernel hasn't changed.

i wish it was more of an option for me to try reinstalling, but i just can't do that, it would ruin grub, and i have a triple-boot setup, with one broken install, and i absolutely can't lose access to my XP partition either, that would just rip.

I used a Jaunty repo to install the 180.11 driver, then removed the repo aftewards to prevent conflict.

during boot there's a DKMS error about a failed installation of the driver and it fails to initialize.

---

### Post by drs305 on 2009-01-01
Did you see the new kernel displayed on grub's menu.lst during boot (and did you select it if you manually log on)?

If you automatically boot to the Desktop, did you change grub's settings to use the latest kernel?

Did you run "uname -r" to check the running kernel?

Is the newer kernel downloaded to your computer?
```

sudo find /boot -name vmlinuz*

```

If you find a more recent kernel and can't get it to run, post your menu.lst and we may be able to see why you didn't boot to it.

---

### Post by stchman on 2009-01-01
If he want to run that 9600GT he will need to either:

Install Intrepid
Install EnvyNG
Install the drivers from Nvidia website.

The restrictred drivers present in Hardy do not support that card.  I recommend EnvyNG.

---

### Post by bonestonne on 2009-01-01
no, in grub i did not see a new kernel listed.

uname -r still gives me the same result it did.

I am running Intrepid.

I am trying to install the nVidia drivers, with no success.

I have tried using Envy in the past with no success either.

```
~~~~~@UbuntuWorkstation:~$ sudo find /boot -name vmlinuz*
[sudo] password for james: 
/boot/vmlinuz-2.6.27-7-generic
/boot/vmlinuz-2.6.24-16-generic
/boot/vmlinuz-2.6.27-9-generic

```

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
timeout		30

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
# kopt=root=UUID=0941cc78-6481-4753-93ea-827c652cc38a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=0941cc78-6481-4753-93ea-827c652cc38a all_generic_ide
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=0941cc78-6481-4753-93ea-827c652cc38a ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Apple OS X
root		(hd0,0)
savedefault
makeactive
chainloader	+1

title		Windows XP Professional x64 Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1

```

I have no edited my boot menu since i updated to Intrepid, which was a while ago. I've been ignoring the OS X partition as well because of the 9600GT with limited compatibility i'm unable to boot that as well.

i'm currently downloading 9.04 alpha 2 to test on a different machine (not x64), maybe i can install the kernel from that CD?

i also just noticed that my boot menu says that it's 8.04, however i'm completely sure that I am running Intrepid (System Monitor says so).

---

### Post by blazercist on 2009-01-01
What are the exact steps you used to install the Nvidia drivers?  Perhaps you did somethign wrong because I use those same drivers and have a 9600GT as well and there is no reason to screw around with the kernel to make it work.

---

### Post by bonestonne on 2009-01-01
well, i downloaded the driver straight from nVidia's website to my desktop. from there, i renamed it to NVIDIA3 (to keep the name short, as well as easy for me to recognize against older versions.

ctrl + alt + F2, to leave the UI

sudo /etc/init.d/gdm stop (to shut down gnome, so i can reconfigure the Xserver).

sudo sh NVIDIA3.run (the name of the file)

from there, i enter the installation.

during the installation process, first it tells me that there's no usable pre-configured file i can download from nVidia's FTP site, so i naturally continue. from there, i get straight to a problem where the version of GCC+ is newer than the version that was used to compile the kernel, and it rejects the older versions. once i pass that, the installation fails, i go back to the shell and type:

sudo /etc/init.d/gdm start

and i log back in to my current desktop, with no new drivers.
---------
those are the steps i've seen used in countless other forums and threads regarding how to install the driver.

---

### Post by blazercist on 2009-01-01
It seems like you are installing the drivers correctly, although you've missed a step in the process ```
sudo chmod +x NVIDIA3
```

But, I don't think that's your problem as it seems that the installer executes as normal.  

Perhaps you should try to downgrade GCC?  Have you upgraded GCC?  Have you enabled any third party repositories that may have had a newer version of GCC?  What kernel are you using? Is it the standard Ubuntu kernel or is it custom?

---

### Post by bonestonne on 2009-01-01
to my knowledge, i haven't had any reason to upgrade GCC unless it was part of one of Ubuntu's automatic update, which i do regularly, whenever available.

the kernel i'm running is 2.6.24-16-generic, it is not custom, and i haven't tweaked it at all. on my older computer, i used to have a modified kernel, but it was a much slower computer (Pentium 3 Xeon Cascades [2x 733mhz]). this rig has just had vanilla Ubuntu x64 installs since 7.10? i guess it was then.

how can i go about downgrading GCC? i tried using Synaptic for it, but that didn't work i guess, how could i use apt?

---

### Post by bonestonne on 2009-01-04
bump

I had tried to install Virtual Box today...what a problem. I need some type of Virtualization software available (i use VMWare Workstation 6 in XP, VMWare Fusion is OS X) but i can't get Virtual Box or VMWare to run in Ubuntu.

I might have come across the source of my problems, but i need hel in solving it.

in my /boot folder, it contains the 2.6.27-9 kernel, however if i edit my menu.lst to use that for booting, it does not work. I simply get a Panic upon boot. i was able to get back into the system by editing grub after boot to the old kernel, and i then edited the menu.lst so that i wouldn't have to keep doing that.

How can i edit the menu.lst that's posted above to use the 2.6.27-9 kernel? do i have to update grub? how can i do that?

---

### Post by Yellow Pasque on 2009-01-04
IMHO, you're going about this all wrong. Instead of trying to roll a new kernel, you should be focused on why you have gcc 4.3 installed on Hardy. gcc 4.3 is not part of the standard Hardy/update repos, so you either got it from a 3rd-party repo, installed it manually, or the Nvidia program is detecting it when it's not actually installed.

What does this command return?
```
file /usr/bin/gcc
```

---

### Post by bonestonne on 2009-01-04
[http://www.kwikpiks.com/files/84/Screenshot-boot%20-%20File%20Browser.png](http://www.kwikpiks.com/files/84/Screenshot-boot%20-%20File%20Browser.png)

[http://www.kwikpiks.com/files/84/Screenshot-System%20Monitor_thumb.png](http://www.kwikpiks.com/files/84/Screenshot-System%20Monitor_thumb.png)

```
/usr/bin/gcc: symbolic link to `gcc-4.3'
```

i don't think the kernel successfully updated when i updated to 8.10.

---

