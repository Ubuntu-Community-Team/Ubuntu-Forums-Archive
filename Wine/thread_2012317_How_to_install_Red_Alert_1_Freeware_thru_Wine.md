---
title: "How to install Red Alert 1 Freeware thru Wine"
date: 2012-06-28
forum: Wine
---

### Post by linux.convert on 2012-06-28
I have not found any threads about installing Red Alert 1 in Linux, I personally have questions about it, but I hope this can help others. I use AcetoneISO to mount the .ISO and the SETUP.EXE runs ok but it shows a window that says

"Unable to locate necessary files. Please run Setup.exe from the CD-ROM disc."

I have tried to mount the allied disk .iso thru the terminal a couple of different ways.

```

USER@USER-AODXXX:~$ sudo mount -o loop /home/ldc/Games/Red Alert 1/RedAlert1_AlliedDisc/RedAlert1_AlliedDisc/CD1_ALLIED_DISC.ISO /media/disk
[sudo] password for ldc: 
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

---

### Post by mateo14 on 2012-06-29
> **linux.convert said:**
> I have not found any threads about installing Red Alert 1 in Linux, I personally have questions about it, but I hope this can help others. I use AcetoneISO to mount the .ISO and the SETUP.EXE runs ok but it shows a window that says

"Unable to locate necessary files. Please run Setup.exe from the CD-ROM disc."

I have tried to mount the allied disk .iso thru the terminal a couple of different ways.

```

USER@USER-AODXXX:~$ sudo mount -o loop /home/ldc/Games/Red Alert 1/RedAlert1_AlliedDisc/RedAlert1_AlliedDisc/CD1_ALLIED_DISC.ISO /media/disk
[sudo] password for ldc: 
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

Here is native version of Red Alert 1:

[http://openra.res0l.net/download/linux/](http://openra.res0l.net/download/linux/)

---

### Post by linux.convert on 2012-06-29
I have OpenRA, and besides some minor graphical issues, it doesn't appear to have the single player campaign or anything like that. Or the music, gotta have the music C&C MUSIC FTW!!!!!!!!

Sorry had to do that, also about the code I posted I figured out why it wasn't working and fixed it, minor little syntax error stuff. I now have the RA1 Allied.iso mounted, it still gives the same "necessary files" issue, which is the next thing to work on.

---

### Post by linux.convert on 2012-06-30
Here's an update on Tiberium Sun, in case anyone is interested, the .rar files for Tiberium Sun and Firestorm does not require installation and runs really good right out of the box, the only problem I have is some minor mouse/flickering issues.

Other than that video/cutscenes/briefings works fine.

---

