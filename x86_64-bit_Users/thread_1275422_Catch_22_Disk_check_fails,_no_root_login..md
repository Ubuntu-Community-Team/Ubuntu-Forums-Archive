---
title: "Catch 22: Disk check fails, no root login."
date: 2009-09-25
forum: x86 64-bit Users
---

### Post by AKADAP on 2009-09-25
Attempting to boot my computer, it spends a bunch of time checking the disk, then fails with the following:

* An automatic file system check (fsck) of the root file system failed. A manual fsck  must be performed, then the system restarted. The fsck should be performed in maintenance mode with the root filesystem mounted in read-only mode.
* The root filesystem is currently mounted in read-only mode. A maintenance shell will now be started.
After performing system maintenance, press CONTROL-D to terminate the maintenance shell and restart the system.
Give root password for maintenance
(or type Control-D to continue):

Fine, except there is no root password because the default setup on Ubuntu is to leave the root account disabled. There are instructions on how to enable the root password, but that requires logging in which I can't do.

So, how do I recover from this mess?

---

### Post by AKADAP on 2009-09-26
I got the system working again.

I had a spare hard drive, I put it in and grabbed my Ubuntu 64 9.04 install CD. It would not boot because it had gotten scratched.
I had used the last CD on the spindle to make that disk, at it took me a long time to remember that I had a few free sample disks that come with various DVD-ROM drives.
I was able to burn a new install disk, install Ubuntu on the spare hard drive, update it, then run fsck -M /dev/sda1 (took a while to determine which disk was the one that needed repair) to fix the damaged drive.

I have now enabled the root user on my system. Without root, one can not debug or fix a broken system without spare hardware.

---

### Post by AKADAP on 2009-09-26
I have never been able to mark a thread I created as fixed
Never mind, I just found out how.

---

