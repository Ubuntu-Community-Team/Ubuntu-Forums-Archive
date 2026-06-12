---
title: "timevault or rdiff-backup..."
date: 2009-03-15
forum: x86 64-bit Users
---

### Post by inphektion on 2009-03-15
I'm looking for something like timemachine for OSX but for Ubuntu.  It seems like timevault or rdiff-backup are the two best choices...
Anyone with any personal experience with either of these two have any options?  It doesn't seem timevault has a 64-bit build so that might be the deciding factor right there but if anyone has opinions let me know.

---

### Post by John Jason Jordan on 2009-03-15
> **inphektion said:**
> I'm looking for something like timemachine for OSX but for Ubuntu.  It seems like timevault or rdiff-backup are the two best choices...
Anyone with any personal experience with either of these two have any options?  It doesn't seem timevault has a 64-bit build so that might be the deciding factor right there but if anyone has opinions let me know.

I tried timevault, but there is no 64-bit deb so you have to install the 32-bit deb with dpkg and the force-architecture option. After installing it my Intrepid locked up several times, so I had to uninstall it.

Backing up a single user's home computer is a problem with Linux because you get so much conflicting advice about what should and should not be backed up.

---

### Post by inphektion on 2009-03-15
Thanks for the feedback.  I think in the end timevault will probably be good but rdiff-backup i know is stable.  Maybe if I install timevault with getlibs instead of forcing it it won't lock up.

---

### Post by John Jason Jordan on 2009-03-15
> **inphektion said:**
> Thanks for the feedback.  I think in the end timevault will probably be good but rdiff-backup i know is stable.  Maybe if I install timevault with getlibs instead of forcing it it won't lock up.

If you're going to use rdiff-backup there is a GUI for it - pybackpack. It's in the repositories, so just use apt-get or Synaptic.

---

### Post by inphektion on 2009-03-15
Cool thanks.  I'll be trying them both to see which one is better for me and I'll post back my opinion.

---

### Post by ahbart on 2009-03-16
I use rdiff-backup to backup to a usb disk. If you have setup this well in a script, it works wonderful. I did not know of this grafical frontend for rdiff - pybackpack. The problem with that one (for me) is that you can not exclude directories.

Have a look at this examplescript:
```

#!/bin/bash

cd /media/backup-disk/backup-vast/home
echo "Backing up /home/bart"
echo ""
rdiff-backup --print-statistics --exclude /home/bart/mnt --exclude /home/bart/.wine --exclude /home/bart/tmp --exclude /home/bart/.VirtualBox --exclude /home/bart/Downloads --exclude /home/bart/media /home/bart bart

cd /media/backup-disk/backup-vast/media

echo "Backing up media foto's and music"
echo ""
rdiff-backup --print-statistics /home/bart/media media

echo "**********rdiff-backup completed************"
echo ""
echo "Disk usage:"
echo ""
df /dev/sdc2

```

In the first part I have excluded media (foto's, movies etc) because I wanted to have this in a separated directory. 
So I backed these up in the second part.

---

### Post by inphektion on 2009-03-16
Do you only use rdiff for your /home dir?  I was thinking of doing that and then maybe something like mondo for the entire system on a monthly basis or so.  If I use rdiff for the entire system I was wondering what I'd want to exclude...  don't need /sys or /tmp etc...

---

### Post by ahbart on 2009-03-16
I have separated partitions for home and root. Of te root partition I make an image with partimage now and then. I do this with [system-rescue-disk](http://www.sysresccd.org/Main_Page).

---

### Post by John Jason Jordan on 2009-03-16
> **inphektion said:**
> Do you only use rdiff for your /home dir?  I was thinking of doing that and then maybe something like mondo for the entire system on a monthly basis or so.  If I use rdiff for the entire system I was wondering what I'd want to exclude...  don't need /sys or /tmp etc...

Which directories to exclude/include is one of the problems us non-gurus have. I understand not to back up /proc, /tmp, /mnt and /media, but I have little understanding of what the other system directories do and whether or not I should back them up.

An even harder thing to get a grip on is permissions and ownerships. 

I haven't actually tried pybackpack yet, but I'm going to in the next couple of days. I keep looking for a GUI that is flexible, yet holds my hand sufficiently so I can back up my computer without first getting a degree in comp sci.

---

### Post by ahbart on 2009-03-16
In that case I suggest you try sbackup in the ubuntu repository. 
After installation you can find Simple backup config and simple backup restore under system and administration. use config to start ;)

Negative point of this tool is that you cannot see the progression of the backup. If you click 'make backup now' the backup starts in the background (as root). 

And as far as I know, permissions are being kept as they are.

But an image of the root partition is much easier! Back to the start in a few minutes. :D

---

### Post by inphektion on 2009-03-16
> **ahbart said:**
> I have separated partitions for home and root. Of te root partition I make an image with partimage now and then. I do this with [system-rescue-disk](http://www.sysresccd.org/Main_Page).

That disk looks good but partimage doesn't mention ext4 yet which my / and /home are.  Mondo does.  Grant it I didn't try either yet but so far I'll try rdiff for /home possibly moving to timevault as it matures and mondo or partimage for the / partition once a month or so.

---

### Post by John Jason Jordan on 2009-03-16
> **inphektion said:**
> ... possibly moving to timevault as it matures 

As exciting as timevault looks to me, I see little evidence of any recent development work. I hope I am wrong. And if development is really stalled, I wish the developers would ask some other group to take it on. 

Meantime I have my last final exam for the term on Wednesday, and after that I'm going to do a thorough backup and then start fixing stuff that I have been putting off.

---

### Post by colau on 2009-06-27
> **John Jason Jordan said:**
> If you're going to use rdiff-backup there is a GUI for it - pybackpack. It's in the repositories, so just use apt-get or Synaptic.
pybackpack,nice tool.

---

