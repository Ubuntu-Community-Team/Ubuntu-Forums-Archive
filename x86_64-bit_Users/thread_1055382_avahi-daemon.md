---
title: "avahi-daemon"
date: 2009-01-30
forum: x86 64-bit Users
---

### Post by zika on 2009-01-30
is this a problem ```
dmesg gives:
[   16.111365] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
```on a 64-bit Phenom-X3-9450 machine with the latest version of avahi-daemon...?

---

### Post by cariboo on 2009-01-30
There has been a [bug]("http://bugs.launchpad.net/ubuntu/+source/avahi/+bug/248577") reported about that problem, it has been sent upstream.

Jim

---

### Post by zika on 2009-01-31
> **cariboo907 said:**
> There has been a [bug]("http://bugs.launchpad.net/ubuntu/+source/avahi/+bug/248577") reported about that problem, it has been sent upstream.
Jim
I've read that bug report and must admit that I do not comprehend what is the effect of that bug on my machine and when it is going to be solved.

---

### Post by thriftee on 2009-01-31
I have the same error.  I wonder if that has something to do with why X won't start automatically on mine?

---

### Post by Yellow Pasque on 2009-01-31
> **thriftee said:**
> I have the same error.  I wonder if that has something to do with why X won't start automatically on mine?
Probably not. I see this error regularly on Debian-based distros I use and none of them have problems starting X.

---

