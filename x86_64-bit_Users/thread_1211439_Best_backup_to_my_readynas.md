---
title: "Best backup to my readynas"
date: 2009-07-12
forum: x86 64-bit Users
---

### Post by inphektion on 2009-07-12
I use clonezilla monthly to clone my entire hdd as I have HFS, ext3, ext4, filesystems.  However I'd like to run daily or every other day backups of my home folder and maybe weeklies of root.  I need to back them up to a readynas I have that I will nfs mount when I want to backup.  

What you guys think best software to use for this?  I don't like rsync as I want to have some history.  Not quite sure how to do rsync with rdiff which would probably do what I wanted.  I've looked at back in time which seems to offer everything I want just haven't tested it out yet.  Anything I'm missing that is easy for what I want?

---

### Post by bedtime_with_the_bear on 2009-07-12
I use rsnapshot for my backups, it's configurable for any interval of backups - hourly/daily/weekly/monthly are pre-configured, but you can configure any arbitrary period - it's how you run it that really determines the backup interval. It sounds complicated, but it really isn't. It performs incremental forever backups: using rdiff and rsync, it only copies changed files, but requires that the destination filesystem supports hard links so that it can present what appears to be a complete directory structure for every backup even though only the changes have been copied - very nice (if you want to see how much space is used by each backup, use rsnapshot du rather than du. Regular du doesn't know to ignore the hard linked files so it reports the full size of each backup). BackupPC does a very similar thing, though I found it more complicated to configure, and is also more heavyweight since it is designed to backup remote clients over the network also. It does come with a web based frontend so may be better for you. BackupPC does it's own scheduling, and you can configure blackout periods when backups should never be taken, but you need to add rsnapshot to your crontab (crontab -e, man 5 crontab). After that, it's totally invisible except for the occasional disk access when it's doing it's work.

Not sure if HFS supports hard links so don't know if rsnapshot would be best for you, but BackupPC supports many different backup formats (rsync,tar,cpio, to name just a few). I think BackupPC uses the hard link thing for incremental backups, but it is pretty insistent on doing a full backup regularly too - I'll let you decide if that's gonna work for you, but I personally found it too time consuming on my home PC when I'm trying to go to bed and it wants to spend 5 hours trawling through my disks (I don't leave the PC on) so I personally prefer the way rsnapshot does things - if you want to backup remote machines, rsnapshot will do that as it supports any protocol rsync supports, including ssh. Both rsnapshot and BackupPC are in the repositories, and will keep as much or as little history as you want.

---

### Post by inphektion on 2009-07-13
rsnapshot might be good.  I don't mind not having a gui and I'd only use it for my /home and / partitions so both are ext4.  The other partitions don't change often so they get covered with the entire clonezilla image.

I'll report back

---

### Post by jefelex on 2009-07-14
> **bedtime_with_the_bear said:**
> I use rsnapshot for my backups, it's configurable for any interval of backups -
 ...snip...
 Both rsnapshot and BackupPC are in the repositories, and will keep as much or as little history as you want.

Thanks for the information!  I've been looking for a good backup program for a long time, and havn't come across anything that I like yet.  I can't remember what I have installed right now (I'm not at my home computer at present) but I don't even know what it's doing, since I can't find any configure files, either in my home dir, or /etc or even it's executable directory! - nor where it put(s) the backups it has made if any!! :eek:

John

---

### Post by bedtime_with_the_bear on 2009-07-14
> **jefelex said:**
> Thanks for the information!

No problem - I vastly prefer rsnapshot as it is so unobtrusive. BackupPC is great, but requires far more configuration and in the default Ubuntu install, runs as the backuppc user - which is great from as security point of view, but bad from a backup point of view as it is unable to backup your files or many system files as this user. You have to do the extra configuration via sudo to make it work. I'm not criticising BackupPC since it's targetted at bigger networks than a single PC in your home office :)

rsnapshot will store its backups in /.snapshots by default, and BackupPC stores its backups under /var/lib/backuppc/pc/localhost by default

---

### Post by jefelex on 2009-07-14
Excellent!!  I'm headin home in a few minutes, and I'm gonna check out both - I do like command line (reminds me of my old Apple ][ and CPM!) although I have to admit that almost everything is graphic these days, and my command line skill has "deprecated!!" :-)

---

