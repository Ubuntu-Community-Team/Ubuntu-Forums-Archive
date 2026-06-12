---
title: "Just installed AMD 64bit Version (all good except refresh rate)"
date: 2005-06-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by Griffology on 2005-06-13
So after researching many different distros (slackware, fedora core 3, suse) I finally decided to go with Ubuntu.  I must say I've been very pleased with the install, as it was my first non-knoppix taste of linux.  Everything went very smooth.  I'm dual booting with Windows XP Pro on hda and Ubuntu 5.1 on hdb and expierenced no problems with that aspect.  I must admit I was a bit worried after reading through the forums before actually diving in.

The only problem I have is setting my refresh rate on my monitor above 60hz, which kills my eyes.  I've noticed a few other threads about this problem and possible solutions so I'll get reading away on those.

I just wanted to thank the community for providing a "noob" into linux many resources making the jump from windows as easy as possible.  I remember how lost I was when I jumped from DOS to Windows 3.11.  As I said, I'm dual booting but hopefully one day I won't even need my windows/microsoft ;) 

Thanks again,
Jason

---

### Post by Griffology on 2005-06-13
Alright, after trying many different options I finally got my refresh rate/monitor config!!

FYI: [http://www.ubuntuforums.org/showthread.php?t=40268&highlight=refresh+rate](http://www.ubuntuforums.org/showthread.php?t=40268&highlight=refresh+rate)
That's what did it for me.  Thanks!


Next step:  Get Kde up and running nad learn some more commands...  'cd' and 'ls' isn't cutting it. :)

---

### Post by Griffology on 2005-06-13
Houston we have a problem :: no longer boots up :(


Here's the error message I got... I reinstalled but after a few reboots similar error was achieved.  Bad HD?

```

Ext3-FS error (device hdb1):  ext3_check_descriptions:  1node bitmap for group 400 not in group (block 4294967295)!

Ext3-FS - group description corrupted
cramFS: wrong magic
pivot_root:  no such file or directory
/sbin/.hit! 428:  can not open dev/console no such file
kernal panic - not syncing:  Attempted to kill init!

``` 

Give or take some bad spelling... any ideas?

---

### Post by rsw on 2005-06-13
woops, you just updated your post. heh


Sounds like you're going to need to boot from a live-cd (or something quick & simple like a slackware/gentoo install disc, i guess knoppix works as well, though Ive not used it). 

You'll want to run fsck on hdb1, probably like so:

# fsck.ext3 -f -y /dev/hdb1


..also worth noting, use a ubuntu-based live-cd, as using a significantly different version of fsck.ext3 will find more wrong than what's really wrong and cause huge problems ;).

As to what might be causing these problems, I dunno. Are you overclocking via FSB? If so, does your motherboard have a PCI/AGP lock? Also, provide system specs.

---

### Post by Griffology on 2005-06-13
Ok, thanks for you reply!  I'm going to try the thing you suggested.  I'm not overclocking.

System Specs:

ASUS K8V SE DELUXE
AMD 64 bit 3200+
512 MB Ram
128MB Nvidia FX 5200
40gig Western Digital HD (7200rpm) (Win Xp)
60gig Maxtor HD (5200rpm) Free/linux
Pioneer DVD-RW (4x)
Generic CD-ROM

---

### Post by Griffology on 2005-06-14
It seems to be working better after that now... Thanks a ton!

I also installed KDE and have that up and running :)

---

