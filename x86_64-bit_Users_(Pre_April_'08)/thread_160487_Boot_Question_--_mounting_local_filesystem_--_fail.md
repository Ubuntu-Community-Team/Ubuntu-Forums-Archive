---
title: "Boot Question -- mounting local filesystem -- fail"
date: 2006-04-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by llanitedave on 2006-04-15
I'm not sure that this is a problem, but it seems to have started recently:

During the boot process, my system reports "fail" on the "mounting local filesystems" step.

I have an AMD64 chip, running 64bit 5.10, with two internal hard drives and a DVD writer.  I also use a USB memory stick on occasion.

Everything seems to work once it's booted up, as far as I can see.

Could this be the symptom of something I'm NOT seeing?  Can there be a chroot problem going on (I recently installed one of those as well).

Any insight or advice is appreciated.

---

### Post by bikeboy on 2006-04-15
You could try checking some logs once you've booted. Look in /var/log for most of them.

dmesg might have something. Then you may be able to narrow down which filesytem is generating the problem and what it is.

---

### Post by Mustard on 2006-04-15
I would suspect that you've got some extra entries in your /etc/fstab to do wtih a chroot environment that you have set up and they are not able to be mounted at boot, so its throwing out spurious error messages that show up as a 'fail' in the boot progress display.

I've been getting the same error message lately after setting up a chroot environment.  While I'm not using the chroot, I've just commented out all the relevant entries in my /etc/fstab.

If I need them again, I can just uncomment them, and then mount -a to mount them again.

---

### Post by llanitedave on 2006-04-15
Thanks, both of you. I'll try both of the things you suggested.  I thought it might have something to do with the chroot, since I never noticed it till after that was installed.  I think I might have some other problems with that as well, but that's another thread!

One thing at a time...

---

### Post by lubosz on 2007-12-03
i had the same problem. the solution was to clear some old ntfs partitions that didnt exist anymore in the /etc/fstab

thx!

---

