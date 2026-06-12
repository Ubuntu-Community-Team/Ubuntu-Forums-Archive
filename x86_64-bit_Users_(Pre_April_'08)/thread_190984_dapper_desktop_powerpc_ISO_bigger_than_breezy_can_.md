---
title: "dapper desktop powerpc ISO bigger than breezy can burn CD"
date: 2006-06-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by rubliwdrahcir on 2006-06-06
I am running Breezy on an iBook 14" 1.4GHz G4 PPC 1.5GB RAM 100GB HD with the SuperDrive (CD-R/DVD-R) made by Matsushita (UJ845-E).  I downloaded the Dapper Drake Ubuntu 6.06  desktop powerpc release ISO from the local bit torrent and attempted to write it to a 700MB CD-R as I have done with half a dozen previous ISO images.  This time it refused to work in Nautilus(2.12.1):CD/DVD Creator claiming that it needed a 702MB disk for the 701.1MB image.  I turned to GnomeBaker version 0.5.0-3~breezy1 which also refused to write the image.  While perusing the GnomeBaker project home at [http://gnomebaker.sourceforge.net/v2/](http://gnomebaker.sourceforge.net/v2/)
I noticed that the most recent version of GnomeBaker 0.5.1 was released February 4th, 2006 and includes the following line in its change log:
* Fix Bug #1270524 Won’t allow burning of 700mb files

I am currently configured to see the Ubuntu Breezy Universe repository which provides GnomeBaker.  Synaptic lists the latest version available from that repository as 0.5.0-3~breezy1.  This is what I have installed.  I checked the file sizes of the most recent images I have been burning and the Ubuntu 6.06 Dapper PowerPC desktop is the largest and closest to the maximum size:
 680540160 2006-06-06 09:09 xubuntu-6.06-desktop-i386.iso
 701743104 2006-05-29 17:51 ubuntu-6.06-rc-desktop-powerpc.iso
 707751936 2006-06-06 13:50 xubuntu-6.06-alternate-i386.iso
 720015360 2006-04-01 15:54 dapper-live-flight6-powerpc.iso
 729980928 2006-04-30 20:31 dapper-live-daily20060430-powerpc.iso
 730804224 2006-05-05 14:01 dapper-live-powerpc.iso
 735117312 2006-06-06 07:40 ubuntu-6.06-desktop-powerpc.iso

I am using Sony  700MB 80min CD-R media which should approximate the Optical Storage Technology Association's listing of 737,280,000 bytes available in mode 1 with 2KB blocks, 75 blocks/second for 80 minutes.
[http://www.osta.org/technology/cdqa7.htm](http://www.osta.org/technology/cdqa7.htm)

A short calculation in bc -l
700MB = 700 * 2^20 = 734003200 Bytes
maximum available on 80 min CD-R = 737280000 / 2^20 = 703.125000MB
file in question = 735117312 / 2^20 = 701.062500MB
This makes it look like the file should fit since it is after all an image of the filesystem and thus shouldn't gain (too much?) size when written to disk.

This brings me to a triple of questions:
1.  When will the new GnomeBaker 0.5.1 arrive in the Breezy Universe repository?  I'd like to try Dapper out with the live CD before upgrading since this is my production machine right now.
2.  Does anyone else have some insight into this problem that I am missing?  If so, please share it and remedy my ignorance.  (I noticed that with the BurnFree option checked in the GnomeBaker setup dialog it could not set its scheduler priority when running non-privileged so I tried it with sudo gnomebaker and then it said it couldn't find the device.  I also tried invoking gnomebaker with the -ignsize and -overburn options, to no avail.)
3.  Has the Dapper powerpc desktop CD outgrown 700MB media so that we now need 800MB media to hold 701.1MB?

Thanks,
r

---

### Post by vladanian on 2006-07-13
Yeah?  Same problem here -- you can't get this onto a 700MB disc?

---

### Post by linear on 2006-07-13
Other CD-burning software (Apple's Disk Utility, for one) _can_ burn this to a 700MB disk. If all else fails, you can use the alternate install disk (< 700MB).

---

### Post by fuoco on 2006-07-21
Anything new about this ? How can I burn that iso to a normal 700MB CD-R ?

---

### Post by birdmun on 2006-07-22
best fix I have found is to right click on Applications and then select Edit menus after that goto System Tools and select Configuration Editor once that is done you can click Applications > System Tools > Configuration Editor and after it starts search for 'burner' you will see a selection for nautilus-cd-burner click it and then click on overburn that should solve your problems btw Configuration Editor will allow you to make other choices about the way your system/gui works :)

---

### Post by em3raldxiii on 2006-07-22
Be aware that overburning can damage your media and (rarely) your burner.On the other hand, it should be noted that ISO files are routinely larger than the actual disc capacity.  I know it's strange, but I have burned happy discs that were well over 800MB in ISO format, but once burned they were indeed well within the actual disc capacity.  In these instances it is due to the data format of the ISO files (I think it might have to do with raw data format and sub-sectors on the physical disc).So if you attempt to burn the ISO directly to disc, it won't fit.  But if you create a disc from the ISO Image (not the same as direct burning), then it might work.  I don't know about using GnomeBaker for that purpose, though.  I typically use K3B (even though I use Gnome, I prefer K3B which is KDE oriented).Hope that helps ... maybe :D

---

### Post by rubliwdrahcir on 2006-08-14
This discussion was continued on the following thread:

[http://www.ubuntuforums.org/showthread.php?t=191024](http://www.ubuntuforums.org/showthread.php?t=191024)

---

