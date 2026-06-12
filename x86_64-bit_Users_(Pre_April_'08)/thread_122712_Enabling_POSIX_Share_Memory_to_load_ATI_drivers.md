---
title: "Enabling POSIX Share Memory to load ATI drivers"
date: 2006-01-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by kpurcell on 2006-01-28
I was on ATI's site and they said in order to load their drivers you have to have POSIX shared memory.  They give the following instructions:

[I][INDENT]The display driver requires POSIX Shared Memory to be enabled on the system in order to run these applications correctly. This feature should be enabled by default on most current Linux distributions, but may be disabled intentionally by some system administrators or not included in older distributions.

To enable POSIX Shared Memory on your system, perform the following as root:

1. Add the following line to /etc/fstab (if it isn't there already): tmpfs /dev/shm tmpfs defaults 0 0
2. Mount shared memory as follows: mount /dev/shm
3. Issue the following command to check that it mounted properly: mount | grep "shm"

If the mount was successful, then the following output (or similar) should appear:
tmpfs on /dev/shm type tmpfs (rw)[/INDENT][/I]

Well that is nice.  But how do I do the above.  I know, learn Linux.  But until I get it running i can't very well learn it that well.  So, how do I add the line in step one?  How do I mount the /dev/shm  -- in terminal?  I assume the third step is done in terminal.  But I am betting that the first step is the crucial one and I don't know how to do it.

---

### Post by slavik on 2006-01-28
here are the commands ...

sudo gedit /etc/fstab
#add the line
sudo mount /dev/shm
sudo mount | grep "shm"

That should work ... you need to type those commands in a terminal.

---

### Post by kpurcell on 2006-01-28
Well that was simple.  Thanks.  U the ?? Person!

---

### Post by slavik on 2006-01-28
huh?

---

