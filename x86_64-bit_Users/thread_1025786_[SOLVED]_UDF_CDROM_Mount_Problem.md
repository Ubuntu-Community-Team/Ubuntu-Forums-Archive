---
title: "[SOLVED] UDF CDROM Mount Problem"
date: 2008-12-30
forum: x86 64-bit Users
---

### Post by todd1814 on 2008-12-30
I'm running 64 bit 8.10, kernel 2.6.27-9.generic

I just upgraded from 32 bit 8.10, kernel 2.6.27-9.generic

When I insert a CDROM, it gets mounted but I don't have permission to view its contents.  Before mounting:

# ls -l /media
lrwxrwxrwx 1 root root    6 2008-12-26 14:26 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2008-12-26 14:26 cdrom0

# grep cdrom /etc/fstab
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0 0

# mount /media/cdrom0
mount: block device /dev/scd0 is write-protected, mounting read-only

# ls -l /media
lrwxrwxrwx 1 root       root          6 2008-12-26 14:26 cdrom -> cdrom0
dr--r--r-- 6 4294967295 4294967295  376 2004-04-09 16:16 cdrom0

---------------------------------------------------------------------

Notice the UID and GID?  They happen to be the max size of a 32 bit integer.  I don't know where these are coming from.  As root I can look at the contents of my CD.  I'm unable to view it as a user (especially in Nautilus) because I don't have permission.

# ls /media/cdrom0
ARLO Full Import  regularexpressions
Compact .Net      Visual Studio 2003 Enterprise Architect

----------------------------------------------------------------------

Here's the interesting part.  If I remove "udf" from the filesystem options in /etc/fstab, I can mount the CDROM with correct permissions:

# umount /media/cdrom0
# vi /etc/fstab    (Remove "udf" from mount option)
# grep cdrom /etc/fstab
/dev/scd0       /media/cdrom0   iso9660 user,noauto,exec,utf8 0  0
# mount /media/cdrom0
mount: block device /dev/scd0 is write-protected, mounting read-only
# ls -l /media
lrwxrwxrwx 1 root root    6 2008-12-26 14:26 cdrom -> cdrom0
dr-xr-xr-x 1 root root 2048 2004-04-09 05:16 cdrom0

# ls /media/cdrom0
arlofu~2   compac~1   regula~1  visual~2

----------------------------------------------------------------------

After removing UDF, I can see the CDROM as a user and in Nautilus.  The permissions look fine (root:root) My gripe is that I now have modified file/path names.

Does anyone know what's happening here or how to correct it?

TIA!

---

### Post by dcstar on 2008-12-30
> **todd1814 said:**
> 
......
After removing UDF, I can see the CDROM as a user and in Nautilus.  The permissions look fine (root:root) My gripe is that I now have modified file/path names.

Does anyone know what's happening here or how to correct it?

TIA!

You might try adding the "ro" option to the fstab line - there might be something in the UDF mount code that needs something like that.

---

### Post by todd1814 on 2008-12-30
After some more research, I found this bug report:

[https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/10550](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/10550)

This appears to be a very old issue that I've never come across.  Mounting the filesystem as iso9660 doesn't observe file permissions.  Mounting as UDF does.  Unfortunately, many disk burning applications leave -1 in the uid and gid permissions of their udf filesystems.  This causes a permission problem in Linux.

The only way I can read CD's as a user is by mounting UDF filesystems on cdrom as iso9660.  It would be nicer if Ubuntu disregarded the permissions except when copying.

---

