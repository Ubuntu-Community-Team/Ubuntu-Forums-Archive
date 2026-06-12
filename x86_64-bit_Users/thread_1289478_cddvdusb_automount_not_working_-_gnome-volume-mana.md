---
title: "cd/dvd/usb automount not working - gnome-volume-manager or hal problem?"
date: 2009-10-12
forum: x86 64-bit Users
---

### Post by AdamGott on 2009-10-12
I have been trying to fix this problem for a long time but today I am getting serious about it!

Inserting CD or USB device does not bring up any popups for automount/autoexecute helper apps.  All Linux functions seem to work (I can manually mount devices either on the command line or in the 'computer' window of the nautilus file browser).

I have found that my gnome-volume-manager is not a running process in my system monitor and I have tried uninstalling and reinstalling gvm.

Any ideas?  It used to work for me back in the hardy heron days.

---

### Post by AdamGott on 2009-10-12
When I try to force start HAL I get:

Error binding udev_event socket: Address already in use


I tried to force restart udev with this:

sudo /etc/init.d/udev restart

but I still get the same error starting HAL.

Here is the hal.log:

11:54:03.268 [I] hald.c:680: hal 0.5.12
11:54:03.268 [I] hald.c:681: using child timeout 250s
11:54:03.268 [I] hald.c:746: Will not daemonize
11:54:03.268 [I] hald_dbus.c:5421: local server is listening at unix:abstract=/var/run/hald/dbus-Ohsj4PCRha,guid=fef0a072fbc6c0aaa27f0a584ad36d3b
11:54:03.272 [I] ck-tracker.c:391: got seat '/org/freedesktop/ConsoleKit/Seat1'
11:54:03.272 [I] ck-tracker.c:321: got session '/org/freedesktop/ConsoleKit/Session1' for seat '/org/freedesktop/ConsoleKit/Seat1'
11:54:03.273 [I] ck-tracker.c:274: Got active state (ACTIVE) and uid 1000 on session '/org/freedesktop/ConsoleKit/Session1'
11:54:03.273 [I] ck-tracker.c:342: Got all sessions on seat '/org/freedesktop/ConsoleKit/Seat1'
11:54:03.273 [I] ck-tracker.c:418: Got seats
11:54:03.273 [I] ck-tracker.c:816: Got seats and sessions
Runner started - allowed paths are '/usr/lib/hal:/usr/lib/hal/scripts:/usr/bin'
11:54:03.275 [I] hald_runner.c:301: Runner has pid 7668
11:54:03.275 [I] hald_runner.c:182: runner connection is 0x2469300
11:54:03.276 [W] osspec.c:387: Unable to open /proc/mdstat: No such file or directory
11:54:03.278 [I] mmap_cache.c:278: cache mtime is 1248042379
Error binding udev_event socket: Address already in use

---

### Post by AdamGott on 2009-10-13
11:54:03.276 [W] osspec.c:387: Unable to open /proc/mdstat: No such file or directory

Could this one be the problem?

---

### Post by AdamGott on 2009-10-16
Anyone?  I have searched and searched and tried everything.

I see that the new Ubuntu is ditching HAL and using something else (devicekit), should I just wait and see if that works better?

---

### Post by AdamGott on 2009-10-16
fstab:

#UUID=a1b6b54d-bc4c-4bc7-820f-f947d751d533 none swap sw 0 0
/dev/cdrom /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

here is dmesg | tail output:

[14652.815456] end_request: I/O error, dev sr0, sector 787984
[14652.816975] end_request: I/O error, dev sr0, sector 789224
[14652.818345] end_request: I/O error, dev sr0, sector 787976
[14652.819558] end_request: I/O error, dev sr0, sector 1248
[14652.820920] end_request: I/O error, dev sr0, sector 2496
[14652.822507] end_request: I/O error, dev sr0, sector 1248
[14652.823796] end_request: I/O error, dev sr0, sector 2496
[14652.823830] UDF-fs: No partition found (1)
[14652.878271] end_request: I/O error, dev sr0, sector 64
[14652.878296] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16


What is /dev/sr0 and why is it doing this when I insert a CD?  I think that this has something to do with this being a SATA drive and not EIDE?

---

### Post by AdamGott on 2009-10-17
It was an fstab issue I guess.  I changed my automount device to /dev/sr0 with a mount point of /dev/dvdrw.  In my media directory there was a file called cdrom and a directory called cdrom0.  The cdrom file linked to the cdrom0 directory and for some reason this was causing a bit of havoc.  After I deleted both of these the automount now works for cd/dvd media and for USB.

I don't know why this was affecting USB but I guess it doesn't matter because it works now.

---

### Post by laxman31 on 2009-11-03
How do you change your automount device/mount point?

---

### Post by AdamGott on 2009-11-03
> **laxman31 said:**
> How do you change your automount device/mount point?

you have to edit your fstab - 

sudo gedit /etc/fstab


here is a link to an old forum post:

 [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

There is lots of info on the web, search for 'ubuntu edit fstab'

---

