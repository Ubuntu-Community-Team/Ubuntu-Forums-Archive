---
title: "right thing to upgrade to 64 bit ubuntu"
date: 2009-04-30
forum: x86 64-bit Users
---

### Post by ecolitan on 2009-04-30
I'm not sure if I'm doing the right thing in re-installing to the 64 bit Ubuntu, and was wondering if I can get some advise.

My processor according to /proc/cpuinfo is:
```
model name	: Intel(R) Core(TM)2 Duo CPU     T8100  @ 2.10GHz
```

Which from everything I can find is a 64bit processor,

And currently my ubuntu is:```
uname -m
i686

```

I also have 4GB of RAM but the os only sees 3GB of it, so i'm pretty sure I need to upgrade to 64bit.

Is there a way to upgrade to 64bit w/o having to reinstall all programs etc? What is the best way of doing it because I wanted to dl a cd iso but the only 64bit I can find says it's for amd cpu and I am intel - does it matter if I dl the link below for my cpu?

[http://de.archive.ubuntu.com/ubuntu-releases/jaunty/ubuntu-9.04-desktop-amd64.iso](http://de.archive.ubuntu.com/ubuntu-releases/jaunty/ubuntu-9.04-desktop-amd64.iso)

Many thanks in advance to anyone who can help!!

---

### Post by Grishka on 2009-04-30
I'm afraid you'll have to reinstall everything. amd64 is a generic standard for intel cpus as well, so the iso you've linked will work for you.

---

### Post by ecolitan on 2009-04-30
Thanks for the reply, sounds like my weekend is sewn up then...

---

### Post by arashiko28 on 2009-04-30
For your next installation I recommend you to make two partitions, one for / and one for /home, that way is a lot easier to reinstall. Still you'll have to reinstall all the software but the good news is that /home keeps the configuration files, so you won't have to twitch them that much the next time.

I had it that way since 8.10 and when reinstalled changed to 64 bit, it even booted up with my wallpaper and desktop decoration from old installation.

---

