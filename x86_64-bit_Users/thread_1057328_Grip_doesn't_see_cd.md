---
title: "Grip doesn't see cd"
date: 2009-02-01
forum: x86 64-bit Users
---

### Post by jmarks on 2009-02-01
I am running Intrepid 64 bit and just installed Grip 3.3.1. Putting a CD in my DVD reader/writer brings up an Audo Disc icon on the desktop, and RhythmBox can see the audioCD tracks just fine. In Grip, the CDROM device is /dev/cdrom (I also tried /dev/scd0). When trying to rip a track, Grip complains that no disc is detected in the drive. (tried with multiple audio cds)

I suspect the drive is being mounted correctly and I just don't know how to point Grip to the right place.
So two basic questions:
1. What am I doing wrong?
2. Where do I look to see what devices/peripherals Ununtu thinks I have, how they are mounted, etc?
The following thread suggests that this may be a Grip problem, however. 
[http://ubuntuforums.org/showthread.php?t=751355](http://ubuntuforums.org/showthread.php?t=751355)

All I'd like to do is rip/encode my cd audio files as FLAC, so if people have other programs they prefer, I'd appreciate hearing about them.

thanks to all.

---

### Post by stmiller on 2009-02-01
Hey yeah that is odd. Audio CDs actually do not ever get mounted. (You can't mount them.) 

So usually just pointing grip to /dev/cdrom or similar works. There's always K3B to rip CDs if an alternative is needed.

---

### Post by divmediat on 2009-03-27
Got the exact same challange;

Grip shows No Disc, and is configured to use /dev/scd0. It can however spin up the CD and eject the disc. And I have actually made grip to show me the content, if I do something rather strange...

 cat /dev/scd0

which gives me an Input/output error in the command line, but for a brief moment, Grip shows me all the tracks on the cd...?

---

### Post by oldos2er on 2009-03-27
Check System, Administration, Users & Groups to make sure your user has access to the cdrom drive.

---

### Post by divmediat on 2009-03-27
I do, thanx for the advice anyway.

---

### Post by Slim Odds on 2009-03-27
Check the devices, sometimes it's /dev/cdrom0 or /dev/cdrom1 (or something like that).

Try this:```
ls /dev/cdr*
```

---

### Post by PtitLu on 2009-04-03
Same problem for me
> **oldos2er said:**
> Check System, Administration, Users & Groups to make sure your user has access to the cdrom drive.

```
ls -l /dev/dvd
lrwxrwxrwx 1 root root 3 2009-04-03 18:50 /dev/dvd -> sr0
``````
ls -l /dev/sr0
brw-rw----+ 1 root cdrom 11, 0 2009-04-03 20:50 /dev/sr0
``````
groups
ptitlu adm dialout voice **cdrom** audio www-data video plugdev games users lpadmin pulse pulse-access pulse-rt admin sambashare vboxusers
```

EDIT : By the way, ripping is ok with abcde, k3b, konqueror, ...

---

### Post by PtitLu on 2009-04-07
SOLVED (for me) !

I added /dev/scd0 (or /dev/dvd) in this line
config -> extraction -> extractor -> genereic SCSI peripheral

---

### Post by PtitLu on 2009-04-07
Oooops, it worked only once :(

---

### Post by sickofthesea on 2009-07-16
Read all the posts. Tried all the tricks. Grip still won't see the CD. :-(

---

### Post by hughcharlesparker on 2009-08-04
I'm getting the same problem.  I'm running Jaunty, with backports, 32-bit.

---

### Post by oldos2er on 2009-08-04
Seems to be a FAQ; i.e. why grip won't see some CD drives. [http://nostatic.org/grip/doc/ar01s05.html](http://nostatic.org/grip/doc/ar01s05.html)

---

### Post by hughcharlesparker on 2009-08-30
Thanks for that.  I've tried all the things in the FAQ - still no use.  I've even tried putting all of the available /dev/sg* devices in the generic scsi box.  Is it just that GRIP can't handle SATA CDROM drives?

---

### Post by oldos2er on 2009-08-30
Have you tried asking the developers? You can subscribe to their mailing list here: [http://lists.sourceforge.net/mailman/listinfo/grip-users](http://lists.sourceforge.net/mailman/listinfo/grip-users)

---

### Post by hughcharlesparker on 2009-08-31
Thanks, I'll try asking there.

---

