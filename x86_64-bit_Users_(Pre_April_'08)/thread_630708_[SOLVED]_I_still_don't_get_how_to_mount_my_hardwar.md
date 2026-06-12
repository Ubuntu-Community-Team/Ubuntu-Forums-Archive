---
title: "[SOLVED] I still don't get how to mount my hardware."
date: 2007-12-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by ve3rpm on 2007-12-03
Okay, I've gone 100% Linux, and still need to use the odd bit of windows based software that I have.  A for instance would be, my software for writing a will.  When I go to run it, I get the message 

You are not privileged to mount the volume 'WILLS_KIT_051'.

I get the impression that I still don't know enough about mounting, and the difference between software and hardware.  I'm sure that there is a wiki or some such tutorial that I'm not aware of, but it's a bit of an irritation.  Perhaps someone can enlighten me.  thanx Dan

---

### Post by John.Michael.Kane on 2007-12-03
I take it you are trying to mount a windows partition.

[Mounting Windows Partitions in Ubuntu]("http://www.psychocats.net/ubuntu/mountwindows")

There is this post as well.
[Windows NTFS Partitions Read/write support made easy in Ubuntu ]("http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html")

However. even after mounting the partition you will still not be able to run windows based applications for that the use of wine or crossover office is most likely going to be needed.

---

### Post by ve3rpm on 2007-12-04
I don't want a windows partition, I just want to run the odd piece of software written for windows.

---

### Post by picopir8 on 2007-12-04
Software is not mounted, just storage devices.  That said, when you run your software, it may  be attempting to create a RAM drive and then execute out of RAM.  It is unable to mound the partition because it does not have superuser access.  Log in as root or use "sudo" when executing the program and I suspect it should have no problem mounting the partition.

---

### Post by John.Michael.Kane on 2007-12-04
> **ve3rpm said:**
> I don't want a windows partition, I just want to run the odd piece of software written for windows.

You can not run window based applications directly on Linux/Ubuntu. In order to run windows based programs you will need to use either wine or crossover office, and you will have to make sure that the application is supported.

[http://www.winehq.org/](http://www.winehq.org/)
[http://www.codeweavers.com/products/cxoffice/](http://www.codeweavers.com/products/cxoffice/)

or 

Find a suitable Linux replacement for the program in question.

---

### Post by ve3rpm on 2007-12-04
K, thanx!  I got it to run under gksudo nautilus.  It just suprised that when I tried to run it under wine, I was told not likely!  Thankfully there is still so much to learn... I'll never get bored.  thanx again.  Now maybe you can tell me how to get this thing to state solved.

---

### Post by John.Michael.Kane on 2007-12-04
> **ve3rpm said:**
> K, thanx!  I got it to run under gksudo nautilus.  It just suprised that when I tried to run it under wine, I was told not likely!  Thankfully there is still so much to learn... I'll never get bored.  thanx again.  Now maybe you can tell me how to get this thing to state solved.

You should be able to mark the thread solved by going to thread tools -> mark as solved. Another option is if you edit the OP there should be a option that says "mark as resolved."

---

