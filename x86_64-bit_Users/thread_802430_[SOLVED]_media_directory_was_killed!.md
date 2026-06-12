---
title: "[SOLVED] /media directory was killed!"
date: 2008-05-21
forum: x86 64-bit Users
---

### Post by ddales on 2008-05-21
Hi all,

Ok, I did something very stupid and in retrospect it's actually unbelievable but nonetheless still true.

I have 2 hard drives and installed ntfs support.  The second drive I mounted as an ntfs partition and everything was going great.  That is, until I decided to play a DVD Movie.

That's when I realized I had mounted the ntfs partition as /media/Backup.  Yes, that's right, /media/Backup.

Of course, that whacked my linux type /media directory and now I can't automount DVDs or CDs or anything else because the directory structure from the original /media directory, the one HAL expects, is wiped out.

Any suggestions?

---

### Post by pytheas22 on 2008-05-21
Did you try rebooting?  I made a similar mistake (mounted a USB stick over ~/Desktop) but after a reboot everything was back to normal.

---

### Post by Kilz on 2008-05-21
> **ddales said:**
> Hi all,

Ok, I did something very stupid and in retrospect it's actually unbelievable but nonetheless still true.

I have 2 hard drives and installed ntfs support.  The second drive I mounted as an ntfs partition and everything was going great.  That is, until I decided to play a DVD Movie.

That's when I realized I had mounted the ntfs partition as /media/Backup.  Yes, that's right, /media/Backup.

Of course, that whacked my linux type /media directory and now I can't automount DVDs or CDs or anything else because the directory structure from the original /media directory, the one HAL expects, is wiped out.

Any suggestions?

```
sudo mkdir /media
```

---

### Post by ddales on 2008-05-23
This turned out to be really bad news.  Since the /media was naturally not it's own filesystem I couldn't rebuild it.  I attempted to rebuild the directories and links using another box as an example which also didn't work.

I ended up just reinstalling the system.  Lesson learned.

---

### Post by Cappy on 2008-05-23
/media is just a normal directory.

If you had mounted a filesystem on the directory itself (/media) then all you need to do is change the mount point in /etc/fstab for the ntfs partition and reboot.

/media/Backup is a perfectly good place to mount a filesystem. There would be nothing wrong if you did this.

---

