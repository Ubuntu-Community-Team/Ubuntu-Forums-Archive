---
title: "[SOLVED] Failed rdiff-backup, Function not implented?"
date: 2008-05-06
forum: x86 64-bit Users
---

### Post by javagamer on 2008-05-06
Hi,
   I've recently attempted to start a backup system using rdiff-backup.  I plan on using it to mirror my boot drive over to my secondary drive.  I wrote this script to do it:
```
#! /bin/bash
sudo mount -t ext3 /dev/sdb1 /mnt/backup
sudo rdiff-backup --exclude /tmp --exclude /mnt --exclude /media --exclude /proc --exclude /dev/sdb / /mnt/backup/backupdata/
sudo umount /dev/sdb1
```
However, whenever I try to run it, I get these errors
```

There were a lot more update errors, but I only included a few of the most recent ones before it crashed
UpdateError sys/power/disk Updated mirror temp file /mnt/backup/backupdata/sys/power/rdiff-backup.tmp.73421 does not match source
UpdateError sys/power/image_size Updated mirror temp file /mnt/backup/backupdata/sys/power/rdiff-backup.tmp.73422 does not match source
UpdateError sys/power/pm_trace Updated mirror temp file /mnt/backup/backupdata/sys/power/rdiff-backup.tmp.73423 does not match source
UpdateError sys/power/resume Updated mirror temp file /mnt/backup/backupdata/sys/power/rdiff-backup.tmp.73424 does not match source
UpdateError sys/power/state Updated mirror temp file /mnt/backup/backupdata/sys/power/rdiff-backup.tmp.73425 does not match source
UpdateError sys/slab/:0000008/aliases Updated mirror temp file /mnt/backup/backupdata/sys/slab/:0000008/rdiff-backup.tmp.73426 does not match source
UpdateError sys/slab/:0000008/align Updated mirror temp file /mnt/backup/backupdata/sys/slab/:0000008/rdiff-backup.tmp.73427 does not match source
Exception '[Errno 38] Function not implemented' raised of class '<type 'exceptions.IOError'>':
  File "/var/lib/python-support/python2.5/rdiff_backup/robust.py", line 32, in check_common_error
    try: return function(*args)
  File "/var/lib/python-support/python2.5/rdiff_backup/rpath.py", line 101, in copy
    if rpin.isreg(): return copy_reg_file(rpin, rpout, compress)
  File "/var/lib/python-support/python2.5/rdiff_backup/rpath.py", line 129, in copy_reg_file
    return rpout.write_from_fileobj(rpin.open("rb"), compress = compress)
  File "/var/lib/python-support/python2.5/rdiff_backup/rpath.py", line 1078, in write_from_fileobj
    copyfileobj(fp, outfp)
  File "/var/lib/python-support/python2.5/rdiff_backup/rpath.py", line 58, in copyfileobj
    inbuf = inputfp.read(blocksize)
  File "/var/lib/python-support/python2.5/rdiff_backup/rpath.py", line 1296, in read
    def read(self, length = -1): return self.file.read(length)
  File "/var/lib/python-support/python2.5/rdiff_backup/hash.py", line 42, in read
    buf = self.fileobj.read(length)

Exception '[Errno 38] Function not implemented' raised of class '<type 'exceptions.IOError'>':
  File "/var/lib/python-support/python2.5/rdiff_backup/Main.py", line 302, in error_check_Main
    try: Main(arglist)
  File "/var/lib/python-support/python2.5/rdiff_backup/Main.py", line 322, in Main
    take_action(rps)
  File "/var/lib/python-support/python2.5/rdiff_backup/Main.py", line 278, in take_action
    elif action == "backup": Backup(rps[0], rps[1])
  File "/var/lib/python-support/python2.5/rdiff_backup/Main.py", line 344, in Backup
    backup.Mirror(rpin, rpout)
  File "/var/lib/python-support/python2.5/rdiff_backup/backup.py", line 38, in Mirror
    DestS.patch(dest_rpath, source_diffiter)
  File "/var/lib/python-support/python2.5/rdiff_backup/backup.py", line 225, in patch
    ITR(diff.index, diff)
  File "/var/lib/python-support/python2.5/rdiff_backup/rorpiter.py", line 281, in __call__
    last_branch.fast_process(*args)
  File "/var/lib/python-support/python2.5/rdiff_backup/backup.py", line 522, in fast_process
    if self.patch_to_temp(mirror_rp, diff_rorp, tf):
  File "/var/lib/python-support/python2.5/rdiff_backup/backup.py", line 543, in patch_to_temp
    result = self.patch_snapshot_to_temp(diff_rorp, new)
  File "/var/lib/python-support/python2.5/rdiff_backup/backup.py", line 572, in patch_snapshot_to_temp
    (diff_rorp, new))
  File "/var/lib/python-support/python2.5/rdiff_backup/robust.py", line 32, in check_common_error
    try: return function(*args)
  File "/var/lib/python-support/python2.5/rdiff_backup/rpath.py", line 101, in copy
    if rpin.isreg(): return copy_reg_file(rpin, rpout, compress)
  File "/var/lib/python-support/python2.5/rdiff_backup/rpath.py", line 129, in copy_reg_file
    return rpout.write_from_fileobj(rpin.open("rb"), compress = compress)
  File "/var/lib/python-support/python2.5/rdiff_backup/rpath.py", line 1078, in write_from_fileobj
    copyfileobj(fp, outfp)
  File "/var/lib/python-support/python2.5/rdiff_backup/rpath.py", line 58, in copyfileobj
    inbuf = inputfp.read(blocksize)
  File "/var/lib/python-support/python2.5/rdiff_backup/rpath.py", line 1296, in read
    def read(self, length = -1): return self.file.read(length)
  File "/var/lib/python-support/python2.5/rdiff_backup/hash.py", line 42, in read
    buf = self.fileobj.read(length)

Traceback (most recent call last):
  File "/usr/bin/rdiff-backup", line 23, in <module>
    rdiff_backup.Main.error_check_Main(sys.argv[1:])
  File "/var/lib/python-support/python2.5/rdiff_backup/Main.py", line 302, in error_check_Main
    try: Main(arglist)
  File "/var/lib/python-support/python2.5/rdiff_backup/Main.py", line 322, in Main
    take_action(rps)
  File "/var/lib/python-support/python2.5/rdiff_backup/Main.py", line 278, in take_action
    elif action == "backup": Backup(rps[0], rps[1])
  File "/var/lib/python-support/python2.5/rdiff_backup/Main.py", line 344, in Backup
    backup.Mirror(rpin, rpout)
  File "/var/lib/python-support/python2.5/rdiff_backup/backup.py", line 38, in Mirror
    DestS.patch(dest_rpath, source_diffiter)
  File "/var/lib/python-support/python2.5/rdiff_backup/backup.py", line 225, in patch
    ITR(diff.index, diff)
  File "/var/lib/python-support/python2.5/rdiff_backup/rorpiter.py", line 281, in __call__
    last_branch.fast_process(*args)
  File "/var/lib/python-support/python2.5/rdiff_backup/backup.py", line 522, in fast_process
    if self.patch_to_temp(mirror_rp, diff_rorp, tf):
  File "/var/lib/python-support/python2.5/rdiff_backup/backup.py", line 543, in patch_to_temp
    result = self.patch_snapshot_to_temp(diff_rorp, new)
  File "/var/lib/python-support/python2.5/rdiff_backup/backup.py", line 572, in patch_snapshot_to_temp
    (diff_rorp, new))
  File "/var/lib/python-support/python2.5/rdiff_backup/robust.py", line 32, in check_common_error
    try: return function(*args)
  File "/var/lib/python-support/python2.5/rdiff_backup/rpath.py", line 101, in copy
    if rpin.isreg(): return copy_reg_file(rpin, rpout, compress)
  File "/var/lib/python-support/python2.5/rdiff_backup/rpath.py", line 129, in copy_reg_file
    return rpout.write_from_fileobj(rpin.open("rb"), compress = compress)
  File "/var/lib/python-support/python2.5/rdiff_backup/rpath.py", line 1078, in write_from_fileobj
    copyfileobj(fp, outfp)
  File "/var/lib/python-support/python2.5/rdiff_backup/rpath.py", line 58, in copyfileobj
    inbuf = inputfp.read(blocksize)
  File "/var/lib/python-support/python2.5/rdiff_backup/rpath.py", line 1296, in read
    def read(self, length = -1): return self.file.read(length)
  File "/var/lib/python-support/python2.5/rdiff_backup/hash.py", line 42, in read
    buf = self.fileobj.read(length)
IOError: [Errno 38] Function not implemented
```
Does anyone know what's wrong?  Could it be a 64-bit issue or just an rdiff-backup issue?  Did I write my script wrong?
Thanks in advance.

---

### Post by javagamer on 2008-05-27
*bump* Anyone know anything that might help?

---

### Post by pixel :-) on 2008-05-27
"more update errors" What kind of errors where they?

Try a simple backup,some files in a clean directory.Without interupting it.To see if goes smouthly

**about the script it self**
"--exclude /dev/sdb" /dev/sdb is a device,change it too"--exclude /dev"
 it's better,most /dev content are not real files.

add "--exclude /sys" this content is created at boot time,it's at this point that rdiff crashed,i read somewhere that a bug cause aplication to crash whille reading sys,bug in the kernel.You where attempting to wright in it O_O,very bad idea.On top of it it's read only,this particular directory.Don't dare touch that directory, sys like in system.

Various files are read only,this should account for some of the errors.

"sudo mount -t ext3 /dev/sdb1 /mnt/backup" you can add a line to your fstab and simply do "mount /dev/sdb1"
Try the gui tool first,system something.Or add in /etc/fstab
/dev/sdb1 /mnt/backup ext3 user,relatime,atime,auto,rw,dev,exec,suid

Now retry a backup,maybe exclude home, if it's to big,and post what errors you keep getting.I never bother with backing up everything,i just backup home,that is on a different partition,for the rest i just reinstall and run a big apt-get command to get back where i was.

---

### Post by javagamer on 2008-05-28
Thanks for all your help pixel :-)!
Everything seemed to work except for one error message which seems minor
```
ListError home/javagamer/.gtk-bookmarks/.gvfs [Errno 13] Permission denied: '/home/javagamer/.gvfs'
```
Should I be worried about that directory? It doesn't sound too important.
BTW, I'm now using a daily root crontab to run this, do you see a problem with this command
```
1 3 * * * /usr/bin/backup >> /home/javagamer/backup.log 2>&1
```
Thanks again!

---

### Post by pixel :-) on 2008-05-29
/home/javagamer/.gtk-bookmarks/.gvfs
it's part of gnome virtual file system,**i'm in kde**,i don't have this file.Ask in the desktops thread for details,i would say it's minor.

never used crontab ,or even cron,but
it seems ok

**I assume you want to run all the procedure under root.The line for fstab that i gave ,the "user" option allows any user to mount it,i think you prefer the "nouser" option,only root mounts/unmounts.**

the mounting part of your initial script is ok.

---

### Post by meonkeys on 2008-09-14
> **javagamer said:**
> Thanks for all your help pixel :-)!
Everything seemed to work except for one error message which seems minor
```
ListError home/javagamer/.gtk-bookmarks/.gvfs [Errno 13] Permission denied: '/home/javagamer/.gvfs'
```
Should I be worried about that directory? It doesn't sound too important.


Here's a hackish way to eliminate the permission denied error. When performing a backup, temporarily disable the fuse mountpoint.

```

# disable fuse mountpoints--these confuse rdiff-backup
sudo -u someuser fusermount -u /home/someuser/.gvfs

# ...run rdiff-backup...

# gvfs-fuse-daemon wants to read the current working directory for
# some reason, so cwd cannot be (for instance) /root
cd /tmp

# reenable fuse mountpoints
sudo -u someuser /usr/lib/gvfs/gvfs-fuse-daemon /home/someuser/.gvfs

```

[Here is a short list of issues tracking the cause of why the root user cannot access .gvfs directories]("http://ubuntuforums.org/showthread.php?t=781805#post5136392").

---

