---
title: "Need help with HFS+ partitioning,PLEASE!!"
date: 2006-03-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by Madman68 on 2006-03-04
I've been trying and trying to resize my HFS partition on my iBook G4 for what seems like all day. (I've been using "parted" to do this. I would also like to do it without paying for any programs unless its absolutly required.) I tryed it once and it went all the way through except at the ennd it gave me an errer message saying that an extent was not rcovered or something to that extent and the errer message also says that some files weren't replace and won't do anthing after that. I don't want to get rid of OS X so if anyone knows another way to do this it would be very nice to hear from you. Thanks!

---

### Post by ssam on 2006-03-06
have you had a look at [HOWTO: Resize your HFS+ partition for free]("http://ubuntuforums.org/showthread.php?t=89960&highlight=hfs")

---

### Post by Madman68 on 2006-03-06
yes, actually I have, I followed the instructions to the "T" and it just gives me an error saying that it failed because an extent was not replaced and some files (doesn't give names) were not repaced. Any Ideas?

---

### Post by ssam on 2006-03-06
could you post the exact commands you used, and the exact output.

also the output of
```
sudo fdisk -l
```
and
```
dmesg | tail -n20
```
after trying to mount the partition

thanks

---

### Post by Madman68 on 2006-03-06
The exact steps and output I used ae as follows:

First and before all I diabled Journaling on my Mac HFS+ partition. First I followed all the steps on the Ubuntu install disk up to the partitioner. When I was in the partitioner I selected "Go back" and then in the menu I selected "Exicute a shell". Once in the shell I typed```
Parted
``` after this I typed```
Print
``` This brought up the hard drive name and information. After this information I typed```
resize 3 128.031 72319.081
``` this happens to be the resize information I want my 80GB hard drive to be resized to. Once I enter this information it comes up with a message sying this exactly> Warning: You have an HFS+ file system that has a feature that I haven't seen used anywhere. Parted can theorectically handle it, but the corresponding code has never been tested, so this might be risky. Please email me so I can see how it works <xilun666@libertysurf.fr> Then I type I for ignore and it starts to resize the partition. After it starts it stops and these exact messages come up> Warning: An extent has not been relocated.> Error: Data relocation left some data in the end of the volume.> Error: Resizing the HFS+ volume has failed. Any ideas please!!??

---

### Post by Madman68 on 2006-03-07
The output of ```
sudo: fdisk -1
``` was ```
sudo: not found
``` The output of ```
dmesg | tail -n20
``` was```
[ 43.467206] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache
[ 43.473545] Uniform CD-ROM driver Revision: 3.20
[ 49.192505] usbcore: registered new driver usbserial
[ 49.201369] drivers/usb/serial/usb-serial.c: USB Serial support registered for Generic
[ 49.210174] usbcore: registered new driver usbserial generic
[ 49.210192] drivers/usb/serial/usb-serial.ci USB Serial Driver Core V2.0
[ 59.804086] SCSI subsystem initialized
[ 59.817030] Initializing USB Mass Storage driver...
[ 59.825881] usbcore: registered new driver usb-storage
[ 59.825898] USB storage support registered.
[ 60.885605] Sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
[ 61.552935] ISO 9660 Extensions: RRIP_1991A
[ 80.786087] Sungem.C:V0.98 8/24/03 David S. Miller (davem@redhat.com)
[ 80.847776] PHY ID: 4061e4, addr: 0
[ 80.857160] eth0: Sun GEM (PCI) 10/100/1000BaseT Ethernet 00:14:51:05:55:e0
[ 80.857183] eth0: Found BCM5221 PHY
[ 86.741347] NET: Registered protocol family 17
[ 134.195103] JFS: nTxBlock = 2000, nTxLook = 16005
[ 134.509670] SGI: XFS with ACLs, large block numbers, no debug enabled
[ 134. 510299] SGI: XFS Quota Management subsystem
```

---

### Post by jdp on 2006-03-07
If you are running the install CD, then you don't need to use **sudo**, so just try **fdisk -l** on it's own.  And that's 'l' as in Leopard, not '1' as in number one, in case anybody is getting confuzzled.;)

---

### Post by Madman68 on 2006-03-08
When I do **fdisk -l** I still get a message saying that it dosn't reconize that code.

---

### Post by Madman68 on 2006-03-09
Even after trying fdisk -l many times it still won't reconize that code, also it still won't let me resize the partition. I've even tried using parted from Gentoo and a couple others to see if they would work but they give me the same error messages. Any ideas??

---

### Post by ssam on 2006-03-09
have you turned off journaling in mac os x? and run a disk integrety check?

---

### Post by Madman68 on 2006-03-09
Yes, journaling is off , I turned it off using the terminal and then to make sure I tured it on again and then back off. I also ran a disk check and it was fine.

---

### Post by jdp on 2006-03-09
Since **fdisk** doesn't work, what does **parted** put out when you give it the print command?  What does the auto partitioner show before you exit out to a shell?

---

### Post by Madman68 on 2006-03-11
The auto partitioner, when you select manualy edit partition table, shows```
IDE1 master (hda) - 80.0 GB Toshiba MK8025GAS
     #1 32.3 KB          APPLE
          134.2 MB        Free Space
     #3 79.9 GB  hfs+  Untitled
          5.1KB             Free Space
``` When I type ```
print
``` in parted it gives me     

> Minor     Start       End        Filesystem      name        Flags

              1      0.000       0.031                           Apple     
                                                                                 
              3    128.031     76319.081     hfs+         Untitled                                                                                  

Sorry about that, the table won't come out right. Under "Minor" it is supposed to say "1" and under that (in the same column) it says "3". Under "Start" it is supposed to say "0.000" and under that "128.031". Under "End" it is supposed to say "0.031" and under that "76319.081. Under "Filesystem" it is supposed to say (nothing in the first line) and under that "hfs+". Under "Name" it is supposed to say "Apple" and under that "Untitled". Under flags it says nothing in either column.

---

### Post by kadymae on 2006-03-11
If you are willing to do a complete wipe the drive and start from scratch method of setting up a dual boot system, this is how I set up my Pismo.

[http://members.cox.net/kadymae/dualboot.html](http://members.cox.net/kadymae/dualboot.html)

(Also, I'm using 10.3, not 10.4, so if 10.4 has made any changes to the disk tools goodies ....)

---

### Post by Madman68 on 2006-03-11
No, thats not what I was thinking. I don't really want to wipe my hard as I don't have a way to fully back up my hard drive. I am lookng for a way to resize my current hard drive's single OSX partition without losing any data because of what I stated previously.

---

### Post by jdp on 2006-03-12
How much free space is left on your OS X partition?

---

### Post by Madman68 on 2006-03-12
Around 10 to 11GB. Why?

---

### Post by Madman68 on 2006-03-13
Well, my hard drive is 80GB and I have about 11GB of free space on this drive (which has the single OSX partition on it) and am still looking for a free way to repartition this drive without erasing it or losing any data. Again, any more ideas are very welcomed!

---

### Post by Madman68 on 2006-03-19
I'm still trying but with no luck. I've tried everything but nothing works. If you have any ideas or need more info than is in this pst just ask.

---

### Post by grazie on 2006-03-19
As parted is failing it's not looking good. You may be able to use parted with a slightly different method, but if your data is important it must be backed up first. Can you not connect to another machine with spare disk space to backup your data? As it is, you've already taken a big risk.

---

### Post by slooksterpsv on 2006-03-20
Here's how I did it, maybe you could try again, and do it this way:
Disable Journaling on Mac OS X by booting into OS X and typing in a terminal:
```

sudo diskutil disableJournal /Volumes/Macintosh\ HD/

```
where Macintosh\ HD/ is the name of your volume.
Next boot off of the Ubuntu Breezy CD. Get to the part where it talks about your partitions and go to go back then to a shell.
Type in:
```

parted

print
[code]
   MINOR   START   END
   1            0          128.13   Empty
   3            128.13      38414.23  HFS+

```
resize 3 128.13 30000
i  to ignore
[/code]

Here's what that does. It changes my partition size for OS X from 40GB to 30GB.

---

### Post by Madman68 on 2006-03-21
Thats exactly what I have bben doing if you read the beging of the post. I've tried that what seems like hundreds of time and it still won't work, but I'll try it again, and then again, and probally again. It still says that an extent has not been relocated and that some data was not relocated or something like that. (I said exactly what it told me earlier in the post)

---

### Post by Madman68 on 2006-03-21
I've been looking around some more and have read some stuff about "Sarge". I read that it was posable to repartition an HFS+ drive with Sarge without losing any data. Can some one tell me if this is possible and where I can get Sarge. Thanks again!

---

### Post by grazie on 2006-03-21
Sarge is to Debian as Breezy Badger is to Ubuntu and Debian & Ubuntu share a large code base.

---

### Post by outofnicks on 2006-03-22
You said you did a disk check--was that from the OSX boot CD? 
I am only on Jaguar, so don't know if this would work--sounds like your OSX file system needs minor repair. I do that by booting into single user mode--Command-S at bootup. That brings me to a console where I enter
```
/sbin/fsck -y
```
If the final output is "FILE SYSTEM MODIFIED" then repeat above until you're told the file system appears to be OK.
I've heard that this works better than using OSX's graphical disk utility.
You might try one of the OSX forums for more specific advice, OSXFAQ has a good troubleshooting thread:
[http://forums.osxfaq.com/viewtopic.php?t=7269](http://forums.osxfaq.com/viewtopic.php?t=7269)

---

### Post by outofnicks on 2006-03-22
[QUOTE=Madman68]Well, my hard drive is 80GB and I have about 11GB of free space on this drive (which has the single OSX partition on it) and am still looking for a free way to repartition this drive without erasing it or losing any data. Again, any more ideas are very welcomed![/QUOTE]
Just a stab in the dark, I'm no expert by any means--but maybe that 11GB just isn't enough free space for some reason. I did a google for "An extent has not been relocated" which you could have done, and found this:
[A possible hint]("http://svn.debian.org/wsvn/parted/upstream/trunk/devel/libparted/fs_hfs/reloc_plus.c?op=file&rev=253&sc=1")

On that page, FIND the word "relocated" and you'll see above that the words /* not enough room */.
Might be worthwhile to zip or stuff up some files, even another 5-10 gb of space would be enough?

---

### Post by Madman68 on 2006-03-22
Thanks, I'll give it a try. I think I made some progress though because it use to tell me that > An extent was not relacated  and that> Error: Data relocation left some data in the end of the volume and it also said that> Resizing of HFS+ partition has failed. Now, it only tells me that An extent was not relocated and not the two other errors. Also, after it tells me that an extent was not relocated the pecent complete keeps going up. It gives me the error between 60% and 80% but after it give me the errro it keeps going up past 100% complete? Any more ideas, especiall about this?

---

### Post by Madman68 on 2006-03-22
when I did booted holding down commabd s and typed fsch -y it said that the drive was ok. Now what should I try/do?

---

### Post by Madman68 on 2006-04-07
Well, I've finially givin up. I still have my iBook but I finially broke down and bought a cheap HP laptop running Windows XP PRO to dual boot with Ubuntu. I wish I could have done it on my iBook because I like working with macs better. But, I guess thats the way things are goning to be. Thanks for all the help trying to get my iBook to dual boot but nothing worked. I hope I won't have as much trouble with this new laptop. If anyone has any more ideas or suggestions that weren't mentioned here that they think will work please tell me. Thanks again for all your help!

---

### Post by jdp on 2006-04-07
Other than finding some way to back up your Mac OS data and then do a full repartition from an OS X install CD, I haven't had any ideas on your situation for a while.  :(  At least you got something that seem to be working.  Does the HP have enough space to store an image of your Mac partition?  You can connect to the HP over a network, create a disk image with Disk Utility and use Carbon Copy Cloner to copy the contents of your boot drive over to it.

---

### Post by outofnicks on 2006-04-07
i think you made the right choice, I've been kind of in the same boat. Tried to get Ubuntu on my old B&W G3 without success, then came across a good deal on my Dell Pentium and it installed on that with no problem. 
I felt guilty about crossing the line from Mac to Pc being a Mac user from day one, but now I feel I have the best of all worlds with the two boxes networked together and running Ubuntu, Windows XP, Vector Linux on the PC and OS X/OS 9.1 on the Mac. I have all the popular operating systems on my workstation and feel on top of the world.
I messed around with Samba for file sharing, it was problematic so settled on PureFTPd on the Mac as the ideal setup for me after discovering that Jaguar's default FTP server was broken.
Anyway, it took a couple weeks of scouring these forums and other forums, and hours of Googling to get where I'm at now where I'm happy with what I've got and with what I've learned. It was kind of a rocky road but well worth it.

---

### Post by Madman68 on 2006-04-08
The Hp has only a 20GB hd in it right now but I bought a  80GB to replace it with and a 100GB external hard drive so I will have enough room. I thought about doing what you said jdp but I'm not going to mess with my iBook anymore. I would have liked to dual boot it but I have too much on it now and I'm just going to dual boot the HP. From what I've read I should have an easier time with that if all goes right, I hope.

---

