---
title: "kde4 freezes after log in problem/upgrade 8.04-8.10"
date: 2008-11-07
forum: x86 64-bit Users
---

### Post by jdelgado on 2008-11-07
Hello,

I was working happily in 8.04 kubuntu and i decided to upgrade. I had 5 applications opened: Kate, openoffice, JabRef, firebird, firefox. In some of them I had files opened that were stored in a local drive, which has to be mounted. In the end of the upgrade, the system restarts, and I did not kill these applications. Now, when I am logging in, these application launch and try to access these files which are no longer available, because the drives where they are stored aren't mounted. Then Kate shows an error message, saying that she can't find the files.

Then it freezes. Or crashes I don't know the exact term. It doesn't work unless I force it to switch off, pressing the adequate button in my laptop.

I have a dell latitude D630.

thanks for your help in advance

delgado

---

### Post by dabl on 2008-11-07
> **jdelgado said:**
> 

I was working happily in 8.04 kubuntu and i decided to upgrade. I had 5 applications opened: Kate, openoffice, JabRef, firebird, firefox. In some of them I had files opened that were stored in a local drive, which has to be mounted.



Wow -- you really gave it the acid test, huh?  :lolflag:  Had you checked, you would have found about one zillion posts on this forum that start out "8.10 upgrade problems ....".

I would start by mounting the drives where your data are located.  That will involve editing /etc/fstab to create the device mounting lines.

Once you have the partitions/drives mounting correctly, you can move on to opening the configuration files in ~/.kde/share/config and fixing the auto-open issues, if that's what you want to do.

---

### Post by jdelgado on 2008-11-07
oh yeah :) i admit it was not the smartest thing to do... but isn't there a way of just not launching what i was working with before? i would like to know it, also in general, because that is something that annoys me when i launch kubuntu.

anyway i will try your suggestion, thanks

---

