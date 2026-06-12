---
title: "Problems installing Ubuntu in OSX dual boot"
date: 2005-11-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by ted400 on 2005-11-23
Ok, I have seen all th info regarding dual boots with windows but I need some help with OS X. I am running Tiger and would like to "play" with Ubuntu on the same laptop (A G3 600 iBook). I have already made two partions when reinstalling Tiger one 22GB for Tiger and one 8GB for Ubuntu. I go through the installation for Ubuntu and get to the partition phase and thats where I get hung up. 

I find the partition I want to install UB on and I have created a newworld boot partition, however I get past the zlib1 portion of the file transfer (about 26%) and the installation crashes saying that there was a Apple Boot Strap error. I can't seem to figure this one out. I would consider myself an advanced OS X user but a higher end n00b in the linux world ( I have a LAMP running on another box, somehow I figured that one out ;0) )

If I have to reinstall Tiger, no biggie, it's a new install anyway, I can start from scratch if someone can point me to some easy How To's....Thanks!

Hope you all can help, and I appologize if this has been answred already, but I can't seem to find anything, and I have been looking all day!

---

### Post by ted400 on 2005-11-23
OK all, I figured this one out, so let me answer my own question just in case this may help someone else in the future. 

I originally created two patitions when installing Tiger. In the process of installing the Ubuntu I was attempting to change patitions manually which was a bad idea. Instead I found some but not all of what I was looking for in another thread, I figured out the rest. What I needed  to do was allow the Ubuntu installation to delete the partition I originally created during the Tiger install. Once I deleted that partition, I then went back into the partition table and chose "use largest empty space" as my option. This then took the old partition space and created the correct swap file, installation partition, and modified the yaboot file to allow for dual boot. Long story short, I was trying too hard. 

To make it easier on others trying the Tiger/Ubuntu dual boot here is a How To:

1.Install Tiger and in the options of installation, use Disk Utility to create two seperate partitions, it doesn't matter how the second one is formatted since you will delete it in the Ubuntu install
2. Install Tiger as usual
3. Once completed get the install iso for PPC and burn the image to CD 
4. Chose to boot from CD (Hold C upon boot)
5. Follow the install directions until you get to partition tables
6. In partition table delete the partition you created for your Ubuntu install during the Tiger install.
7. Go back to the main partition table and select "use largest free space" for your installation.
8. Sit back and wait while it runs and installs your dual boot

Note: My installation with 5.10PPC the yaboot file was automatically converted for dual boot, but it may not for you...I was lucky for once!

Once completed upon reboot you should get a boot menu stating that you should press "L" to boot Ubuntu, "X" for OSX and "C" for CD boot.

DONE!

Hope this helps others in the future....it's really easy once you figure it out, and this step by step should be all you need.

---

### Post by ssam on 2005-11-23
thanks for posting the working method, it will probably help someone out in the future. have fun with ubuntu.

---

### Post by rob_gendreau@yahoo.com on 2005-11-27
I did basically the same thing, except I was using a disk with a fat32 partition, and a big empty space. I have three other boot disks. The install via CD went OK until the install ended and it was time to boot into the installed linux; the machine instead booted into OS X on one of my other drives. I tried resetting the PRAM and using option at startup to find the linux disk to boot from, but only OS X showed up (in the past when I had Ubuntu installed on the same disk on the same machine it worked; I since had to wipe it to use it on another machine).

suggestions to finish the install?

Are there any instructions out there on booting from the CD again in rescue mode and correcting the problem so it will boot into Linux and finish the install?

Rob

---

### Post by rob_gendreau@yahoo.com on 2005-11-28
To add a bit more info to my previous post. I could get to the shell on the CD.

Yaboot.conf lists boot=/dev/hdc5 (/dev/disk2s5 on the mac, right?).

fdisk listed /dev/hdc1 to /dev/hdc4, with 1 being Apple partition map, 2 being Apple bootstrap, 3 being Apple Unix Linux native, and 4 being a swap disk.

So, given this info what do I have to do to 1) get the mac to list the yaboot menu on startup, or 2) boot from the rescue disk so that I can finish phase 2 of the install? (Remember, I only got to the part where the installer finished with the CD, ejected it, and was supposed to reboot into Linux to finish).

Also, I previously had a Ubuntu install on this machine, but with different partitions. But I haven't added anything OVER this Ubuntu install.

TIA,
Rob

---

### Post by CerebralDawn on 2005-11-28
I followed ted400's procedure and everything seems to have installed correctly.  However, I can't seem to access one partition while in Ubuntu and I can't access the other in OSX.  Is this normal?  And is there anything I can change so that they can see each other?

---

### Post by Ptero-4 on 2005-11-28
CerebralDawn. About the partition stuff, that's normal. Linux doesn't yet support hfs+ (OS X) and OS X doesn't support reiserfs and jfs (Ubuntu). Currently to be able to share partitions you have to put a hfs (OS 7 and OS 8 ) partition next to your ubuntu and your OS X partitions, both Ubuntu and OS X support hfs.

---

### Post by kevinlyfellow on 2005-12-12
I have found a driver for linux for hfs+, unfortunatly its still in early development and only supports the 2.4 kernel, but its good to know that its being developed.

[http://sourceforge.net/projects/linux-hfsplus](http://sourceforge.net/projects/linux-hfsplus)

I also found a driver that claims to work on the 2.6 kernel, it says that is based on the above driver

[http://www.ardistech.com/hfsplus/](http://www.ardistech.com/hfsplus/)

---

### Post by autocrosser on 2005-12-12
Before you go too far with adding drivers to your system---I mount HFS+ on my system via the /etc/fstab --HFS+ works just fine & I read/write without problems--you just have to set the permissions correctly in OSX & Linux (make the partition "No ownership" in OSX & as root in Linux allow anyone to read/write)--My fstab looks like---

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb5       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb6       /home           ext3    defaults        0       2
/dev/hdb10      /opt            ext3    defaults        0       2
/dev/hdb8       /tmp            ext3    defaults        0       2
/dev/hdb7       /usr            ext3    defaults        0       2
/dev/hdb9       /var            ext3    defaults        0       2
/dev/hdb4       /mnt/osx        hfsplus defaults        0       0
/dev/hdb3       none            swap    sw              0       0
/dev/hda3       /mnt/osx4       hfsplus defaults        0       0
/dev/hda5       /mnt/root       ext3    defaults        0       0
/dev/hda6       /mnt/home       ext3    defaults        0       0
/dev/hda7       /mnt/opt        ext3    defaults        0       0

Notice that both OSX & OSX4 are hfsplus--mounted default without error checking.

Also I have two external HFS+ firewire drives that mount in /media without problems--again, I just made sure that permissions were set correctly.

As far as EXT2/3--OSX can't read them yet--there ia a driver for OSX (extfs) at Sourceforge--it just won't support 10.4 & up--The author is currently working on 10.4 support--will be after the first of the year---

Also--take a look at this thread--- [http://www.ubuntuforums.org/showthread.php?t=92141]("http://www.ubuntuforums.org/showthread.php?t=92141")

---

### Post by bennyp on 2006-02-01
Is it practical/possible to use the same home directory for both operating systems?

Allow me to elaborate: Advances in the broadcom (airport extreme) drivers will soon make it practical for me to use GNU/Linux daily on my iBook G4, and revert back to OS X only when I need to do Audio work using my MOTU 828mkII.

My iBook has only a 27gb drive, and so I must be very frugal with my hard disk space. I have a lacie d2 drive that I could use with either OS to store documents and such.

Perhaps the best set up would be 5gigs each for ubuntu and os x roots, respectively, and 17gb left over for a shared /home??

---

### Post by autocrosser on 2006-02-02
Sorry--I don't think that you would be very happy (nor would OSX) with the result--Linux & OSX are Unix-based--this much is true----but the difference is in the details. BSD linux/unix & the Debian version used in Ubuntu won't live in the same house (nor will most if not all standard flavor linux OS out there). You would end up with two un-bootable operating systems.

I cross-share data between OSX & Ubuntu, so you can pass documents across the table--I'd divide your drive with about 5 to 7g to OSX (because you won't be using it much;)) & give the rest to Ubuntu--create a / (root) partition (about 7G) & a /home with the rest--I set-up a seperate /home incase I need to re-install or mod my system--you just install to / & your user stays the same.

Follow the guidelines in the thread & your 'book will be a happy one!!

[quote=bennyp]Is it practical/possible to use the same home directory for both operating systems? <snip>Perhaps the best set up would be 5gigs each for ubuntu and os x roots, respectively, and 17gb left over for a shared /home??[/quote]

---

### Post by bennyp on 2006-02-03
What if ubuntu was configured to only recognize dotfiles with a specific header like
```
#ubuntu 5.10 .xinitrc
```

---

### Post by ssam on 2006-02-04
[QUOTE=bennyp]What if ubuntu was configured to only recognize dotfiles with a specific header like
```
#ubuntu 5.10 .xinitrc
```[/QUOTE]

that would require a patch to a huge number of packages. there are thousands of unix apps that use dotfiles.

also mac os x's .ssamappprefs would need a different file name from ubuntus .ssamappprefs

---

### Post by nooduntu on 2008-04-24
> **ted400 said:**
> OK all, I figured this one out, so let me answer my own question just in case this may help someone else in the future.

Thanks ted400 - your post just answered my question perfectly. Cheers.

---

