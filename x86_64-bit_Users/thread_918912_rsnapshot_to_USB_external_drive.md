---
title: "rsnapshot to USB external drive"
date: 2008-09-13
forum: x86 64-bit Users
---

### Post by raywood on 2008-09-13
I'm using Ubuntu Hardy 8.04 x64.  I have an ext3 partition I want to back up to an external USB hard drive (also ext3).  I am new to rsnapshot and am attempting to figure out the backup line to enter at the bottom of rsnapshot.conf.  I keep getting an error telling me, "Backup destination ... must be a local, relative path."  Here's what I've tried so far (with tabs instead of spaces in the appropriate places):

backup /media/CURRENT /media/OFFSITE/P4 CURRENT/

backup root@P4-VM:/media/CURRENT /media/OFFSITE/P4 CURRENT/

Both approaches gave the same error.  I think P4-VM is the name of my computer, but I'm not sure how to check that.

Thanks!

---

### Post by Stunts on 2008-09-13
I think the problem is in the path you typed. Linux supports spaces, but not like that on a terminal.
Try typing it this way:
backup /media/CURRENT "/media/OFFSITE/P4 CURRENT/"

Good luck

---

### Post by soxs on 2008-09-14
well either you use ```
"
``` as allready suggested or you escape them like that : ```
/home/ugly\ path
```

---

