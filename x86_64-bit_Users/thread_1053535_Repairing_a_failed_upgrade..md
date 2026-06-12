---
title: "Repairing a failed upgrade."
date: 2009-01-28
forum: x86 64-bit Users
---

### Post by TimothyLuke on 2009-01-28
Hi All,

I just recently bit the bullet and upgraded from 8.04 to 8.10.  I have an interesting quirk from my motherboard.  It has an onboard Intel 965G chip that when ever it is initialised the machine hangs on a black screen requiring a hard reboot.  Previously intel_agp was blacklisted and that solved my problem. 

During the upgrade process, this driver was removed from the blacklist (User error - I approved the change without thinking).  The next thing that occured was that the driver was probed and the machine blackscreened.

I have managed to get it back up and running and have my gnome desktop back, well sort of.  I get to a point now where I need to run 'dpkg --configure -a'.  This fails due to dependency issues and i get stuck.  Short of wiping the entire install and starting again are there any processes for working through this?

---

### Post by cariboo on 2009-01-28
Have you tried:

```
sudo spt-get install -f
```

that should fix brken dependencies. If not use the synaptic broken packages filter, and completely remove the broken packages and start all over again.

Jim

---

### Post by TimothyLuke on 2009-01-29
That didnt solve the problem but it did point me in the right direction - thank you.  I had conflicting versions of CUPS and xmms2 that i had to remove and then it all sorted itself out.  I then had no sound but recovered that when I installed pulse and had to reinstall CUPS to get printing to work.

---

