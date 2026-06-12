---
title: "cant mount dvds"
date: 2007-04-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by d80tb7 on 2007-04-29
Hi all,

I installed Feisty last week but haven't yet been able to mount any sort of DVD.  I was therefore hoping someone on here might be able to help.

All types of CDs automount fine.  If I insert a any sort of DVD (movie, commercial or one I've burned myself)  then the light comes on on the drive for a few seconds and nothing else happens.

If I then go to places->computer and click on CD-RW/DVD+RW drive I get an error message to the tune of :

'unable to mount media, there is probably no media in the drive'


If I try sudo mount /media/cdrom0/  then the terminal window just hangs 

Here's my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=5dc041e2-6a88-46a3-99b1-4b6839db7519 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=1ec04659-3350-45aa-8d17-9091fe6d960b none            swap    sw              0       0
/dev/hdd        /media/cdrom0   auto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sdc        /media/floppy1  auto    rw,user,noauto  0       0

To rule out a hardware problem I've tried two different dvd drives both of which work fine under windows.  

All help gratefully received!

Chris

---

### Post by kuja on 2007-04-29
That's really odd, all I can say is every drive out there is going to behave a bit different. Some of my drives are pretty quarky (especially my cheapo samsung RO drives) , but my Pioneer DVD+R/W drive doesn't give me any trouble, fortunately.

One thing you could try would be changing "auto" to explicitly say "udf,iso9660" instead

---

### Post by gregdwih on 2007-04-30
I cannot mount dvds either:confused:

---

### Post by d80tb7 on 2007-05-01
I tried changing "auto" to explicitly say "udf,iso9660"  but no luck so far.  Aargh.

Things I've found so far (may or may not be of any use for people)

1.  My original /etc/fstab had a mountpoint set for /dev/hdc but dmesg indicated it should be /dev/hdd.  I changed  my fstab but nothing changes.

2.   There's a bug report for something similar at ([http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg294967.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg294967.html)) The suggested solution there is to manually mount using sudo mount -t udf /dev/cdrom /media/cdrom0.  Unfortunately this just hangs my console.

3.  At one point I popped in a DVD and tried to load it using VLC.  Nothing happend so I ignored it.  A minute later the dvd started playing! At that point I thought my problems were solved but I've not been able to read a dvd since in VLC or otherwise.

the search continues....

---

### Post by kuja on 2007-05-02
I recommend trying to run it in a different live cd just to see if you can get it to mount properly. Something like Knoppix or an older version of Ubuntu. If it works in those it's probably an issue with the 2.6.20 kernel.

---

### Post by d80tb7 on 2007-05-02
Good Idea!  I just tried a Dapper Live CD I had lying around and experienced the same issue so it doesn't seem to be a kernel specific thing.  I also downloaded a mandriva live cd but when I try to run it I get a "monitor signal out of range" on my LCD.  I'll therefore have to dig out a CRT to try it (Unless someone knows how to change the xorg.conf for a live cd?)



Chris

---

### Post by kuja on 2007-05-02
more likely than not it's the videocard instead of the monitor.

---

### Post by d80tb7 on 2007-05-11
Ok I've 'fixed' it by diabling automounting of media in System->preferences->removbale drives and media and can now mount stuff from the command line.

It might be a bug (from looking on the internet a few other people are having the same problem), but just to rule out chronic stupidity on my part before I file a report, does anyone else have any ideas?

Chris

---

### Post by Verminoz on 2007-05-15
OK, maybe I'm wrong but I have reasons to believe what's to blame! I have the same problem in Kubuntu 7.04! Before I installed them on my computer I backed up my data in DVDs and formated my disk. I installed Kubuntu 7.04 and after that I copied most of my data from the DVDs back on the hard disk. Everything was fine for a month until the day before yesterday when I inserted one of my backup DVDs to find some uncopied data and I noticed that none of those dvds can be mounted and manual mounting does not work either. It just spits out the same errors yours did.
Some days ago I made some updates the automatic update program found. One of them was the "hal" package which is the Hardware Abstraction Layer and the "libhal" package. All these can be found on my dpkg logs.

So, could it be something about that? It seems rather important and related to hardware devices. Could it be a "hal" bug???

I'm sorry if I'm totally mistaken. I am simply trying to help.

---

### Post by rggavubt on 2007-05-15
I'm having the same problem.  When I upgraded to Feisty, I hit next by mistake before the HAL files had downloaded to my PC.  Feisty installed but I noticed that it couldn't fine the HAL files and used defaults during the install operation.  Feisty works expect that I can't mount DVD's or play DVD's on any player I have.  I understand HAL files are for SATA drives so I thought I was OK because I don't have SATA hard drives.  Change HAL to mdadm......sorry.

---

### Post by mooscape on 2007-05-15
I have just installed the latest Feisty desktop onto a friend's IBM T30.  Everything seems to work well except that DVD's simply won't play.  I have tried Totem, Gxine, Mplayer ,  ... nothing works! This also a bit embarrassing after raving about Linux for months.  (My machines are all purring. Including an alternate install of Feisty from when it first came out.(IBM R40))  Could there be a bug in latest version of Feisty?

:confused:

---

### Post by rggavubt on 2007-05-15
I think there is a bug i Feisty.  I submitted a bug on this today #114816.  In my previous post HAL needs to be changed to "mdadm"

---

