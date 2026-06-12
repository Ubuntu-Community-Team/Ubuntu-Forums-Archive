---
title: "Software with poor logging keeps crashing, are there any system logs"
date: 2009-05-15
forum: x86 64-bit Users
---

### Post by vectorm12 on 2009-05-15
I've got an issue where I have a software that whenever I allow the software to use multiple threads it starts to crash randomly. Now the software ontop of this offer close to no logging whatsoever which means I can't actually tell what's happening when the software is running multiple threads.

My question is, is there any log that might offer me some insight into what is going on or if there is some software I can install to try to figure out what's going on?

The system is running 64bit 9.04 desktop ubuntu

---

### Post by cariboo on 2009-05-15
All the logs are in /var/log, check /var/log/messages and /var/log/syslog.

---

### Post by vectorm12 on 2009-05-18
I've already had a look at them but they didn't really offer any real insight into what was going on. Is there any other way of logging what a software does besides these logs?

---

### Post by kelt65 on 2009-05-18
> **vectorm12 said:**
> I've already had a look at them but they didn't really offer any real insight into what was going on. Is there any other way of logging what a software does besides these logs?

Yes of course.

You can try ```
strace -f <command>
``` for starters, it will show you every system call the program and it's children make. Keep in mind it send output to STDERR not STDOUT so if you want to redirect to a file you will have to do like:

```
strace -f <command> > /tmp/strace.out 2>&1
```

It will produce a lot. You can limit what system calls you want to see with ```
-e (open|execve|read|whatever)
```

---

