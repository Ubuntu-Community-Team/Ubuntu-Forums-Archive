---
title: "Automatically create and delete mount folders for Fstab"
date: 2008-07-03
forum: x86 64-bit Users
---

### Post by schopo on 2008-07-03
I was puzzled by how easily Nautilus can just mount something by clicking it: it creates a directory, names it correctly, mounts and removes the directory upon dismount.
Now I was wondering if it is possible to make an ordinary mount command create and delete directories almost like that. For example if I type
"sudo mount /dev/hda1 /media/hda1"
I'dd want the not yet existing directory /media/hda1 to be created instead of giving the error 
"mout: mount point /media/hda1 does not exist".

In the same principle I'dd want to put a complete list of all possible devices in my Fstab and let it mount only the ones that are physically there, even though the mount points are still to be created.
with all possible devices I mean sda through sdd and partition 1 through 4 for all of them: 16 total

This since my device setup changes a lot: repartitioning hdd's and 2 USB drives.

TIA

---

### Post by schopo on 2008-07-14
(Bump)

At the moment I have simply created 16 directories named hda1,hda2 - hdc3,hdc4 and it works correctly. But that is, of course, very messy and difficult to quickly navigate. I stumble into empty folders hourly :S

Probably Udev rules can help me out but I can't find nub-friendly documentation...

Any directions would be greatly appreciated :S

---

### Post by Bonster on 2008-08-05
Try this
[http://www.youtube.com/watch?v=o12k3gRkdIc](http://www.youtube.com/watch?v=o12k3gRkdIc)

You might need to change the mount points to ur likeing. Not sure if this is wat ur looking for.

---

### Post by noshellswill on 2008-08-05
> **Bonster said:**
> Try this
[http://www.youtube.com/watch?v=o12k3gRkdIc](http://www.youtube.com/watch?v=o12k3gRkdIc)

You might need to change the mount points to ur likeing. Not sure if this is wat ur looking for.
I had a look. Well intentioned, I'm sure. But presentation is strictly for weinerdudes/byteboyz. 

Why the OS ever allows this issue to occur simply escapes me.

---

### Post by InfinityCircuit on 2008-08-05
You can use pmount.  This will allow a user to mount drives without sudo privileges and will create/remove the folders automatically. You just add /dev/sda1, etc. for what you want in /etc/pmount.allow.  Beyond pmount you must use udev rules.

---

