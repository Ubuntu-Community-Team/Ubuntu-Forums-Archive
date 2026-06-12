---
title: "Ext4 and Windows"
date: 2009-05-01
forum: x86 64-bit Users
---

### Post by 73ckn797 on 2009-05-01
I got a good laugh when trying to read my 9.04 64bit ext4 drive from Windows XP Explorer. The display will show the directory names but when entering any of the directories I am only getting the following, single file listing:

```
, go on foot; run; leave
```Has anyone seen this before? I am running the reader for ext3 in Windows with no problems. Is there a reader for ext4 that anyone knows of?

---

### Post by WindPower on 2009-05-02
From what I've heard, you can use the ext2 filesystem driver to mount an ext4 drive, but only if you have disabled extents (which are on by default).
I too am looking forward to an actual ext4 filesystem driver for Windows :(

---

### Post by 73ckn797 on 2009-05-02
Do you get the same results looking into an ext4 directory from Windows? I really thought is was funny.

---

### Post by Elfy on 2009-05-05
off topic posts moved.

---

### Post by stchman on 2009-05-05
AFAIK Windows XP or Vista will not read Linux volumes EXT2/3/4 without some kind of software interface.  I use DiskInternal Linux reader for the rare instances I boot into Windows.

[http://www.diskinternals.com/linux-reader/](http://www.diskinternals.com/linux-reader/)

It does the job for me.

---

### Post by 73ckn797 on 2009-05-05
My whole point was the humor I found by what an attempted read produced. It actually surprised me that it would even read the directory names at all. I run the ext2s in Windows to read the ext2/3 file system.

---

### Post by abhiroopb on 2009-05-06
I use the following to read ext3 in windows: [http://ubuntuextreme.blogspot.com/2009/01/how-to-mount-ext3-filesystem-in-windows.html](http://ubuntuextreme.blogspot.com/2009/01/how-to-mount-ext3-filesystem-in-windows.html)

In the comments another program is suggested.

Mine never worked with explorer. 

Would be interested to know if there is at all an ext4 driver for windows.

My external hard drives are in ext4, which is great for speed, but iritating if I want to share something with friends.

---

### Post by 73ckn797 on 2009-05-06
My looking around has found no reader for ext4, yet.

---

### Post by countryjake on 2009-06-19
[http://sourceforge.net/projects/ext2fsd](http://sourceforge.net/projects/ext2fsd)
this is the driver for ext2 and is SUPPOSEDLY compatible with ext4, however you will have to access it as an ext2 filesystem and therefore will be unable to use the new features of the ext4 filesystem

UPDATE: Works on Windows 7 if settings are put for it to run as if it is on windows xp. however, no filesystem shows up and I am somewhat confused as how I am going to make it show up as an ext2 filesystem. more googling to do!
Furthermore, this note from a developer of Ext4 came to my attention: [https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/317781/comments/45](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/317781/comments/45)
maybe time to downgrade to ext3?

---

### Post by 73ckn797 on 2009-06-19
I have gone back to ext3 for multiple reasons.

---

### Post by os56k on 2009-07-15
Hi,

I do not think now there be a driver for ext 4 because this file system is very new. According to [http://en.wikipedia.org/wiki/Ext4](http://en.wikipedia.org/wiki/Ext4) the stable patch for ext4 was merged to the kernel on Oct 11, 2008.

But you can have an eye on the following websites :

[http://www.fs-driver.org/](http://www.fs-driver.org/)
[http://www.ext2fsd.com/](http://www.ext2fsd.com/)

and check when this driver will be available.

I e-mailed the author of the first website, Stephan Schreiber, about ext4 :

/*********************MY E-MAIL********************************************************************************************/
/***********************************************************************************************************************/
Hi Stephan Schreiber,

When are you going to create a driver for ext4 file system ? and when will it be ready ?

Thank you very much
/***********************************************************************************************************************/
/******************HIS ANSWER*******************************************************************************************/
Hello,
Ext4 support is being developed but I can't promise that the next version of Ext2 IFS will have all features of Ext4.
I can not tell you a specific date of release.

Kind regards
Stephan Schreiber
/**************************************************************************************************************/

---

### Post by vincebs on 2009-08-20
I'm having the same problem, with both Windows and Mac OS X. I'm wondering whether disabling ext4 extents and ext3 journalling will allow me to access my Ubuntu partition. If so, how do you do this?

---

### Post by takbal on 2009-08-30
I can read ext4 partitions from Windows by installing a minimal Ubuntu distribution through VirtualBox, which enables one to mount hard disks on the host operating system directly (check the advanced part in its documentation). Starting the VM is comparable in speed to starting a dedicated reader program especially if it is done from a memory snapshot. I use Ubuntu, but practically any distros should do which has a kernel with ext4 support built in.

Another benefit is that I am using the native ext4 driver this way, so there is practically no chance of disk corruption because of an early and buggy ext4 implementation in some 3rd party kernel driver. Mounting the linux in RW should be absolutely safe.

However, you have to be careful not to mount the Windows partition as well, because two operating system accessing it concurrently may trash it. Fortunately VirtualBox has a shared folder feature which makes very easy to use the Windows partition in a safe way.

The disadvantage is that you need to store a relatively large virtual disk image, but as I said it can be possible to use an even more lightweight Linux for this purpose (but then you may have problems with the guest additions of VirtualBox).

---

### Post by Starks on 2009-09-06
You can boot your Ubuntu partition in Windows using Virtualbox and vice-versa.

---

### Post by bonfire89 on 2009-09-21
> **Starks said:**
> You can boot your Ubuntu partition in Windows using Virtualbox and vice-versa.


How do you do that?

---

### Post by Slim Odds on 2009-09-21
> **bonfire89 said:**
> How do you do that?

You install VirtualBox and then install Ubuntu inside (using the CD image).

---

### Post by bonfire89 on 2009-09-22
I know how to do that, but, the message above seems to say you

ie  if you are currently dual booting between windows in ubuntu that you can run your current windows from in ubuntu and vice versa.... similar to vmware workstation.

---

### Post by MKdx on 2009-09-22
> **Slim Odds said:**
> You install VirtualBox and then install Ubuntu inside (using the CD image).

I think what he meant is that you can use the real Ubuntu partition as image inside VirtualBox, this way VB will communicate between the two systems using shared folders for example.

---

### Post by partsdale on 2009-09-23
I thought it was funny

---

### Post by bonfire89 on 2009-09-23
> **MKdx said:**
> I think what he meant is that you can use the real Ubuntu partition as image inside VirtualBox, this way VB will communicate between the two systems using shared folders for example.


oh true. hmm that is a lot of weight... although. I suppose one could virtualize ubuntu server or perhaps something even lighter that supports ext4.

Interesting thought.

---

### Post by mattkoehn on 2009-09-29
VM server can do that, which is to say booting from a physical partition instead of a virtual partiton. Virtualbox may be able to, I'm not sure. There was some interest a while ago when the Virtualization programs offered some degree of graphics acceleration to using a physical partition instead of wine for gaming. However, this never got far as the virtual graphics adapter is still limiting the acceleration the result is about the same as running wine. There is a video tutorial on linuxjournal from like 2006 showing how to do this.

Regardless, the host operating system still needs to be able to view the partition you are mounting, so even with that idea it won't help for Ext4.

---

### Post by Lockheed on 2009-10-21
> **takbal said:**
> I can read ext4 partitions from Windows by installing a minimal Ubuntu distribution through VirtualBox, which enables one to mount hard disks on the host operating system directly (check the advanced part in its documentation). Starting the VM is comparable in speed to starting a dedicated reader program especially if it is done from a memory snapshot. I use Ubuntu, but practically any distros should do which has a kernel with ext4 support built in.

How exactly do you do that? I've been reading the manual but I cannot find anything on accesing on host (XP) physical partitions seen by guest (ubuntu).

Unless you are doing something else...

---

### Post by MilesTails on 2009-10-21
You can have virtualbox acces partitions via the VBoxManage command which can be used to create a vmdk file for RAW disk access

---

### Post by Lockheed on 2009-10-22
Ok, but how do I access from host XP the partition mounted inside guest ubuntu ?

---

### Post by RaveJunkie on 2009-10-23
EXT4 is better. I am running 9.04 on a few machines and on one i timed a load on ext3 then formated and went to ext4 and then booted and cut off a few seconds on boot. That is on a quad boot machine and my 6 meadia drives are all ntfs and i can read and write to them no problem (all four OS share pictures, music ect) plus my liniux drive never needs a defrage and the read write times are faster


[http://www.hiprank.com/ext3-vs-ext4-...at-vs-xfs.html](http://www.hiprank.com/ext3-vs-ext4-...at-vs-xfs.html)

---

### Post by MilesTails on 2009-10-23
> **Lockheed said:**
> Ok, but how do I access from host XP the partition mounted inside guest ubuntu ?

Um only way i can come up with is to mount the disk in virtual ubuntu then share it via samba. Depends on how much you need to transfer/have access to, samba is kind of a dumb  workaround here but if you need access to an ext4 file system to do more than just copy stuff across it would work.

If all you need though is the ability to move stuff across then using shared folders is a viable option, and if you can copy what you need to work on to the shared folder its really a better option.

---

### Post by mgillespie on 2009-10-23
Booting with Ubuntu and Virtualbox is not a solution for me, I need to mount a USB HDD formatted as EXT4 in Windows, so I can virus scan it (please don't insult me by offering ClamAV as a solution).

---

### Post by RaveJunkie on 2009-10-23
[COLOR="Blue"]can you use virtual box, install xp, update it, install anti virus and anti spyware apps, update them, then run on the drive in question?  

then when done you can delete the VM or whatever cause it has served its purpose.[/COLOR]

---

### Post by ceefour on 2009-10-31
If you want to dual boot Ubuntu with Windows and read ext4 filesystem, you can use Ext2FSD. Although you may need to take special steps as explained below.

I’ve successfully used Ext2fsd on Windows 7 to read my ext4 (!) filesystem this way.

For those interested, more detailed how-to is here: [Read ext3/ext4 Partition from Windows 7]("http://www.soluvas.com/read-browse-explore-open-ext2-ext3-ext4-partition-filesystem-from-windows-7/")

Hope this helps!

---

### Post by jonathanstratford on 2009-11-05
If you've got a Ubuntu VM in VirtualBox under Windows, can you just drag files out from VirtualBox into Windows? I know this is possible under VMWare Player with VMWare Tools, but not sure about VirtualBox, and the manual doesn't seem to want to load. Just thought I'd suggest it.

---

### Post by Slim Odds on 2009-11-05
> **jonathanstratford said:**
> If you've got a Ubuntu VM in VirtualBox under Windows, can you just drag files out from VirtualBox into Windows? I know this is possible under VMWare Player with VMWare Tools, but not sure about VirtualBox, and the manual doesn't seem to want to load. Just thought I'd suggest it.

Easiest way in VirtualBox is to use shared folders.

---

### Post by abhiroopb on 2009-11-05
So, is there a way without VM? or Virtualbox? I just want something like Ext2Fsd to work.

---

### Post by Slim Odds on 2009-11-06
> **abhiroopb said:**
> So, is there a way without VM? or Virtualbox? I just want something like Ext2Fsd to work.

Well.... as you can see from the name, it's made to work with ext2. ext4 is has a number of changes (including extents) which make it incompatible. Although, my understanding is that Ext2Fsd works with ext3.

So your choices are:
1) Don't use ext4
2) Update Ext2Fsd to be Ext4Fsd

Good luck.....

---

### Post by abhiroopb on 2009-11-06
According to this guy ext2fsd can be used to read ext4 partitions:

[http://www.soluvas.com/read-browse-explore-open-ext2-ext3-ext4-partition-filesystem-from-windows-7/](http://www.soluvas.com/read-browse-explore-open-ext2-ext3-ext4-partition-filesystem-from-windows-7/)

---

### Post by Slim Odds on 2009-11-07
> **abhiroopb said:**
> According to this guy ext2fsd can be used to read ext4 partitions:

[http://www.soluvas.com/read-browse-explore-open-ext2-ext3-ext4-partition-filesystem-from-windows-7/](http://www.soluvas.com/read-browse-explore-open-ext2-ext3-ext4-partition-filesystem-from-windows-7/)

Did you read this part?
> 
[LIST=1]
[*]When creating the ext4 filesystem, make sure to add “-O ^extent” which means disabling the “extent” feature bit. I’m not sure if the following steps will work if your ext4 filesystem still has “extent” feature enabled. ext2 and ext3 partitions should be fine.
[/LIST]


---

### Post by abhiroopb on 2009-11-07
I wasn't sure where to add that bit!

---

