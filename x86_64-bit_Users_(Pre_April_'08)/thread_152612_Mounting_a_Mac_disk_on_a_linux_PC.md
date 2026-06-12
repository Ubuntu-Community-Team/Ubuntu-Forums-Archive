---
title: "Mounting a Mac disk on a linux PC"
date: 2006-03-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by xmastree on 2006-03-30
I'm not sure if this is the right forum, I'm in unknown territory here, but here goes. :roll:

A friend has an iMac. Not sure of the exact model, but it's not the 'flat screen on a stick' one. It's a CRT.

It's dead, he doesn't know what's wrong, local shops won't touch it since all they know is PCs. I've offered, but I know nothing about them either. :rolleyes: 
And I've told him as much. He's ok about that, since I also told him I have access to a vast resource of knowledge (that's you guys ;) ).

What he wants is to retrieve the data on the disk. Mostly photographs. He's not too worried about the hardware, and I have a feeling that if I can get his photos, he might be so grateful that he'll give me the rest...

Is it possible to pull the disk and mount the Mac filesystem (whatever it is) in my PC and read it? Is the disk itself even compatible (IDE?).

If I can copy the photos to my disk, they're saved. If I end up with the iMac, and fix it, I'll be back here trying to put ubuntu on it. 8)

---

### Post by ssam on 2006-03-30
it will be a standard IDE disk. its in hfsplus format which ubuntu should read fine, just stick a ```
-t hfsplus
``` in you mount command.

you may have to change the permissions on the files so that you can read them.

you might find some info on getting it open at [http://www.apple.com/support/imac/g4/](http://www.apple.com/support/imac/g4/)

---

### Post by xmastree on 2006-03-30
Ok, that's good to know. At least I can offer to retrieve his pictures. That's the main thing as far as he's concerned.
I did look at man mount, but since I didn't know about hfs I couldn't tell. Having looked again though, there seems to be hfs and hpfs but no hfsplus.

As for permissions, it will probably be as easy to copy them as root.

Thanks, I'll let you know what happens.

---

### Post by jdp on 2006-04-01
One common thing that "kills" CRT (ie, G3) iMacs is when people try to start the OS X installer **before** they install the firmware update.  Some do actually dies from the common flyback transformer failure, but most often it's the OS X video bug.  You have to boot the machine from a HDD with at least OS 9.1 on it to do the FW update.  A CD will not work.  If the machine seems to start and you can hear the HDD making noises like it's booting, then it's probably salvageable.  If it just powers on and seems to go dead right away, it's probably the flyback.

---

### Post by xmastree on 2006-04-01
Wow, so software can kill the hardware? :eek:

I don't think he tried to install anything, like a new OS. He's not that technical. But I'll be sure to ask how it happened.

The main priority is to save the data though. Hardware can be replaced. Photos of his daughter growing up can't.

Is it simple to pull the hard disk? I haven't looked at it yet, but I'm hoping it won't be difficult to open up.

---

### Post by rfruth on 2006-04-01
I have a G3 iMac and it had finder version 8 something on it, I wanted (and now have) OS X installed but *had* to update the firmware first not sure if I'd say software can do in hardware though - anyway it's a all - in - one so removing the hard disk is going to be major surgery, not done it myself (I did add a stick of RAM & that was easy)((later IMac's are quite serviceable(i.e a G5 not a G3))

---

### Post by linear on 2006-04-01
You can find guides to opening the G3 iMacs various places online, such as this: [http://www.theimac.com/drive_steps.shtml](http://www.theimac.com/drive_steps.shtml)

Also Apple service manuals are out there: [http://home.earthlink.net/~strahm_s/manuals.html](http://home.earthlink.net/~strahm_s/manuals.html)

---

### Post by xmastree on 2006-04-01
Whoa! Gimme a PC any day!

I really hope I can do that in the comfort of my own home, without the owner looking over my shoulder... :rolleyes:

I'm seeing him later, so I'll take a look and try to bring the machine home.

Of course, my wife will kill me... Another computer in the house? Hmm, better make some space for it.

Thanks for all the tips so far.

---

### Post by jdp on 2006-04-02
The big difference for G3 imac takeaprts is if it's trayloader or slotloader.  They have totally different internals and takeaparts.  Generally I've only worked on slotloaders, and they can have the RAM done in under 2 minutes.  A HDD takes about 10 or less if you know what you are doing.  Trayloaders need more takeapart for the RAM, and I think just a bit more to get the HDD.  The big difference is that the trayloaders have a HDD/CD/mobo sled that can be pulled out.  The slotloaders have a mobo fastened to the main frame and a seperate drive chassis.

---

### Post by xmastree on 2006-04-02
Ok, I have the unit here now. Apparently he did have it upgraded,and it worked for about 10 hours.
I just plugged it in (without the keyboard), pressed the power switch and a chord sound came from the speakers. I didn't hear anything else, like disks spinning though.
I can't get it to make that sound again.

I presume these instructions
[http://www.theimac.com/drive_steps.shtml](http://www.theimac.com/drive_steps.shtml)
are for the trayloader. I'm not sure which this is, so I'll follow those first and if it seems totally different I guess I'll just figure it out as I go...
Wish me luck.

---

### Post by dombleu on 2006-04-02
Just be careful with the axe.

---

### Post by xmastree on 2006-04-02
[QUOTE=dombleu]Just be careful with the axe.[/QUOTE]Heh, it went exactly as that site said, and I now have a 20GB Seagate IDE drive in my hand.
Looking at the construction though, I'm sure I could have got to it without removing the motherboard... :-k

---

### Post by xmastree on 2006-04-02
fdisk -l gives:
```
Disk /dev/hdc: 20.0 GB, 20020396032 bytes
16 heads, 63 sectors/track, 38792 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

Disk /dev/hdc doesn't contain a valid partition table
```


```
chris@xmastree:/mnt$ sudo mount /dev/hdc /mnt/mac -t hfs
mount: /dev/hdc already mounted or /mnt/mac busy
chris@xmastree:/mnt$ sudo mount /dev/hdc /mnt/mac -t hpfs
mount: /dev/hdc already mounted or /mnt/mac busy
```

```
chris@xmastree:/mnt$ sudo mount /dev/hdc1 /mnt/mac -t hfs
mount: wrong fs type, bad option, bad superblock on /dev/hdc1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

:confused:

---

### Post by xmastree on 2006-04-02
So, I wondered if something might have changed with the latest version, you never know, and I remembered I recently made myself a dapper live CD, so i tried that. No different.

Just for the sake of it, I tried running through hdc1,2,3,4,5,6,7,8 to see what happened. When I reached hdc6 mount didn't give me an error. But there wasn't much there when I looked. /dev/hdc7 was the same, exactly. :-k 

```
ubuntu@ubuntu:~$ sudo mount /dev/hdc6 /mnt/mac -t hfs
ubuntu@ubuntu:~$ ls -l /mnt/mac
total 156
-rw-r--r-- 1 root root 155648 2005-03-08 06:11 Desktop DB
-rw-r--r-- 1 root root      0 2005-03-08 06:11 Desktop DF
-rw-r--r-- 1 root root      0 2005-03-08 06:11 Finder
-r--r--r-- 1 root root      0 2005-03-08 06:11 System
-rw-r--r-- 1 root root   1778 2005-03-08 06:11 Where_have_all_my_files_gone?
ubuntu@ubuntu:~$ sudo umount /dev/hdc6
ubuntu@ubuntu:~$ sudo mount /dev/hdc7 /mnt/mac -t hfs
ubuntu@ubuntu:~$ ls -l /mnt/mac
total 156
-rw-r--r-- 1 root root 155648 2005-03-08 06:11 Desktop DB
-rw-r--r-- 1 root root      0 2005-03-08 06:11 Desktop DF
-rw-r--r-- 1 root root      0 2005-03-08 06:11 Finder
-r--r--r-- 1 root root      0 2005-03-08 06:11 System
-rw-r--r-- 1 root root   1778 2005-03-08 06:11 Where_have_all_my_files_gone?
ubuntu@ubuntu:~$ sudo umount /dev/hdc7
ubuntu@ubuntu:~$ sudo mount /dev/hdc8 /mnt/mac -t hfs
mount: wrong fs type, bad option, bad superblock on /dev/hdc8,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

Where **have** all the files gone?

---

### Post by xmastree on 2006-04-02
Well, I managed to read the file, and...

> Why can't you see your files?

This hard disk is formatted with the Mac OS Extended format. Your files and information are still on the hard disk, but you cannot access them with the version of system software you are using.

How can you access your files?

To access your files you must mount this hard disk on a computer that has Mac OS 8.1 or later installed. To determine the version of system software you're currently using, choose About This Computer from the Apple menu. If you're using a version of the Mac OS earlier than 8.1, you must do one of the following: A) upgrade the system software on your computer, B) start up the computer from a hard disk or CD that has Mac OS 8.1 or later, or C) connect the hard disk to another computer with Mac OS 8.1 or later installed.

If you want to access the files without upgrading your system software, start up your computer with the ``Mac OS 8.1'' CD or the ``Disk Tools PPC'' disk, then access your files. Apple recommends that you have the ``Mac OS 8.1'' CD if you plan to reformat any hard disk using Mac OS Extended format.

To continue to use this hard disk with this computer, you must upgrade your system software to Mac OS 8.1.

How do you upgrade your system software?

If you have a version of system software earlier than Mac OS 8, you can order Mac OS 8.1 on the Internet or buy it at a local Apple software reseller.

If you have Mac OS 8 on your computer, you can download the Mac OS 8.1 update from the Internet at [http://www.info.apple.com](http://www.info.apple.com).

I also discovered hfsutils, but that didn't help.
[-(

---

### Post by ssam on 2006-04-02
you need -t hfsplus

there is a backwards compatability thing if you mount as hfs, and you get the message as that text file.

---

### Post by jdp on 2006-04-02
[QUOTE=xmastree]Ok, I have the unit here now. Apparently he did have it upgraded,and it worked for about 10 hours.
I just plugged it in (without the keyboard), pressed the power switch and a chord sound came from the speakers. I didn't hear anything else, like disks spinning though.
I can't get it to make that sound again.[/quote]

It may be because the HDD seems dead, but I'm not sure yet.  If it were functioning, you could put the iMac to sleep once it's booted, then wake it up and you'll likely get some sort of video back.  THe sleep trick does work when booted from an OS 9 CD, too.  It's good to use if you have a spare HDD to install and you need to install OS 9.1 to do the FW update.

> I presume these instructions
[http://www.theimac.com/drive_steps.shtml](http://www.theimac.com/drive_steps.shtml)
are for the trayloader. I'm not sure which this is, so I'll follow those first and if it seems totally different I guess I'll just figure it out as I go...
Wish me luck.

The difference is if there is a tray that pops out to take the CD, or if there is simply a thin slot that CDs are slid into.  It's a very descriptive distinction.  Tray loaders have the bezel that is about 1" high by 5.ish" wide with a matching color button in the middle.  The slotloaders just have a thin color matched slot that is 5.ish" wide.

From what you mentioned of the take apart I'm guessing it might be a tray-loader, as the mobo on a slotloader is (somewhat)  easily taken out all by itself.

Also, under Breezy and Dapper you might not need to specify the filesystem type when mounting.  Running something like **mount /dev/hdc6 /mnt/mac** will let mount auto detect the FS type.

---

### Post by xmastree on 2006-04-02
[QUOTE=jdp]The difference is if there is a tray that pops out to take the CD, [/QUOTE]Once I have that sub-assembly out, the CD can be pushed back against a spring and folded back over the motherboard. Then it's two screws to remove the HD tray. Easy. :cool: 
Much esier than that guide would have me believe. There's no need to remove the motherboard at all.

So, pulling the disk isn't a problem now, but mounting and reading it is.
[QUOTE=ssam]you need -t hfsplus[/QUOTE]

```
chris@xmastree:~$ sudo mount /dev/hdc6 /mnt/mac -t hfsplus
Password:
mount: wrong fs type, bad option, bad superblock on /dev/hdc6,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

chris@xmastree:~$

```Same for hdc7

I tried hfsplus from synaptic:
```
chris@xmastree:~$ sudo hpmount -r /dev/hdc6
hpmount: /dev/hdc6: no error (Success)
chris@xmastree:~$

```Which looks promising, but:
```
chris@xmastree:~$ sudo hpls
hpls: hpls: Unable to read file for cached Volume information. (No such file or directory)
chris@xmastree:~$
```
Then, when I try to unmount it, i get this:
```
chris@xmastree:~$ sudo hpumount
hpumount: destroy: Error while destroying .hfsplusvolume (No such file or directory)
chris@xmastree:~$

```

According to the man page, when hpmount mounts the disk it creates .hfsplusvolume in the home directory, but that file isn't there, so hpls can't read it to give me the listing, and hpumount can't delete the file as it's not there. :confused:  

](*,)

---

### Post by jdp on 2006-04-04
Have you tried mounting with regular mount, and not specifiying a FS type?  From what I've done with Breezy and up, I didn't need to tell it that it was an HFS part.  Mount might be smart enough to try HFS if it notices an Apple partition map on the disk. ;)  **sudo mount /dev/hdc6 /mnt/mac** might just work fine.  I know a similar command worked to mount the HFS+ partition when I was working on getting Breezy on an OldWorld G3MT.

---

### Post by xmastree on 2006-04-04
[QUOTE=jdp]Have you tried mounting with regular mount, and not specifiying a FS type?[/QUOTE]Yes, I tried that and it sais i need to specifya filesystem. Presumably for the same reason that sudo fdisk -l can't identify ant partition table.
I've even resorted to trying Windows programs. :evil: 
I found [macdrive]("http://www.mediafour.com/products/macdrive6/") which looked promising, but it seems to be aimed at external drives only.

I tried a couple of others, but the only one which could actually see the disk still couldn't read it.

As the Mac itself is dead, there is a possibility that the drive is corrupted. I imagine there must be recovery tools avalable, but they probably need a working Mac in the first place. So not only am I trying to read from an alien filesystem, I need to repair it too... ](*,)

---

### Post by xmastree on 2006-04-04
[QUOTE=jdp]If it just powers on and seems to go dead right away, it's probably the flyback.[/QUOTE]I saw the owner last night, and asked about the failure. Apparently there was a noise like arcing inside, and the screen flickered a few times then it died.

---

### Post by jdp on 2006-04-06
Wow, that's a hardware failure for sure.  It'd be an analog board failure, likely the flyback, but the cost to repair might be more than the iMac is worth unless you have a dead-in-another-way iMac of similar model to scavenge the parts from.  It may be possible to do a mobo sled transplant and put the iMac into a regular case and hook up an external monitor.  Even that will cost something to get fixed.

---

### Post by xmastree on 2006-04-06
That's why I'm trying (and failing) to rescue what's on the disk...

How can I mount this sucker?

---

### Post by jdp on 2006-04-06
It's quite possible that when the iMac died, if it was running, it did cause corruption.  Without a running Mac to use tools like DiskWarrior on it may not work.  I don't know of any tools that are designed for HFS recovery under Linux to anywhere near the capability of the Mac OS based tools.

---

### Post by dj_flx on 2006-04-08
Well, you can still put the HD back in, disconnect the internal monitor connection (it should start up with no screen in that way) and hook up either an old Mac monitor or a VGA display with an adapter. Then copy over a ethernet crossover cable.

[IMG]http://static.flickr.com/50/124105701_2f92c59e66.jpg[/IMG]

Mine lives in a crate after getting spliced into an old Pmac 7500 PS.

As for mounting HFS, does HFS+ kill xhfs? That's what brought me here.

---

### Post by dj_flx on 2006-04-08
OK, this probably doesn't fix your thing, but this thread got me what I needed...

I'm accessing old Zip disks off my (first run) SCSI Zip drive. Jazip wasn't mounting the hfs/hfsplus and hmount etc. in the terminal were killing me.

I found that if I ran Gparted and looked at the dev (sdc in my case) I just needed the number of the last partition. Then

```
mount -t hfsplus /dev/sdcX /mnt/mac
```

mounts it (X is the partition # of course) where I can see it in Nautilus. BTW, yeah, I'm running terminal in root - I started with expendable disks.

I don't know how much jazip is affecting this, though.

---

### Post by xmastree on 2006-04-08
[QUOTE=dj_flx]Well, you can still put the HD back in, disconnect the internal monitor connection (it should start up with no screen in that way) and hook up either an old Mac monitor or a VGA display with an adapter. Then copy over a ethernet crossover cable.

[IMG]http://static.flickr.com/50/124105701_2f92c59e66.jpg[/IMG]

Mine lives in a crate after getting spliced into an old Pmac 7500 PS.

As for mounting HFS, does HFS+ kill xhfs? That's what brought me here.[/QUOTE]

Ooh, I like the sound of that solution... Tell me more about this adaptor...

---

### Post by xmastree on 2006-04-08
[QUOTE=dj_flx]```
mount -t hfsplus /dev/sdcX /mnt/mac
```

mounts it [/QUOTE]I get that 'wrong fs type, bad option, bad superblock on /dev/hdc7' error when I try that.

---

### Post by dj_flx on 2006-04-09
[QUOTE=xmastree]Ooh, I like the sound of that solution... Tell me more about this adaptor...[/QUOTE]

You want something like [this]("http://shop.store.yahoo.com/cablesonline/hdvgafemtodb1.html").

Make sure you get the genders right, you **don't want to connect a mac monitor to a VGA output**. Mine lacks the dip switches, hence there was some goofing around with resolutions. SwitchRes took care of that for me.

This is probably really the simpler solution for the problem. I was able to run mine upside-down on the floor for a long while until I got around to re-casing it. Since it's in a new "case" it has a second IDE hard drive now too.

You'll probably want to read [this thread]("http://community.livejournal.com/macintosh/2190848.html")

Of course, once you're done you can always just go ahead and put Ubuntu on it.

---

### Post by xmastree on 2006-04-19
Hmm... been thinking about this.
It seems that duting boot, the system looks for something from the monitor. If the flyback is dead, presumably the system will sense this and not start to boot.
So, if I simply unplug the DB15, will the unit boot up? Or do I need to remove the dead part?
I haven't been able to find that adaptor yet. Is there much in it? I'm pretty handy with a soldering iron, and I can source the connectors. Since it will probably only be used once, to rescue the data, it doesn't need to be too elegant.

---

### Post by qw3rty on 2006-04-20
If you need a working Mac to mount it.  You could try to install OS X that is hacked to run on regular PCs.  It is picky about the hardware it will run on.
[http://thepiratebay.org/details.php?id=3451287](http://thepiratebay.org/details.php?id=3451287)

Have you asked for help in any Mac forums?
[http://forums.macosxhints.com/](http://forums.macosxhints.com/)
[http://www.macfixitforums.com/](http://www.macfixitforums.com/)
[http://forums.macnn.com/](http://forums.macnn.com/)
[http://discussions.apple.com/](http://discussions.apple.com/)

---

### Post by xmastree on 2006-04-20
Hmm, 4.3GB download? That would take about a week... Presumably it's a DVD, which would mean even more hassle as the only system I could use doesn't have a dvd drive...

Firstly, I will try hooking up a regular monitor to the mac, and see what, if anything, happens when I fire it up.

If I can't get it going then I would probably be better off in a Mac forum since this is not really the right place. Thanks for the links.

---

### Post by xmastree on 2006-04-22
[QUOTE=xmastree]Firstly, I will try hooking up a regular monitor to the mac, and see what, if anything, happens when I fire it up.[/QUOTE]This happened:

[[IMG]http://www.lotechdesigns.com/host/thumbs/7774macvga.jpg[/IMG]](http://www.lotechdesigns.com/host/images/7774macvga.jpg)

It switched between a folder with a questionmark and the face logo a few times, before settling for the face.

So, i guess that's a good thing.

Now what? The usb mouse isn't lit up, and the only thing it responds to is pulling the power cord. :-k 

I know, I know, mac forums... :-#

---

### Post by dj_flx on 2006-04-22
[QUOTE=xmastree]Hmm... been thinking about this.
It seems that duting boot, the system looks for something from the monitor. If the flyback is dead, presumably the system will sense this and not start to boot.
So, if I simply unplug the DB15, will the unit boot up? Or do I need to remove the dead part?
I haven't been able to find that adaptor yet. Is there much in it? I'm pretty handy with a soldering iron, and I can source the connectors. Since it will probably only be used once, to rescue the data, it doesn't need to be too elegant.[/QUOTE]

It's something along those lines. It's finding the internal monitor hooked up and then sensing the flyback failure then shutting down, essentially. Disconnect the internal monitor, it doesn't pay attention to the internal monitor or its associated parts.

Which may not be the entire story, but good enough for our purposes.

---

### Post by dj_flx on 2006-04-22
[QUOTE=xmastree]This happened:

It switched between a folder with a questionmark and the face logo a few times, before settling for the face.

[/QUOTE]

That's the Mac not finding/having a PRAM-set startup drive, so it goes through looking at the CD drive and then any connected hard drives for a volume with a valid system folder. The face seems to indicate it's finding a system folder, but something's wrong with it?

Pretty much the same as a PC on startup; although I don't think it even remembers floppies anymore and I don't think it will take a CD over the HD if the HD is set in PRAM.

Hold down the shift key on startup to attempt to bypass extensions loading - Mac OS 9 version of a safe boot. This might get you further along. You also might need a great deal of patience...

Hold down the 'c' key at power-on to force CD startup; it looks like you might need to start from a system CD to have a look at the drive.

---

### Post by jdp on 2006-04-22
I'm almost positive that that photo is a single still that only caught the smiley face part, the other part turns to a ? and then back to the face and back to the ?.  This repeats while the Mac continues to search for bootable volumes, and will continue to do so if it doeesn't find any.

---

### Post by xmastree on 2006-04-22
No, the photo was after it stopped switching between the two. It just sat there displaying the logo.
I tried an ubuntu live CD which almost got there, but it just hung while setting up the desktop. Is this machine capable of rnning ubuntu? I have no idea of the processor speed or RAM, and I don't know how to find out.

---

### Post by xmastree on 2006-04-22
I gave up on the Live CD, instead I swapped the disk and tried an install.
It fails at starting up the partitioner, 52% ](*,) 
That suggests to me a dodgy CD, but it checks out fine in this PC where I made it (burned nice and sow).
I tried cleaning the laser with alcohol, but that made no difference.

If I do get it installed, will it be possible to install both disks on one cable? That's the plan. I realise I'll have to arrange a cpu fan since I won't be able to replace the motherboard etc.


Edit: I'll start another thread about my installation problems.

---

### Post by dj_flx on 2006-04-23
[QUOTE=xmastree]I gave up on the Live CD, instead I swapped the disk and tried an install.
It fails at starting up the partitioner, 52% ](*,) 
That suggests to me a dodgy CD, but it checks out fine in this PC where I made it (burned nice and sow).
I tried cleaning the laser with alcohol, but that made no difference.

If I do get it installed, will it be possible to install both disks on one cable? That's the plan. I realise I'll have to arrange a cpu fan since I won't be able to replace the motherboard etc.


Edit: I'll start another thread about my installation problems.[/QUOTE]

I never got a Ubuntu installer CD to work on mine - either quit at the partitioner or at the finalization part after that or something.

(and why do I HAVE to erase to install? OS 9/X don't require that... Ubuntu installer still has a ways to go...)

OS X, with two drives on one IDE cable works fine, but be aware that I draw power straight from the new power supply and I relegated the old drive supply on the board to powering the re-positioned CPU fan. Using X11 along with Fink/Fink Commander will probably be more stable for you on that machine anyway.

---

### Post by xmastree on 2006-04-23
[QUOTE=dj_flx]I never got a Ubuntu installer CD to work on mine - either quit at the partitioner or at the finalization part after that or something.[/QUOTE]
I got it as far as fiishing the installation, removing the CD and restarting...

The problem turned out to be due to the presence of Windows on the disk.

There's a [new thread]("http://ubuntuforums.org/showthread.php?t=164631") about that, since the title of this is no longer appropriate.

---

