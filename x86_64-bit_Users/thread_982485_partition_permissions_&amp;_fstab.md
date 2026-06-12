---
title: "partition permissions &amp; fstab"
date: 2008-11-14
forum: x86 64-bit Users
---

### Post by Grant A. on 2008-11-14
is it safe/secure to just use this line in fstab:

```

# docs
/dev/sda5 /home/grant/docs vfat user,rw 0 1

```

or will it open my partition up to attacks?

---

### Post by dcstar on 2008-11-14
> **Grant A. said:**
> is it safe/secure to just use this line in fstab:

```

# docs
/dev/sda5 /home/grant/docs vfat user,rw 0 1

```

or will it open my partition up to attacks?

FAT partitions have no ACL security anyway, so I have no idea whatsoever what "attacks" you mean, or why you are asking this in a 64bit forum.

---

### Post by cariboo on 2008-11-15
If you are worried about security have a look at this:

[http://ubuntuforums.org/showthread.php?t=919472](http://ubuntuforums.org/showthread.php?t=919472)

and this:

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

Jim

---

