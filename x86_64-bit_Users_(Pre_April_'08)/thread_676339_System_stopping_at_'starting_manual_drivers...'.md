---
title: "System stopping at 'starting manual drivers...'"
date: 2008-01-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by Thorning on 2008-01-23
This problem began with video driver updates and a conflict I had with nvidia-glx-new driver required by the extra visual effects desktop setting and my nvidia system drivers.

Now however I have a totally different problem which fits much better in this category.

After doing some changes to my xorg.conf and installing, un and re-installing nvidia-glx-new the system all of a sudden would not go passed "Starting manual drivers..." when booting and mounting my system drive as read-only, thus disabling me to do any changes or updates.

This is what i wrote in the previous thread:

I can start the system problem free with x-server (vesa-generic) by selecting a previous kernel in the boot-list and the drive is then R/W.
Using this, I completely removed nvidia-glx-new and rebooted as normal, but the problem remained.

The system stops after the following, (as I see it):

* starting kernel event manager
*loading hardware driver
udevd-event[3747]: run program: '/sbin/modprobe' abnormal exit
*setting system clock
*loading kernel modules...
*loading manual driver...
...
...
... and there's nothing more after this.

*** At this point the system is still responding but I can't see anything on the other tty's.
I then press ctrl+alt+del and it continues with: ***

init:rcS main process (2592) killed by TERM signal
init:rc6 main process (4919) killed by TERM signal

kinitname_to_dev_t(/dev/disk/by-uuid/c3832ccd-45blablabla)=hdb6 (3,70)
kinit: trying to remove from /dev/disk/by-uuid/c3832ccd-45blablabla..
kinit: No resume image, doing normal boot

*loading ACPI modules...
*starting ACPI modules...
acpid: can't open /var/log/acpid: Read-only file system
*starting system log daemon...
chown:changing ownership of /var/log/mail...: read-only file system
chown:changing ownership of /var/log/...: read-only file system
chown:changing ownership of /var/log/...: read-only file system
etc
etc
etc
*starting kernel log daemon [OK]
*starting system message bud dbus [OK]
*starting ... [OK]
*starting ... [OK]

fsck reports no problems.
I have not touched fstab or mtab.

---

