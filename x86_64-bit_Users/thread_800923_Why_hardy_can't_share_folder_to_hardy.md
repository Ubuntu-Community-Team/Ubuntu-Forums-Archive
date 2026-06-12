---
title: "Why hardy can't share folder to hardy"
date: 2008-05-20
forum: x86 64-bit Users
---

### Post by nancom on 2008-05-20
I try to share folder in hardy by shares-admin.It's can browse via windows but can not mount in another hardy machine.I try to use 
"usershare owner only = False" in [global] section but it's didn't work.Any body help.

---

### Post by stephenb on 2008-05-21
It sounds like you are trying to access another Linux box with Samba. I think Samba is just for connecting Linux with Windows machines. I've never had any success with it connecting Linux to Linux.

For connecting Linux to Linux, read this: [http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

Once set up, you could put a line in your fstab file (which you should always backup first), something like this:

linux2:/home/user /media/laptop nfs rsize=8192,wsize=8192,timeo=14,intr 0 0

In this example, "linux2" is the name of your other Linux machine, "user" is your home directory name, and /media/laptop is what you'll be mounting--you just create a directory called laptop, or whatever, in the media directory. Also, instead of linux2, you could use the machines address, like 192.168.0.100, or whatever.

Then while linux2 is up run this command:

sudo mount -a

The mount should appear in the sidebar of any open window, or you could just go to /media/laptop and have a look.

Now, I should mention that this used to work for me, but in Hardy I just get this error:

mount.nfs: internal error

If you get the same thing, then you'll have to wait until the bug has been fixed. It's been reported.

---

### Post by nancom on 2008-05-24
Thanks you very much.By your solution means i need to mount drive.
In case, i need to browse only i need to wait bug fix.

---

