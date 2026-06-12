---
title: "Possible pmount problem?"
date: 2006-08-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by KenF on 2006-08-05
Last week I installed the upgrade to pmount:
 0.9.11-1ubuntu1 (dapper-updates)
I didn't notice it at first, but now the write speed to
my external USB drive (vfat filesystem) seems slow.

1.  Has anyone else noticed something similar?  I didn't
notice until I started writing a series of 200MB files, but
I would say that it is a factor of 5 slower than before.

2.  Is there any reason why I shouldn't downgrade to the
previous version (0.9.11-1(dapper))?  I don't think the
update came with a reason.

More Info:
    a.  The downgrade didn't seem to help.  i.e. may not be pmount, but some other update?
    b.  The files are actually 840MB.
    c.  I'm getting about 1MB/sec writes.
    d.  contents of /etc/mtab:
/dev/sde1 /media/IOMEGA_HD1 vfat rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8 0 0

    e.  There is something else that is truly weird.  Here is an ls -ltr:
-rwx------ 1 ken ken 840000000 2006-08-04 21:37 capture001.dv
-rwx------ 1 ken ken 840000000 2006-08-04 21:40 capture002.dv
-rwx------ 1 ken ken 840000000 2006-08-04 21:44 capture003.dv
-rwx------ 1 ken ken 840000000 2006-08-04 21:48 capture004.dv
-rwx------ 1 ken ken 840000000 2006-08-04 21:52 capture005.dv
-rwx------ 1 ken ken 840000000 2006-08-04 21:56 capture006.dv
-rw------- 1 ken ken 840000000 2006-08-04 22:00 capture007.dv
-rw------- 1 ken ken 840000000 2006-08-04 22:04 capture008.dv
-rwx------ 1 ken ken 441810944 2006-08-05 08:59 capture009.dv

   These were all written on 2006-08-05 at about 8am PDT.  They look like they are spaced 4 minutes apart, but they are in fact taking 14 minutes -- i.e. the time stamps are bogus:  After the write finishes, the date/time gets set to be the previous night???



Thanks,

Ken

---

### Post by KenF on 2006-08-05
Just a quick reply to my own problem.

1.  I looked at syslog (dmesg) and found that it was only recognizing a high-speed device in a full-speed hub (USB1.1).
2.  I unmounted, powered off, and disconnected the device.  Same thing upon reconnect.

3.  I'm not used to doing this under Linux, but having been trained by MSWindows, I  rebooted.  Yuck.  That did the trick.  All is fine.  Speed is now back to normal (10 times or more).


Ken

---

