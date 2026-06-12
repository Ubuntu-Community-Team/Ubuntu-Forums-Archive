---
title: "Install keeps freezing"
date: 2008-07-27
forum: x86 64-bit Users
---

### Post by evilkl0wn on 2008-07-27
I am trying to install the 64 bit version of ubuntu 8.04.1. I burn it to cd, and reboot system. I select install, it loads the kernal. It then goes on to load the Ubuntu splash screen where the bar bounces back and forth, and it stops, and does nothing.

I tried reburning it 4 times at 8x and once to dvd at 4x and always get the same result. 

Specs

ASUS A8N-SLI SE s949
AMD X2 4200+ at 2.21GHz
4GB OCZ DDR PC3200 
200 GB SATA HDD
nVidia eVGA 7900 GTX 512MB PCI-E
SATA PCI card

What is going on?

thanks

---

### Post by Teeh on 2008-07-27
Maybe the disc image you downloaded is corrupt, have you tried redownloading it, and verifying that the disc is OK using the menu option that comes with ubuntu?

---

### Post by Neo0351 on 2008-07-27
try this, when u boot the cd and it askes u what to do, press F6 and add this after quiet splash
```
all_generic_ide floppy=off irqpoll
```
should look something like this
```
quiet splash all_generic_ide floppy=off irqpoll
```

---

### Post by evilkl0wn on 2008-07-27
Thank you both, generic_ide floppy=off irqpoll fixed the problem.

---

### Post by evilkl0wn on 2008-07-27
Now a new problem. It installs fine, but after the boot loader, it freezs at the splash screen again. Any ideas now?

---

### Post by Neo0351 on 2008-07-27
when you get to the grup menu, hit esc and then hit the "e" key and arrow down to the kernel line and hit "e" again.  then enter all_generic_ide floppy=off irqpoll then hit enter, and then "b"  that should get you booted, once booted
```
sudo gedit /boot/grub/menu.list
```
find this
```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash
```
edit it to look like this
```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash all_generic_ide floppy=off irqpoll
```
save your changes and exit, then
```
sudo update-grub
```
after that, you should be able to boot with no problems

---

### Post by smooth3006 on 2008-07-28
so this must just be specific to x64 installs right ? once i got ubuntu installed i had a ton of other issues "bugs" and i got rid of it. i even tried to install kbuntu x64 and do the trick that was mentioned above and it doesn't work now ? id go with the 32bit install if i didn't need to utilize my 4gigs of ram. i hope the ubuntu / kubuntu team is working on a fix for this issue because it is steering me away from linux at the moment.

---

### Post by chexed on 2008-08-05
My 64 bit edition of Ubuntu 8.04 freezes while installing too, but at different points.

The furthest I ever got is when it started formatting the drive... It got to 5% and froze. Can it not format NTFS drives?

It usually freezes just AFTER the loading screen finishes, when the wallpaper (bird) shows up.

The second most common place is freezes is when the partioning program is just loading.. It stops at 50% for a few seconds, then finishes to 100% and the loader goes away making you think it's coming up, but it just sits there forever.

...

I don't know why this is happening, but I've tried pre-formatting the drives, loading the DEMO before installing (so it installs within the demo) - which seems to get me further, usually past the wall paper...

...

I didn't make a new post, because I figured I'd just be making a duplicate post, I'm just adding to this one to make sure people know this is a problem with just more than one person...

I've never gotten Linux of any flavor to install on any of my machines :(

---

### Post by divrdrew on 2008-08-07
I was going to start a new thread, but looks like others are experiencing similar issues to mine, so I figured I'd follow up here.  Looks like I'm getting a bit farther down the road, but still having problems.

I tried the solution posted below, but that didn't work.

I am a newbie with Ubuntu but have been around since the days of the Apple II, so I'm pretty familiar with computers (did a lot of programming back in the day as well).  I'm trying to install 8.04 onto a self-built system.  Let me try to explain the problems I've been having.

Downloaded it, burned it, and verified the CD more than once...doesn't appear that it's a problem with the image or the CD itself.

First, I tried to run it directly from the CD...would not load.

Second, I tried to install it by booting to the CD...froze up as well.

Both hung up about 80% of the way through the main splash screen that has "Ubuntu" and a progress bar below it.

Finally, I tried to install it from within windows.  Seems as it partially installed.  When I boot and choose to load Ubuntu, I get an unrecognized partition table error.  From what I've seen on these forums, that can be ignored.  Ubuntu will load and I get the screen with the bird on it.  Then it will start to verify the installation and when it starts verifying the partitions, it hangs when it hits 100%.

Once it got past that and went a few steps further and got to 50% while "copying files" but never finished.  

When I reboot and start Ubuntu again, the whole process begins over and it will freeze at 100% where it says "computing the new partition."

I am running the following (system is about 3-3.5 years old):

AMD Athlon 64, 3000+
MSI K8T Neo-FSR Motherboard (newest bios flashed)
2Gb RAM 
MSI Nvidia GeForce FX5700LE video card with 2 monitors (I am turning off the second one during the install)
2 Western Digital 160GB HD from SATA controller (not set up as RAID)
1 Maxtor 200GB HD PATA controller
DVDRW and Combo CDRW/DVD Drive from second PATA controller
Floppy drive
1394 (on mobo)
Gigabit ehternet NIC (on mobo)
USR wireless maxg PCI
Realtek AC97 sound (on mobo)
And your usual USB ports, etc.

XP x64 (completely updated) is installed on the first 160 GB Hd and I tried to put Ubuntu onto the second 160GB hd (completely empty drive).  All my data is on the third (200gb) HD and all three hard drives are NTFS.

Any help / ideas would be greatly appreciated.  I really want to try Ubuntu, but my computer won't let me ;-)

Thanks

Drew

---

