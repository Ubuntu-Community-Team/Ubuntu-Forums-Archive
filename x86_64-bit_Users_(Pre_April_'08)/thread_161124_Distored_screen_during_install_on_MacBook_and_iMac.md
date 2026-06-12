---
title: "Distored screen during install on MacBook and iMac"
date: 2006-04-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by maverick808 on 2006-04-16
I'm trying to install Ubuntu on my MacBook and iMac but on both machines I can't get through the installer because the screen immediately becomes garbled after I select "Install to the hard disk" from the initial install screen.

I've tried pressing F4 and trying VGA and a bunch of different video resolutions but they all fail in exactly the same way. The live CD does not boot either as the screen becomes messed up there too.

I know other Linux distrobutions work. For example, I can install Suse no problem. If I could just get ubuntu installed I could install the new ATI drivers and that would probably work fine. Is there a setting I'm missing somewhere?

I'm trying to install Dapper flight 6 by the way.

---

### Post by SpoonMan on 2006-04-16
I had this problem, with a Mac Mini and an iMac G3. At the "boot:" prompt type "video=ofonly" (without the quotes). Worked for me....

Good Luck!

---

### Post by maverick808 on 2006-04-16
Thanks for the reply.  I'm afraid it doesn't work and I get exactly the same distored screen as I do without the video=ofonly :(

---

### Post by jdp on 2006-04-18
Are you sure of the hardware you are using?  If you are using a MacBook, it would likely be a MacBook Pro, ie the Intel based laptops.

Otherwise, do you mean a PowerBook of some sort, or maybe an iBook?  Also, what kind of iMac.  There's 4 differnt kinds, G3 CRT iMacs, G4 LCD iMacs, G5 LCD iMacs and their look-alike Intel Core Duo LCD iMacs...

---

### Post by maverick808 on 2006-04-20
[QUOTE=jdp]Are you sure of the hardware you are using?  If you are using a MacBook, it would likely be a MacBook Pro, ie the Intel based laptops.[/QUOTE]

I am quite sure of the hardware.  It's a 2.0GHz MacBook Pro... these have ATI  Mobility Radeon X1600 video cards.  I am also trying to install on an Intel 20" iMac which also has the same video card and ends up suffering from the same distortion during the install.

I have no idea why the screen becomes distorted during the install process.  I thought the installer utilised standard VGA and since the Windows and Suse installers work fine I'm quite surprised Ubuntu doesn't.

---

### Post by T31 on 2006-04-20
Hi guy, so you are a lucky guy with such 2 machines!!!

by now I think ubuntu doesnt support EFI so problably it looks for your bios :-k  thing that the new intel macs dont have.

Till now I know two ways to install GNU/Linux on intel macs, use gentoo and build elilo or use bootcamp.

---

### Post by maverick808 on 2006-04-20
Since bootcamp makes it looks like there is a standard BIOS I doubt that is the problem.  It does boot up into the initial installer and only becomes distorted after I select "Install to hard-disk".

Remember, both Windows XP and Suse do not support EFI yet they work fine.

I appreciate everyone's comments so far... I really hope there is a solution soon.

---

### Post by FlakJacket on 2006-04-20
I am having much the same problem on my brand new 17" intel duo iMac.  I hit the Live option and it shows some green text at the top then it says uncompressing kernal... ok booting with lines running up and down the screen.  Eventually X kicks in and i'm in gnome but it'd be nice to see the terminal dialog. I think this might have to do with the resolution of the screen but I don't know. My iMac also has the ATi X1600. I'm using the DVD of Dapper Drake 6.06 BTW.

Thanks,
Flak

---

### Post by shawnhcorey on 2006-04-20
[QUOTE=maverick808]Remember, both Windows XP and Suse do not support EFI yet they work fine.
[/QUOTE]

OK, I have a problem. This is a Ubuntu Macintosh/Apple/PPC Users forum. Why should anyone here care about Windows XP?

shc

---

### Post by FlakJacket on 2006-04-21
I guess because like most linux distros Windows uses BIOS and the Intel macs come with EFI but after a firmware update they can emulate BIOS.

Flak

---

### Post by maverick808 on 2006-04-21
[QUOTE=shawnhcorey]OK, I have a problem. This is a Ubuntu Macintosh/Apple/PPC Users forum. Why should anyone here care about Windows XP?

shc[/QUOTE]

Like Flak says, I am simply countering the suggestion that the problem could be lack of EFI support by mentioning two OSs I've tested that do work but do not support EFI.

---

### Post by shortflood on 2006-05-01
I too am experiencing the distorted screen on my 1.83ghz macbook pro.  This doesn't seem to be a problem with the distros that have what I would guess to be a "less fancy" boot procedure.

maverick, were you able to completely install Suse and boot it through Apple's bios emulation?  or did you just report success with booting their install CD?

The initial menu of the dapper beta livecd clearly uses a supported (by the fake bios) video mode, so what exactly changes when you start loading the kernel?  Could it be a problem with apples "fake bios" not being standards compliant? I don't have the livecd on me at the moment, but does anyone know exactly what mode the bootloader tries to switch to before failure?

--Good luck maverick, consider me in the same boat

---

### Post by maverick808 on 2006-05-02
I got nowhere with it and have given up with the betas.  I can install Ubuntu inside Parallels ([http://www.parallels.com/](http://www.parallels.com/)) now so have been using it that way.

One intersting thing is that when I boot off the CD in Parallels I don't get the same installer but instead get a purely text mode installer.  I thought there would be a way to get into this text mode installer normally so booting the CD directly and holding down shift I get a message saying something like "abort gui install and proceed with text? (c/a)".  However, although the holding shift was detected the installer then refuses to detect any subsequent key presses so I can't press c or a.  Aaagh.

I can boot off the live CD in "Safe VGA/Video" mode so that's probably the way to go to install it.  Put in the live CD and at the boot screen make sure you select safe video.  When it starts booting the screen will distort but just wait (ages... like 2 minutes or something) and eventually when it gets to the desktop the screen is no longer distorted.

I got that far with the live CD but I was using Beta 1 at the time and when I went to do the partitioning in the installer from there it locked up and when I restarted it had totally destroyed all the partitions on my drive (this is a known bug and I believe now fixed in beta 2).  After going through all that I just didn't have the heart to try Ubuntu again when beta 2 did come out.

However, if you boot in safe mode off the live cd, wait ages to get to desktop and finally use the GUI installer it will probably work now.

I bet that even once it's installed you'll still get the screen distortion during normal startup until you get to the desktop.  God knows what strange video mode it is using during the bootup... obviously no other distro or other OS is using it since everything else works fine.

---

### Post by Adam Boettiger on 2006-05-04
[QUOTE=shawnhcorey]OK, I have a problem. This is a Ubuntu Macintosh/Apple/PPC Users forum. Why should anyone here care about Windows XP?

shc[/QUOTE]
Anyone here should care because the new Macs are using an intel-based chipset, so discussing workarounds for installing ubuntu on a MacBook Pro - even if it means going through XP - are still APPLE discussions and this is an Apple forum.

---

### Post by Thingi on 2006-05-06
Sorry to be the bearer of bad news but a distorted screen is only the start of your problems, once the video is sorted out you still wont be able to install because ubuntu can't understand the partition map of an intel apple.

I've got a 2gb mac mini (the intel gfx are fully supported), the livecd works perfectly apart from no networking and the installer cant handle the partitions :-(

The install cd bombs out completely, it's got nothing to do with video support :-(

thingi

---

### Post by shortflood on 2006-05-07
I may be way off here, but my understanding is that ubuntu itself should have no problem with the GPT, as it has been supported by linux for some time now.  The version of 'parted' that is on the liveCDs appears to behave well too.  I have had no problems partitioning the disk, making filesystems, and reading/writing to these in the live environment.  Once that works, the partiton table should be transparent (or at least irrelevant) to the OS, right?

As maverick said, even us macbook pro users can get X running (after quite a wait).  Does anyone remember if the source (python?) for the installer is included on the cd?  I'd love to be able to bypass the partitioning/filesystem-creation wizard and get on to finding the next obstacle.

---

### Post by Thingi on 2006-05-07
[QUOTE=shortflood]I may be way off here, but my understanding is that ubuntu itself should have no problem with the GPT, as it has been supported by linux for some time now.  The version of 'parted' that is on the liveCDs appears to behave well too.  I have had no problems partitioning the disk, making filesystems, and reading/writing to these in the live environment.  Once that works, the partiton table should be transparent (or at least irrelevant) to the OS, right?
[/QUOTE]

The latest version of parted on the ubuntu live CD hasn't had the correct patches for writing an MBR block to the start of GPT partitions so although it does apper to format them I wouldn't trust it (could stop your osx part booting..... I've actually used the GParted LiveCD which is more upto date than the ubuntu version with no problems just to make sure. However the real issue comes when copying the files during the livecd install - it just bombs out :-( 

A few people are doing this from a live CD to get ubuntu working from the live CD:-

After the partitions have been created do:-

rsync -av --exclude=/mnt --exclude=/proc --exclude=/sys --exclude=/tmp / /mnt/target

Then to fix things up:

mkdir /mnt/target/mnt
mkdir /mnt/target/proc
mkdir /mnt/target/sys
mkdir /mnt/target/tmp

...and edit

/mnt/target/etc/hosts,
/mnt/target/etc/hostname and 
/mnt/target/etc/fstab 

After this has been done get elilo working and install rEFIt in the root of your osx partition and use that to boot (you can't use the bios stuff added by BootCamp or the radeon stuff wont work) 

All in all it's a pain but peeps do have it working, at present I'm working on a ghost image of all this so people will only need to take the following steps:-

1. Install bootcamp
2. Create a fat32 partition
3. Use the gparted live cd to do the partitions
4. 'ghost' the premade ubuntu partitions
5. Edit elilo config (if required)
6. Install rEFIt and 'Bless your HDD' 

:-)

thingi

---

### Post by shortflood on 2006-05-09
good news!  I currently have Flight 7 running with everything I need on my macbook pro.  The only deviations from a pure Flight 7 installation are a 2.6.16 kernel (almost identical to the one on gimli's livecd) and lilo instead of grub.  (Grub still gave me some troubles even after I tried the patch, though I admit to not playing with it very long as I knew I had a solution with lilo.)

thingi, Luckily, I think you may have gotten it backwards about the ati drivers.  They require the video mode provided by the bootcamp firmware.  elilo doesn't seem like the way to go here if you want the fancy graphics.

I have a feeling this process is going to be all point-and-click in a few weeks though... 

shortflood

---

### Post by amitofu on 2006-05-09
I had the same garbled screen problem with my intel mac mini. My solution was to use an older, pre flight-6 install cd that for some reason works.

As for the partitoion table. I repartitioned using the Mac OS X partitioner, which writes both the GPT and standard MBR partition tables. Then, while running the installer, BEFORE I assigned partitions using Ubuntu's partioner, I switched to the second virtual console (Ctrl + Alt + F2) and used the shell to back up the MBR (Master Boot Record; the first 512Kb on your hard disk), which holds the old BIOS partitions.

```
# dd if=/dev/sda of=/root/mbr bs=512 count=1
```

I then switched back to the Ubuntu installer and told it how to use the partitions (you can't resize any partitions by this method). After I finished partitioning and wrote the changes to disk, while the system was installing, I switched back to VT 2 and copied the original MBR back to the disk.

```
dd if=/root/mbr of=/dev/sda bs=512 count=1
```

WARNING: Writing directly to your hard disk is dangerous and could hose your system.

Then I installed Lilo at the end of the installation (is there anyway to tell the installer at bootup to automatically install lilo without lowering the frickin' debconf priority?), and rebooted with success.

So it is perfectly possible to install Dapper using only an unmodified install cd. The framebuffer won't work however, so don't try anything sketchy with Xorg unless you have a livecd handy to fix things. The i810 driver gave me hardware accelerated OpenGL for a while, but an update killed it a while back and it hasn't worked since. The wireless doesn't work either, but other than that the performance is great (and is so much more pleasant than Mac OS X, in my opinion of course).

Since there is so little info on runnig Linux on these beauties, I hope this helps someone.

---

### Post by shortflood on 2006-05-10
>  The wireless doesn't work either... 

I found myself automatically connected to an open wifi net on my first boot.  (I think the madwifi drivers are included with Flight 7)  Only problem is I can't connect to my encrypted one.  Oh well, guess I'll just borrow the neighbors connection until I get this figured out.

shortflood

---

### Post by crimsondragon12 on 2006-05-27
amitofu, how did you install lilo?

---

### Post by amitofu on 2006-05-28
[QUOTE=crimsondragon12]amitofu, how did you install lilo?[/QUOTE]

I had to install lilo to the mbr. A couple of things first though, which you're probably aware of but I want to write down for others who may be searching.

The garbled screen was because the Ubuntu folks added the imacfb patch from mactel-linux which uses the EFI framebuffer. When booting from BIOS mode, however, the EFI framebuffer isn't available. This is why the screen becomes garbled. As of linux-2.6.15-23 imacfb is disabled when not booting from EFI and vesafb is used instead, which works. I installed Ubuntu from the rc desktop cd and everything worked nicely.

As for installing lilo. Again, before even running the installer, back up your mbr. Open up a terminal, become root, and type:

```
sudo su -
dd if=/dev/sda of=/root/mbr bs=512 count=1
```

Keep the terminal window open and go ahead and run the installer. After you setup your partitions, switch back to the terminal and copy the mbr back (since it was cleared by the partitioner) so that the installer will continue without breaking.

```
dd if=/root/mbr of=/dev/sda bs=512 count=1
```

You can do this wile the installer is running. The installer will go ahead and install grub (which you can't avoid without making the install a total hassle). When the installer is finished, quit it and say you want to contiue using the livecd. switch back to the terminal and copy the mbr back one more time since grub has now played with it.

```
dd if=/root/mbr of=/dev/sda bs=512 count=1
```

Now it's time to chroot into your new installation to remove grub and install lilo. I also copied my mbr to the hard disk just because.

```
sudo su -
mount /dev/sda3 /mnt
mount -t proc none /mnt/proc
mount --bind /dev /mnt/dev
cp /root/mbr /mnt/root/
chroot /mnt /bin/bash
```

The mbr package needed to install lilo into the mbr is in universe, so edit /etc/apt/sources.list and uncomment the universe repository. Then you're ready for a little apt-getting:

```
apt-get --purge remove grub
apt-get install lilo mbr
```

Now run liloconfig and answer its questions, specifying that you want to install it to the mbr. When this is done you will have a new /etc/lilo.conf--but don't use it. The splash screen it enables seems to cause problems. Edit the file and delete lines (Cntrl+K helps here :-) until it looks like mine.

*/etc/lilo.conf*
```
lba32

boot=/dev/sda3
root=/dev/sda3

prompt
timeout=50

image=/boot/vmlinuz-2.6.15-23-686
	label="Lin 2.6.15img0"
	initrd=/boot/initrd.img-2.6.15-23-686
	read-only

image=/boot/memtest86+.bin
	label="Memory Test+"
	read-only
```

Every time a new kernel is released you will have to manually edit /etc/lilo.conf to use it. Go ahead and rerun lilo, exit and reboot into your new Ubuntu system.

```
lilo -v
exit
```

I don't think I forget anything, but let me know if I did or if anything could be made clearer. All the usual caveats apply: try this at your own risk.

---

### Post by crimsondragon12 on 2006-05-28
ahahahaha we did the same thing except I forgot to chroot.

That is embarassing!  Thank you for the help, it boots wonderfully now.

---

### Post by emrys on 2006-06-24
Mmmm, strange...

With this post I'm able to do most of the process (although the instalation crashes in the grub part).

After that, everything seems ok. (well, this: "apt-get install lilo mbr" fails and I have to delete the mbr part ). I install lilo, I have the wonderfull menu on turning on the laptop with the macOS and linux options but if I choose the linux one, I can just see a black screen with the cursor blinking on left top.

What can be the problem????

---

### Post by mdmunoz on 2006-08-29
I got all the way up to running liloconfig. I installed lilo, but how do I get liloconfig to run?

---

### Post by gavin8or on 2006-10-01
Thanks for the help guys, I installed lilo (took a little /sbin/lilo -P fix and other -P options to get it to install) but when I booted, even though rEFIt can see the LILO no problem, when I select the penguin hard disk, I get a black screen and a hardware lock. Maybe I forgot to comment out a line in lilo.conf?

Anyways, I will keep tinkering with lilo, might try a manual install of grub. 

EDIT: No I just chrooted and looked at the /etc/lilo.conf and everything is commented out properly... But there are some worrisome warnings when I run lilo:

Warning: '/proc/partitions' does not match '/dev' directory structure.
    Name change: '/dev/dm-0' -> '/dev/evms/sda1'
Warning: Partition 4 on /dev/sda is not marked Active.
Warning: partition type 0xAF on device 0x0804 is a dangerous place for
    a boot sector.
I will assume that you know what you're doing and I will proceed.
Added Lin_2.6.15img0 *
Added Memory_Test+


What does it mean that the partition is not marked Active?? Will it not boot if it is not marked active?

---

