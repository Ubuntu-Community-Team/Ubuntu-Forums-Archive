---
title: "Dual monitors nvidia settings reset on restart?"
date: 2007-07-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by seekdestroy16 on 2007-07-06
I just got dual monitors working in Ubuntu (desktop version) latest release from the ubuntu website. Though everytime I restart ubuntu the settings change back to just 1 screen and I have to set it back everytime... in the first place the nvidia driver did not detect the second monitor but now it does and it just resets on restart to the normal setting it was on before I set it to dual monitors. Anyone else have this problem? any help appreciated, TIA.

---

### Post by kuja on 2007-07-06
When you ran nvidia-settings were you running it as root? You need to (ie: kdesu/gksudo nvidia-settings). Also be sure to save your config before exiting.

---

### Post by seekdestroy16 on 2007-07-06
> **kuja said:**
> When you ran nvidia-settings were you running it as root? You need to (ie: kdesu/gksudo nvidia-settings). Also be sure to save your config before exiting.

I know I did click Save to Config (ie: xorg.conf) and I even previewed it and I saw it saved in there...
I dont exactly know what you mean by root, can you explain that?. Yeah I'm a noob, but a learning noob. Oh and a couple other questions, why does the boot manager show two of these?:
Ubuntu-generic
Recovery Mode 

I think theres only supposed to be one, and then windows xp below that since I'm dual booting. And, when I set the dual monitors to be configured correctly it is stretched over the screen aka the bottom and top toolbar. I want it to be like windows xp where its only in the main screen and the second screen is just a blank toolbar. Is this possible?. TIA.

---

### Post by kuja on 2007-07-06
This is a good page to read up on what I mean by "root" - [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

If you have two of each, you probably have two kernels installed, for example, you might have 2.6.20-15 and 2.6.20-16 both installed.

---

### Post by seekdestroy16 on 2007-07-06
> **kuja said:**
> This is a good page to read up on what I mean by "root" - [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

If you have two of each, you probably have two kernels installed, for example, you might have 2.6.20-15 and 2.6.20-16 both installed.

So how exactly do I choose the option to save as root?. If I have 2 kernals installed (which I probably do after reinstalling ubuntu so many times) how do I fix it?. And what about the stretched screen with dual monitors?.

---

### Post by kuja on 2007-07-06
You need to run the program as root to begin with to have root privileges. So, hit alt + f2, type in gksuo nvidia-settings (or kdesu nvidia-settings, whichever works), and Set your settings, then press save. That *should* do the trick. Whether the screen is "stretched is dependent on the options you chose. I personally uncheck the "xinerama" option box because I'd rather have my two monitors as two seperate desktops. To remove any "extra" kernels, you can do so from your package manager, (either synaptic or adept), open it, search for 2.6.20-15, then search for 2.6.20-16, if you see that both are installed, uninstall the packages related to the one  you aren't using ( probably 2.6.20-15).

---

### Post by seekdestroy16 on 2007-07-07
> **kuja said:**
> You need to run the program as root to begin with to have root privileges. So, hit alt + f2, type in gksuo nvidia-settings (or kdesu nvidia-settings, whichever works), and Set your settings, then press save. That *should* do the trick. Whether the screen is "stretched is dependent on the options you chose. I personally uncheck the "xinerama" option box because I'd rather have my two monitors as two seperate desktops. To remove any "extra" kernels, you can do so from your package manager, (either synaptic or adept), open it, search for 2.6.20-15, then search for 2.6.20-16, if you see that both are installed, uninstall the packages related to the one  you aren't using ( probably 2.6.20-15).

Ok got the dual monitors working...finally!. Which normally didnt work properly in the first place, basically I couldnt launch nvidia settings by typing gksuo or kdesu before nvidia-settings. I just went to terminal and typed sudo nvidia-settings and it launched and I made the changes in settings and they were the same on restart. Now I got a problem with the kernals, it does not give me the option in Synaptic Package Manager to uninstall the earlier version kernal. It just says "Mark for installation" and all the other options are greyed out. I'll do some googling while I wait for your response.

---

### Post by kuja on 2007-07-09
Sorry, I do believe that was a typo on my part, meant to type gksudo ... but, oh well, we all make mistakes. If it's saying "mark for installation" that means it's not already installed. If you showed me your /boot/grub/menu.lst I can figure out why you see multiple kernels there though.

P.S. I'm sorry I didn't reply again sooner, but I work weekends (long hours too)

---

### Post by seekdestroy16 on 2007-07-09
Hope this isnt too much. I understand that you work, I also work like full weekends and it sucks!:

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
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
# kopt=root=UUID=5ce3d21a-77cd-40e3-8586-fcef4545d0e3 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=5ce3d21a-77cd-40e3-8586-fcef4545d0e3 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=5ce3d21a-77cd-40e3-8586-fcef4545d0e3 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=5ce3d21a-77cd-40e3-8586-fcef4545d0e3 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=5ce3d21a-77cd-40e3-8586-fcef4545d0e3 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
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
title		Microsoft Windows XP Home Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1

---

### Post by kuja on 2007-07-10
It says you have linux-image-2.6.20-15-generic and linux-image-2.6.20-16-generic both installed, try removing the -15 one. If it's not installed (which I still think would be really, really odd), try running this command in a terminal: sudo update-grub

---

### Post by seekdestroy16 on 2007-07-10
> **kuja said:**
> It says you have linux-image-2.6.20-15-generic and linux-image-2.6.20-16-generic both installed, try removing the -15 one. If it's not installed (which I still think would be really, really odd), try running this command in a terminal: sudo update-grub

Alright!, I found the package "linux-image-2.6.20-15-generic" right where you'd said it would be and I completely removed it and then I restarted and saw only the 16-generic boot thingy and windows xp home edition in the list. Nothing went wrong at all, besides when I restarted before I even removed the package above. In this image shows the message I got, and I wrote down what it says if you cant read it in the image: Kernal direct manning tables up to 100000000 @ 8000-d000 

And it just stayed paused like that for awhile....I am guessing that it was something to do with both kernals installed onto the same partition. The reason for that issue is I was installing/uninstalling linux over and over again because I couldnt get anything to work. I learned my lesson, and hopefully it has been fixed now. Thanks alot for the help by the way, I am a new linux user and I love it already. It's fun screwing things up (but not purposely) and fixing those problems. If I have any more issues I'll post again if I can't find anything on google.

---

### Post by kuja on 2007-07-10
You should be able to safely ignore the Kernel direct mapping message, I think it says that while it's loading the kernel, or some such.

---

### Post by seekdestroy16 on 2007-07-11
> **kuja said:**
> You should be able to safely ignore the Kernel direct mapping message, I think it says that while it's loading the kernel, or some such.

It has been saying that, sometimes it just ignores it and keeps going. But now it does it and nothing happens, should I try waiting for more than 5 minutes? even though it shouldnt take that long...I think I really screwed it up by installing linux over and over again. I tryed a few google searches but I can't find anything with the code that I gave you in my previous reply. I probably typed it in wrong or something, but this is a tricky one. What should I do?

---

### Post by kuja on 2007-07-12
ack. Certainly doesn't sound good. Try following this procedure just to get things working again:

- Pop in the live cd
- Create a folder and mount your linux partition to it  (if you have multiple partitions for it (ie: seperate partitions for /boot and/or /home), mount them all in an appropriate location. If in doubt look here and if still confused ... ask :) : [https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount)
- pull up a terminal
** For sake of example I'm going to assume you mounted your linux root partition to /target **
```
sudo chroot /target
```
```
apt-get install --reinstall linux-image-2.6.20-16-generic
```

Then try booting again. Let me know how this goes.

---

### Post by seekdestroy16 on 2007-07-12
> **kuja said:**
> ack. Certainly doesn't sound good. Try following this procedure just to get things working again:

- Pop in the live cd
- Create a folder and mount your linux partition to it  (if you have multiple partitions for it (ie: seperate partitions for /boot and/or /home), mount them all in an appropriate location. If in doubt look here and if still confused ... ask :) : [https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount)
- pull up a terminal
** For sake of example I'm going to assume you mounted your linux root partition to /target **
```
sudo chroot /target
```
```
apt-get install --reinstall linux-image-2.6.20-16-generic
```

Then try booting again. Let me know how this goes.

Ok first I put the livecd in and it wouldnt let me create a folder called target...so I just restarted and tryed to boot linux regularly (not from the cd) and it worked but I still get the same message. I was able to mount the linux partition to /mnt but when i typed sudo chroot /mnt it said:
chroot: cannot run command `/bin/bash': No such file or directory
mike@mike-desktop:~$ 
So I dont really know what is wrong, though I was able to get a full picture of the boot message it gives me (and sometimes pauses on me forever) which is the pic in attatchment. Let me know what you think.

---

### Post by kuja on 2007-07-12
It's making it further intot he boot process than you said it was ... but methinks this will make it easier to fix. 

When you get to the grub menu, hit 'e' to edit the boot option (whichever one you intend to boot), then move down to the kernel line and hit 'e' again to edit that line. Go to the end of the line and add a space followed by "noapic". Hit enter once to return and then hit 'b' to boot. 

Failing this, try using "noapic pci=noapic". 

If these options allow you to boot post back and I'll let you know how to make it permanent.

---

### Post by seekdestroy16 on 2007-07-13
> **kuja said:**
> It's making it further intot he boot process than you said it was ... but methinks this will make it easier to fix. 

When you get to the grub menu, hit 'e' to edit the boot option (whichever one you intend to boot), then move down to the kernel line and hit 'e' again to edit that line. Go to the end of the line and add a space followed by "noapic". Hit enter once to return and then hit 'b' to boot. 

Failing this, try using "noapic pci=noapic". 

If these options allow you to boot post back and I'll let you know how to make it permanent.

Good news, noapic did the trick. I just installed beryl, and firefox seems to crash everytime i launch firefox with beryl launched or launching beryl when firefox is launched....is their a way to fix this?

---

### Post by kuja on 2007-07-18
Hey there, sorry for the delay, I took off for a short vacation. Anyhow, now that I'm here ...

To make it permanent, pull up a terminal and type in:
"*sudo nano /boot/grub/menu.lst*"

It'll bring up a rather lengthy file.
Look for a section like this --

> [color=blue]## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
**# defoptions=quiet splash**[/color]

At the end of the defoptions line put noapic. Save the file and exit nano. 

Now, run the command "*sudo update-grub*"

Now you should be good to go, sorry for the delay again.

---

### Post by seekdestroy16 on 2007-07-20
> **kuja said:**
> Hey there, sorry for the delay, I took off for a short vacation. Anyhow, now that I'm here ...

To make it permanent, pull up a terminal and type in:
"*sudo nano /boot/grub/menu.lst*"

It'll bring up a rather lengthy file.
Look for a section like this --



At the end of the defoptions line put noapic. Save the file and exit nano. 

Now, run the command "*sudo update-grub*"

Now you should be good to go, sorry for the delay again.

I dont see any code in here simular to what you posted to edit. Where would it be?. I'm sure i typed in the right command: "sudo nano /boot/grub/menu.lst"
and this is exactly what it gave me in the attatchment. What should I do?

---

