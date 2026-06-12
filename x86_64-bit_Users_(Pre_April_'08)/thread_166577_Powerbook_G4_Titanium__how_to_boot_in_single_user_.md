---
title: "Powerbook G4 Titanium // how to boot in single user mode?"
date: 2006-04-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by jaskah on 2006-04-26
i want to boot into single user mode on my g4 titanium powerbook in order to run fsck and fix my scrambled file system.
ctrl+alt+f1 doesn't work.
can anyone help?
thanks.

---

### Post by davidmaxwaterman on 2006-04-29
[QUOTE=jaskah]i want to boot into single user mode on my g4 titanium powerbook in order to run fsck and fix my scrambled file system.
ctrl+alt+f1 doesn't work.
can anyone help?
thanks.[/QUOTE]

Why don't you boot a live cd and fix it from there?

Max.

---

### Post by jaskah on 2006-04-29
i was able to boot using the ubuntu live but it wasn't clear to me how to run fsck on the damaged system on my computer.

---

### Post by davidmaxwaterman on 2006-04-29
[QUOTE=jaskah]i was able to boot using the ubuntu live but it wasn't clear to me how to run fsck on the damaged system on my computer.[/QUOTE]

Hrm. I would have thought it would be fairly straight forward.

Do you know/remember what the devices where?

I would try this - showing you what it says on my TiBook, in case it helps:

1) use 'parted' to find out the filesystem partition from the partition table :

```
$ sudo parted /dev/hda print
Disk geometry for /dev/hda: 0.000-57231.562 megabytes
Disk label type: mac
Minor    Start       End     Filesystem  Name                  Flags
1          0.000      0.031              Apple
2          0.031      0.985  hfs         untitled              boot
3          0.985  54879.220  ext3        untitled
4      54879.221  57231.562  linux-swap  swap                  swap
```

2) so it looks like the main filesystem is partition number 3. Since mine is OK, I can confirm that with 'mount' :

```
$ mount
/dev/hda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /lib/modules/2.6.12-10-powerpc/volatile type tmpfs (rw,mode=0755)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)

```

but you won't be able to do that - it'll only show you what the live cd has mounted (I've no idea what that would be).

3) So, now you should just run fsck on /dev/hda3. You'll need to use sudo, I expect. I won't do this on my system, since it isn't broken, and trying to fix things that aren't broken, in my experience, tends to break them :) Look in the man page for fsck to tell how to run it...you might have to specificy a type of filesystem (not sure).

4) Once you've done fsck, you could try to mount it - something like :

```
$ sudo mkdir /mnt/other_root
$ sudo mount /dev/hda2 /mnt/other_root
$ ls /mnt/other_root
```

and try to fix anything you can see that is wrong in that filesystem (I'd guess it would be ok to copy stuff from the livecd's filesystem if necessary, though that would indicate some serious breakage and YMMV).

Hope this helps.

Max.

---

### Post by aimislame15 on 2006-04-30
If this is a dual boot system with linux and osx, click osx and then hold apple+s. This will take you to single user mode and you can do fsck -f from there.

---

