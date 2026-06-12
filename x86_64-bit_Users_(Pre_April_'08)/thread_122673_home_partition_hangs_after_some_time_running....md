---
title: "/home partition hangs after some time running..."
date: 2006-01-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by n3ofr on 2006-01-28
Hi all,

This is my first post in the Ubuntu community, so be comprensive if I hadn't putted the topic in the good forum.

So here is my problem :

I have a standalone /home ext3 partition (mounted with defaults options in /etc/fstab). After about 30mn~1hour working on it, a problem happends and when I want to save a file on it I face the "Filesystem is read-only" message.

Thanks for you help, and I apologize for my poor English :-k

---

### Post by GTvulse on 2006-01-28
When that happens, does anything funky shows up in the kernel logs?
```
dmesg | tail -80 | less
```

When the error message happens, try to reboot your box while forcing a filesystem checkup on boot:
```
sudo /sbin/shutdown -r -F now
```

---

### Post by n3ofr on 2006-01-28
Thanks for the help, I'll try to send you my dmesg when it will crash (soon, soon...)
(but opening firefox is problematic when it can't write on /home !)

When it crashes on reboot, the check is already launched "automatically" because he found errors when mounting the filesystem and checking the journal.

---

### Post by n3ofr on 2006-01-28
[ 1508.056772] ext3_abort called.
[ 1508.056778] EXT3-fs error (device hda7): ext3_journal_start_sb: Detected aborted journal
[ 1508.056782] Remounting filesystem read-only

---

### Post by n3ofr on 2006-01-28
any idea ?

I precise that's a laptop if it could help

---

### Post by GTvulse on 2006-01-28
Oh Boy!
  
The journal is very much borked. Boot into single user mode, and do this:
```

umount /home
fsck.ext3 -C 0 -c -D -f -v /dev/hda7
fsck.ext3 -C 0 -f -v /dev/hda7
mount /home
exit

```

The system should continue booting up into your graphical login screen. The explanation: The first time do a forced check of the filesystem while checking for bad blocks and rebuilding all directory entries. Rebuliding directories leaves the filesystem dirty so you need to run fsck once more, but this time you don't need to check for bad blocks. The "-C 0" bit is for the "thermometer" thingy.

---

### Post by n3ofr on 2006-01-28
Ok I've done this little trick and thank you very much for the help.

Now, let's see if it works !

Did you know something to convert a ext3 drive to ext2 ? Because I compile a lot of C++, and with 100+ files updated each time... journaling is maybe a bad idea

---

### Post by n3ofr on 2006-01-28
Ergh it did not work... I can't write files again

---

### Post by GTvulse on 2006-01-28
Hmmm... That's bad.. But not all is lost. Edit /etc/fstab and change the mount fstype from ext3 to ext2 (yup, its that simple ;-). 
```
sudo gedit /etc/fstab
```
and do the change. That'll save you from the journal corruption problems but then you'll want to reduce file system checking to something like every 10 mounts or thereabouts... ```
sudo tune2fs -c 10 /dev/hda7
```

If you can use a spare partition, or a different one, you can rescue your data and the partition yet. (I've done this a zillion times already ;-)). Let's assume the simple scenario first (but do tell me that you have a spare partition, that would make things so much easier ;-)). ** Works if the root partition can hold the contents of your home partition for a while.**

Boot into single user mode and do:
```

cd /home
tar jcf /var/tmp/myaccount.tar.bz2 myhomedir
cd
umount /home
mkfs.ext3 -c -L ubuntu_home -j -O dir_index,filetype,sparse_super -T news -v /dev/hda7
mount /home
tar jxf /var/tmp/myaccount.tar.bz2 -C /home

```
Do a ```
ls /home
``` to make sure your data is restored and if so, type ```
exit
``` to continue booting into graphical mode.

If you do have a spare partition that can keep your home data (can be already in use by a different Linux install, doesn't matter) I'll give you a different recipe that in fact allows you to move full linux installs if necessary (I do it all the time...).

---

