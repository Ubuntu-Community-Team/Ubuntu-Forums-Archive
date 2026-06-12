---
title: "passwd does not work"
date: 2009-02-02
forum: x86 64-bit Users
---

### Post by Kilbasar on 2009-02-02
Hi all. I've been having a problem on my Intrepid x86_64 box. Ever since I first installed it, I have been unable to change my account password at the command line. When I run the 'passwd' command, it asks me for my current password, but never asks me for a new one:

$ passwd
Changing password for kilbasar.
(current) UNIX password: 
passwd: password updated successfully


The same thing occurs if I try 'sudo passwd kilbasar'. I am able to change passwords using the GUI "Users and Groups" tool, but I prefer to do things at the command line, so what gives? Thanks!

---

### Post by deepclutch on 2009-02-02
your installation is corrupted?you must reinstall sudo ,passwd packages.
why not use a livecd and mount your Linux partition and chroot ,reinstall those packages mentioned above.atleast adding a suid bit to /usr/bin/sudo and /usr/bin/sudoedit. 

google for chrooting and mounting partition.

---

### Post by cariboo on 2009-02-02
Have you tried:

```
sudo passwd kilbasar
```

to change your passwd?

Jim

---

