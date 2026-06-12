---
title: "[SOLVED] strange mount.ntfs behaviour"
date: 2008-03-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by LoneWolfJack on 2008-03-11
Ok, I have an NTFS raid 0 array that I need for backup purposes and that I can't whipe because I carry these drives from one PC to another... and since Windows doesn't speak ext3...

Now for some reason, ubuntu doesn't mount the array automatically, which is no big deal, as I can easily mount it with
> sudo mount /dev/dm-1 /home/~/backup

Today I decided to have this done automatically. I know this can be done in fstab, but due to the complicated nature of the commands there, the fact that the drives sometimes are not (physically) present and last but not least the fact that I already have a working solution I decided to simply add the command to my root crontab.

So I added:
> @reboot mount /dev/dm-1 /home/~/backup

Which worked fine. However, here comes the problem:
now upon every reboot, all hell is breaking loose in terms of disk activity. It takes like 5 minutes for the drives to calm down and even then, all couple of seconds they crunch away for a couple seconds, also causing my SCSI raid array (which ubuntu is installed on) to become active at the same time.

Using "top" I found out that the process responsible is the aforementioned mount.ntfs

If I manually mount the drives, this doesn't happen.

Any ideas?

---

### Post by Zorael on 2008-03-11
I don't have the know-how to help you with your problem, but do note that there are ext2/ext3 drivers for Windows. They'll ignore permissions, of course, which makes it a grand vulnerability. But if you're not too worried about that, give it a go.

There's one over at [http://www.fs-driver.org/](http://www.fs-driver.org/), and I know there are more out there.

Google and you shall find.

---

### Post by konungursvia on 2008-03-12
For external drives, you shouldn't bother with fstab, which is for internals. Ubuntu should be able to mount the external drive automatically, provided you mount it manually, then share it using volume management software.

---

### Post by LoneWolfJack on 2008-03-12
Like I said... mounting is actually not the problem... the problem is that when mounting it automatically through cron, I am getting insane disk activity that's pretty annoying.

So bottom line is, the mount command used in terminal doesn't produce the same problem (disk activity) the very same command causes when called through cron and I have no idea why.

ext3 for windows is not an option... there's critical data on these drives and I don't trust non-native filesystems.

---

### Post by LoneWolfJack on 2008-03-16
Apparently, the problem was not the ntfs mount thingy but trackerd that was working to index the removable devices every time they were present. 

Disabling trackerd fixed the issue.

---

