---
title: "Kernel Update &amp; Hibernate in Hardy broken"
date: 2009-02-12
forum: x86 64-bit Users
---

### Post by Izkata on 2009-02-12
Up until the kernel update yesterday, I had no trouble with hibernate.  After the update, no matter which kernel I choose, hibernate will hang indefinitely before finishing - after it is done writing to the hard disk.

Suspend has been broken for as long as I've had it.  (It suspends, then fails to resume, but only some of the time.  Unless I've opened the Gimp, in which case it's guaranteed not to resume)

I have a Dell Studio 1535, Hardy Heron, 64-bit

Anyone have ideas?

---

### Post by Izkata on 2009-02-13
FALSE ALARM

About a week ago I installed Motion.  For some reason, upon bootup, it starts a daemon process recording.  I hadn't rebooted since then and had completely forgotten about it.

So I rebooted for the kernel update.  And the daemon process started.  Apparently hibernate doesn't work while the webcam is in use - I killed the process and now it works perfectly fine.

Suspend problem still seems to be there, though..

---

