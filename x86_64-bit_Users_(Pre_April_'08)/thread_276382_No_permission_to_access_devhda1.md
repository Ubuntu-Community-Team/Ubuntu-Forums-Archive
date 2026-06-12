---
title: "No permission to access /dev/hda1"
date: 2006-10-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by Jadix on 2006-10-12
Hi,
I'm dual booting windows and ubuntu, and would really like to mount my windows drive so that i can grab some things off of it.  when i type "sudo mount /dev/hda1 /media/windows -t ntfs -0 nls=utf8, umask 000000" it says "/dev/hda1 is already mounted on /tmp/disks-conf-hda1".

When I try to go to /tmp/disks-conf-hda1 it says I do not have permission.  I tried "sudo chmod 777 /tmp/disks-conf-hda1" and it said "chmod: changing permissions on /tmp/disks-conf-hda1 : Read only File System".  

When i try to access the same folder again it says, "Permission denied".  Can anyone help me out?:-?

---

### Post by kidders on 2006-10-12
Hi there,

*Should* you be able to access /tmp/disks-conf-hda1? (What does **ls -ld /tmp/disks-conf-hda1** say about it?)

Either way, my suggestion would be to add (or edit) a line in your /etc/fstab to have your NTFS partition mounted when (and how) you like it.

---

