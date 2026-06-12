---
title: "[SOLVED] 8.04 upgrade: libmono-corlib1.0-cil broken"
date: 2008-08-27
forum: x86 64-bit Users
---

### Post by the_weekend on 2008-08-27
I recently upgraded to 8.04 and had problems with the libmono-corlib1.0-cil package, which is apparently broken. Everything seems to work fine so I just ignored it...until I realized flash is broken. As flash-nonfree seems dependent upon this package, I thought I'd seek help.

```
E: /var/cache/apt/archives/libmono-corlib1.0-cil_1.2.6+dfsg-6ubuntu3_all.deb: short read in buffer_copy (backend dpkg-deb during `./usr/lib/mono/1.0/mscorlib.dll')

```

Any ideas?

---

### Post by prshah on 2008-08-27
> **the_weekend said:**
> 
```
<snip>: short read in buffer_copy (backend dpkg-deb <snip>)

```


Looks like you may need to run fsck.

Check: Try to copy the libmono* file to your home directory to see if can actually be sucessfully read```
cp /var/cache/apt/archives/libmono-corlib1.0-cil_1.2.6+dfsg-6ubuntu3_all.deb ~
```

It should give an error; if it doesn't I'm probably not on the right track.

If it gives an error, you may have logical/physical damage to  your hard disk; to resolve, boot with a live CD, open a terminal (Applications-Accessories-Terminal) and unmount and check your linux partitions with ```
sudo unmount /dev/sda2
sudo fsck -a /dev/sda2
``` replace /dev/sda2 with your actual partition device.

Remember, you need to fsck only if the first copy command fails.

---

### Post by the_weekend on 2008-08-27
Your advice was kinda close, the file was corrupted, so I deleted the file and tried again. Fsck wasn't necessary though. Thanks!

---

### Post by prshah on 2008-08-28
> **the_weekend said:**
> Your advice was kinda close, the file was corrupted, so I deleted the file and tried again. Fsck wasn't necessary though. Thanks!

OK! Maybe now you should mark this thread "solved": Near the upper right hand side of the page, click on "Thread Tools"-"Mark thread as solved"

---

