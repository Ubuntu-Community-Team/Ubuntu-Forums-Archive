---
title: "Broken samba mount stalls shutdown"
date: 2008-09-26
forum: x86 64-bit Users
---

### Post by parkejr on 2008-09-26
Hi,

I have a server system running hardy for x86, with a sempron processor, and a desktop system running a hardy for x86_64 with an AMD 64 bit processor..

Both systems are running samba, and both can mount partitions on the other. 

If I'm on my desktop (64 bit machine) and I shut it down while leaving the server on, everything is fine.

If I shut the server down first, then shutdown the desktop, then the system goes through most of the shutdown cycle, but then stalls with a flashing cursor - needs a power off to kill the system.

If I umount all the mounted samba partitions, shutdown the server, then shutdown the desktop, everything is ok.

So  I guess there is something in the shutdown sequence that tries to umount the samba partition, but the because the server is no longer there, it stalls?

Is this a bug? is it documented? how might I start to find out what the problem is? is there a log file that might record the error.


Thanks,

Jeff.

---

### Post by cariboo on 2008-09-26
How are you mounting your share? Do you use Nautilus, or you mounting the share manually? Are you mounting the share via fstab. I have the same problem, only when I mount the share manually. The work around is to umount the share before shutting down.

JIm

---

### Post by parkejr on 2008-09-28
Thanks,

yes I could umount the share before shutting down, either manually, or scripted, but I don't think I should have to - this problem hasn't occurred with previous versions of ubuntu, and doesn't occur with the x86 version of Hardy.

Jeff.

---

### Post by cariboo on 2008-09-28
I should note that my server runs 24/7 as it is not in the house and it is a pain to run out to the garage to start it up every time I need it. I forgot to umount the share I had mounted last night and my desktop shutdown properly with a pause of about 5 seconds while the share unmounted. I'm running Intrepid alpha 6.

Jim

---

### Post by parkejr on 2008-09-29
Jim,

I think I'll move to intrepid once 8.10 becomes available.

Regarding having the server in the garage - same setup as me. Wake on Lan is quite straightforward to set up if your hardware supports it, and if used with a dyndns account allows me to boot the server remotely from any computer with an internet connection.

Rgds,

Jeff.

---

### Post by Jive Turkey on 2008-09-29
I'm having a similar problem I have my samba share mounted through fstab and I'm hoping its just a matter of changing an option or two there, but if not there may be a way to tell ubuntu not to stall on the error with the shutdown or reboot command.  Also there may be a way to make a shutdown script that will unmount the shares on shutdown.  I'll let you know it I get one of those to work for me.

---

### Post by parkejr on 2008-10-03
any one know if this problem exists in 8.10?

---

### Post by rhcm123 on 2009-03-28
> **parkejr said:**
> any one know if this problem exists in 8.10?

this is probably a bit too late, but i was browsing this thread looking for a fix to this very problem, and yes, this bug exists in 8.10 and 9.04. strange, considering 2 symbolic links fixed the problem for me.

---

