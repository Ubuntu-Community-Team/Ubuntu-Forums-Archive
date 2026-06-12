---
title: "Wierd error on bootup (mount --help appears in bootup messages)"
date: 2008-11-20
forum: x86 64-bit Users
---

### Post by bismark on 2008-11-20
I've installed 8.10 amd64 cleanly and configured it for LVM on LUKS.  It boots up fine and I'm running so far so good. The other day though usplash didn't start (bad theme) and I watched my messages scroll by.  I noticed that after the following two lines the output from 'mount -h' appeared. I can't get a snapshot or find it in any log messages so I've tried to recreate it by repeatedly rebooting and quickly scribbling it down. :D

```

kjournald starting. Commit interval 5 seconds
EXT3-fs: mounted filesystem with ordered data mode.
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .

```

Anyone have any suggestions on what file this could be coming from?  I've tested all my entries in fstab (not much more then default) and disabled autofs (though this is too early in the boot process for it).

Really stumped right now. ](*,)

---

