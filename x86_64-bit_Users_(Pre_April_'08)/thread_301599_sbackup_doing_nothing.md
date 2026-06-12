---
title: "sbackup doing nothing"
date: 2006-11-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by t_ras on 2006-11-17
I installed Sbackup to back up my comp (kubuntu 6.10 AMD64).
Configured it to bkp files to a near by comp I have with FTP server.
checked connection fine through sbackup (I also sow it connecting in the FTP server consul). Then I tried "backup now" but nothing got done (it stayed connected to FTP server till timed out).in fact, the moment I closed the window backing up process died...
I tried setting it up to automatically run, but it did nothing.
Is there any problem with it running AMD64? I'm I missing something?
Can some one advice me of another program to use? Maybe a good script?

Thanks

---

### Post by LeslieL on 2006-11-17
I seem to have that problem too. If I backup to a new directory everything works (I put the backup on another partition), but it won't write to that directory again. The directory has read & write permissions for everyone. I don't know what's going on.

---

### Post by John Jason Jordan on 2006-11-17
> **LeslieL said:**
> I seem to have that problem too. If I backup to a new directory everything works (I put the backup on another partition), but it won't write to that directory again. The directory has read & write permissions for everyone. I don't know what's going on.
I've tried since Breezy to get SBackup to work, but I have the same problems. In my case I was trying to back up to a removable USB drive. The only way I could ever get it to work was to let it back up to /var, which is its default.

Eventually I gave up and now I use Kdar instead. I don't like it though, and I wish there was a good standalone desktop backup utility useful for an "as needed" basis.

---

### Post by LeslieL on 2006-11-17
I had it backing up automatically at 11 p.m every night under Breezy - to hda2/Backups. Now it makes one backup per directory. Now that I've figured that out, I can work around it, but it's annoying.

---

### Post by SteveHoffmanUK on 2006-11-18
Problems also here with Sbackup. I have been faithfully using it to write backup (full and incremental) backup files to an external HDD. I have never tried to restore from them, though, so I installed Ubuntu Edgy Eft onto a spare laptop, installed Sbackup on it, plugged in my external HDD and tried to do a restore by doing this:

Ticked "Use custom"
Successfully dragged the latest Sbackup full restore file from the external HDD to the Restore files/directories panel name field
Clicked "Apply"
...but nothing happened, and got the error messages
Error: backups directory does not exist!
Error: no backups found in the target directory

Note: My laptop/desktop are NOT 64-bit machines. Maybe this is the wrong thread and I should also put this on another forum?
Also tried first copying the backup file to my desktop and then trying to get the Restore program to recognise the file, but still get the same errors.

Do we conclude that Sbackup only works from its default file /var/backup? That would be truly stupid, since best practice is always to put security backup files on an external medium.

Or do we conclude that Sbackup doesn't work at all?

---

### Post by fabertawe on 2006-11-18
I had a similar problem Steve. I used it when I started with Ubuntu and needed to do a restore of '/home' but it was corrupted somehow (I forget exactly what). I now keep an incremental mirror of '/home' with a simple one liner using rsync...
```
sudo rsync -az --progress --delete-after /home /media/storage/backup
```

Paul

---

### Post by t_ras on 2006-11-18
Can I use rsync to windows FTP server?

---

### Post by fabertawe on 2006-11-19
> **t_ras said:**
> Can I use rsync to windows FTP server?

I've never used an FTP server and couldn't tell you, sorry. Check out 'man rsync', it's intended to work over networks so maybe it's worth testing.

Paul

---

