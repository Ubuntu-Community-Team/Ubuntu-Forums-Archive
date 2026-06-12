---
title: "Backup Software"
date: 2008-06-26
forum: x86 64-bit Users
---

### Post by mercules2178 on 2008-06-26
I have decided to make the jump to Ubuntu and would like some help with very good backup software that will create and image of my system and then do incremental backups after that. Suggestions would be great!!!

---

### Post by stinger30au on 2008-06-26
do you want to make a mirror image of every single piece of data on your hard drive or just backup only your saved data.

i suggest you create a directory and all data that you need to save you drop it in to that directory.

you can then use simple backup to create backups of it.

but i have been lead to believe that simple backup will not span media.
this means that if you have 7 gigabyte of data and only a single layer dvd that will backup 4.7 gig of data per disc it wont allow you to backup the remainder.

i could be mislead though as im yet to try it myself.

---

### Post by stchman on 2008-06-26
> **mercules2178 said:**
> I have decided to make the jump to Ubuntu and would like some help with very good backup software that will create and image of my system and then do incremental backups after that. Suggestions would be great!!!

There is a package in the repos called Simple Backup.

```
sudo apt-get install sbackup
```

---

### Post by PeterBBB on 2008-06-26
> Suggestions would be great

Pybackpack is listed in the 'System Tools' as 'File Backup Manager', not installed by default. Very easy to use, allows include/exclude of hidden directories as well.

[http://andrewprice.me.uk/projects/pybackpack/screenshots/0.4/editing_backup_set.png]("http://andrewprice.me.uk/projects/pybackpack/screenshots/0.4/editing_backup_set.png")

The latest backup is stored simply as files in folders, so a restore can even be done with just the copy (cp) command. Simple yet robust IMHO.  

PB

---

### Post by kwilliam on 2008-06-26
Unfortunately, there are dozens of backup tools available for Linux, which makes it hard to choose between them. Part of choosing the right tool is knowing what you want. For instance, do you want to back up EVERYTHING, or just your home folder? Do you want to store the backups on the same computer, on CD/DVD's, on an external hard drive, or on a remote server? Is your primary concern hard drive failure, or accidentally deleting a file? Knowing these things in advance can help you narrow down the choices.

Currently, my favorite is **rdiff-backup**. I use it to backup my whole computer to an external USB hard drive. It doesn't have a graphical interface, but it is pretty simple to use. 

```
rdiff-backup /directory/to/back/up /where/to/back/up/to
```

You can also tell it to ignore certain directories with --exclude, for instance if you have some large files you don't care about backing up. After it's initial run, subsequent backups are incremental. Unlike some tools (like rsync) which backup all changed files, rdiff-backup is smart enough to only back up the parts of the files that have changed, which results in even smaller backups.

If you'd rather have a graphical tool, I believe **pyBackPack** is a graphical front-end for rdiff-backup. Some other choices that look superior to Simple Backup are [**FlyBack**]("http://code.google.com/p/flyback/") and [**TimeVault**]("https://wiki.ubuntu.com/TimeVault"). I haven't tried any of them though, so I can't vouch for them. If you want to back up to CDs or DVDs, I've used **KDar**. (However, I found backing up to DVDs to be tiresome, so I eventually gave in and bought an external hard drive.) And I know this doesn't fit your description of doing incremental backups, but **RemasterSys** is a tool that will backup everything and create a Live DVD with your files on it that you can boot. (Assuming it can fit all your files on one DVD, that is.)


No matter which tool you choose, if you are going to do full backups (e.g. backup the root directory / versus some other directory), there are several folders you will probalby want to NOT back up: /proc, /sys, /tmp, /var/cache, and /var/run. They are all temporary files that get deleted upon reboot anyway. Also, you probably want to exclude /media, which is where CDs, USB drives, and possibly other disk partitions (such as a Windows partition) would be mounted.

---

### Post by kwilliam on 2008-06-26
Oh, here's a thread that might be helpful too: [http://ubuntuforums.org/showthread.php?t=723535](http://ubuntuforums.org/showthread.php?t=723535)

---

### Post by esteckis on 2008-06-26
I have not tried these yet because I use Acronis (not free) and have not totally switched over to UB yet.  But here are 2 links  that seem to have a nice GUI instead of using the terminal.

 Timevault
[http://www.howtoforge.com/snapshot-backups-with-timevault-ubuntu-7.10]("http://www.howtoforge.com/snapshot-backups-with-timevault-ubuntu-7.10")

 FlyBack
[http://www.howtoforge.com/creating-snapshot-backups-with-flyback-ubuntu-7.10]("http://www.howtoforge.com/creating-snapshot-backups-with-flyback-ubuntu-7.10")

---

### Post by LK_gandalf_ on 2008-06-29
Hi, I'm trying Flyback, but I have a doubt.

I created a backup, manually, of my home directory. Then some days ago I created another snapshot, but...on my backup drive (external usb) I see the two directory of the snapshots but each one has the same size of the original one!!

Originale: 11 gb
snapshot #1: 11gb
snapshot #2: 11gb
This is quite disturbing, it uses an huge amount of memory!
I think only the first backup should occupy the same amount of memory of the originale. the following backups should only register the differences in the files, isn't?

---

### Post by kwilliam on 2008-06-30
> **LK_gandalf_ said:**
> Hi, I'm trying Flyback, but I have a doubt.

I created a backup, manually, of my home directory. Then some days ago I created another snapshot, but...on my backup drive (external usb) I see the two directory of the snapshots but each one has the same size of the original one!!

Originale: 11 gb
snapshot #1: 11gb
snapshot #2: 11gb
This is quite disturbing, it uses an huge amount of memory!
I think only the first backup should occupy the same amount of memory of the originale. the following backups should only register the differences in the files, isn't?

Fear not LK_gandalf! Flyback uses "hard links" to duplicate files, which will fool most file system utilities. Any files that have not changed since the last backup are not copied, but "hard linked" to the existing copy, meaning it is the same file physically on the hard drive, but has two different names in the file system directory structure! So if you ask, how big is /backup/time1/file and it says 100mb, if you ask how big is /backup/time2/file it will also say 100mb, because it's the "same" file. However, assuming that these "two" files use up 200mb of physical disk space would be incorrect, since they are really a *single* file with two different names.

If instead of measuring the file size, you use GParted and look at the percent of the partition that is used, you'll see that your backups probably use *less *than 22gb of your hard drive.

---

### Post by Gael33 on 2009-02-24
Is it possible to create a usb startup with Ubuntu and Flyback installed?
I think Flyback is a great program, but in the worst case scenario and the computer won't boot, I had to reinstall Ubuntu 8.10 (64), then reinstall Flyback and then restore the system and programs using the backup on my external hdd. 
The time it took however was considerably shorter than the time it would have taken had it been necessary to install 'everything' from scratch, plus I lost none of my personal and work stuff that I had accumulated over many months.

gael.

PS. I don't have a floppy drive on my PC.
HP Compaq dx2250 Microtower ... AMD 64 Athlon 3000 ... 2 Gig Memory.

---

### Post by lensman3 on 2009-02-24
I use "star" which, I think, is super-tar. I has backup levels and does incremental backups with file compression.  

This script line I use across the network is:

ssh root@192.168.200.11 'star -c -xdev -sparse -acl -link-dirs level=0 -wtardumps -C /boot . ' | dd of=$save_file

Works very well.  A -j flag will compress the output.

---

### Post by John Jason Jordan on 2009-02-24
I have tried all the programs and scripts mentioned in here, and they are all lacking for my needs in one way or another.

Flyback frequently stops in the middle of the backup because it discovered some error. The error messages are incomprehensible unless you are one of the programmers who wrote rsync.

Tar and kdar can't do incrementals.

Timevault won't install on x86_64 unless you do --force-architecture. And if you do it crashes as soon as you start it.

Also, most of the mentioned packages can't find the backup destination unless it is a bookmark or something you can click on without having to enter the destination by typing it in. That especially includes Simple Backup. 

Some of the others can back up only to tape, others only to CD/DVD drives. 

And the biggest problem is that, for us ordinary desktop users with little knowledge of how Linux works, there is no way to figure out includes and excludes. How is a newcomer to Ubuntu supposed to know not to back up /proc and /media, inter alia?

And did I mention that NONE of them have documentation worth a damn?

And while I'm talking about documentation, what happens in the event of catastrophe? How am I supposed to figure out how to do a restore?

I've been using computers for nearly two decades. Only once in all that time have I had to do a complete restore. (Windows NT 4.0 - disk died - and the restore went perfectly.) But I have needed backup data on many other occasions - always just one file or folder that I inadvertently deleted. Just about all the Linux backup utilities are designed for a complete system restore. Few save the files individually so I can just go grab an individual file and restore it.

Still looking for a backup solution that works without bugs and is comprehensible to a non-programmer.

/rantmode: off/

---

### Post by quixote on 2009-02-24
I have to agree that the whole backup problem is a vexed issue.  For what it's worth, this is my system:

Use [Clonezilla]("http://www.clonezilla.org") to make the occasional disk image for those rare total disk crashes.  I've never actually needed to use this for a restore.  I've used it to mirror disks, partitions, or big directories, and it works beautifully.  The "graphics" are straight out of the old DOS days, though!

For the accidentally deleted files, which does happen all too often, I have an external hard drive and mirror to it regularly using rsync.  Rsync is very fast because (like rdiff mentioned above) it writes only the changed parts.  I'm doing only my /home directory, since that's where all my files are.  So there aren't any issues with excluding /proc and so on.

Example:
```
rsync -avu --exclude ".local/share/Trash/" --exclude ".thumbnails/" --exclude ".VirtualBox/" --delete --ignore-errors  /home/quixote/ /mnt/mediavault/quixotebackup/home  1>log-backup.txt 2>log-backup-errs.txt

```

-a means add to the previous set, rather than replace
-v means verbose
-u means update
--exclude [dir] excludes that directory from backup
--delete deletes files on the backup that were deleted on your computer.  You may or may not want that.  If your primary purpose is having old files be recoverable, then obviously not.  (For me, not accumulating junk is the priority.)
--ignore-errors is necessary because of braindead security BS the devs who designed gnome virtual filesystem think we need.  If your rsync runs without it, don't use it!
...then comes the path to the source dir
...then the backup dir
1> directs what would be the screen output to the txt file
2> directs any error messages likewise

The final twist is that if you'd like to automate it, set up a crontab:
```
$crontab -e
``` will create or let you edit the file.  You see this:
```
#m   h    dom    mon    dow   command
```
that's minutes, hour,  day-of-month,  month,  day-of-week  command-to-run
so, in my case, I have my rsync script run every day at 18:30, any day of the week or month:
```
30   18    *    *    *   /home/quixote/backup.sh
```

The "backup.sh" refers to a text file:
```
#!/bin/bash
rsync -avu --exclude ".local/share/Trash/" --exclude ".thumbnails/" --exclude ".VirtualBox/" --delete --ignore-errors  /home/quixote/ /mnt/mediavault/quixotebackup/home  1>log-backup.txt 2>log-backup-errs.txt
```
that contains the shell script I want to run at the specified time.

There's a bit of fiddly and tedious typing, but this is the most functional of the many methods of tried.

Good luck!

---

