---
title: "Booting bug"
date: 2009-09-19
forum: x86 64-bit Users
---

### Post by Damouf on 2009-09-19
Good morning,

Quite naive ubuntu user for few months now, still not very keen on using the console. Ubuntu is bugging at booting due to unclean shut down (my mate turned off the main power before it finished). Now when booting, it is trying to check harddrive until it blocks at step 1/5 and switch to console with the following screen:

/dev/sda1: Multiply-claimed block(s) in inode 10887241: 43559092
/dev/sda1: (There are 3 inodes containing multiply-claimed blocks.)

/dev/sda1: File /var/log/Xorg.0.log.old (inode #10887230, mod time Wed Sep 16 22:41:46 2009) has 1 multiply-claimed
 block(s), shared with 1 file(s):
/dev/sda1: /var/log/syslog (inode #10887241, mod time Thu Sep 17 11:47:48 2009)
/dev/sda1:

/dev/sda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
          (i.e., without -a or -p options)
fsck died with exit status 4
[fail]
 *An automatic file system check (fsck) of the root filesystem failed.
A manual fsck should be performed in maintenance mode with the root file system mounted in read-only mode.
*The root filesystem is currently mounted in read-only mode.
A maintenance shell will now be started.
After performing system maintenance, press control-D to terminate the maintenance shell and restart the system.
bash: no job control in this shell
root@ln-dam-desktop:~#

Could someone help me to launch manual fsck?

Many thanks for your help.

Damien

---

### Post by Joshua Lückers on 2009-09-19
When that happens you will see the commandline right? If yes just type fsck and hit enter.
When it's done press control+D.

---

### Post by Damouf on 2009-09-19
Problem solved. Thanks Joshua!:)

---

