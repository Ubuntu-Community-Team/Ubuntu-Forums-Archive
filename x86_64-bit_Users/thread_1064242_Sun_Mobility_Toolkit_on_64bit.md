---
title: "Sun Mobility Toolkit on 64bit"
date: 2009-02-08
forum: x86 64-bit Users
---

### Post by steveyeager on 2009-02-08
I am trying to develop some j2me apps on my ubuntu 8.10 x86-64bit system with no success.  I downloaded the Sun Mobility toolkit and both 64bit and 32bit 1.6 jdk/jre.  (By the way, I installed both Eclipse and Netbeans, each with the j2me tools installed but both have problems)  When I run the ktoolbar to develop an app, all seems to work initially.  It loads, it builds successfully.  However, running the newly built app results in an error:

java.lang.UnsatisfiedLinkError: /home/steve/WTK2.5.2/bin/sublime.so: /home/steve/WTK2.5.2/bin/sublime.so: wrong ELF class: ELFCLASS32 (Possible cause: architecture word width mismatch)

My research suggests that I am using a 64bit jdk/jre and that is ok until I run the emulator, which expects 32bit.  How can I test this using the installed 32bit jre?

---

### Post by scottuss on 2009-03-11
I have a similar issue (on Arch Linux 64 bit), slightly different error but down to the same cause I think. I'm playing around with a few solutions so I'll get back to you if I solve it. Meanwhile, any one else got any suggestions?

---

### Post by Plan B on 2009-10-19
Any updates?

---

### Post by Plan B on 2009-10-21
I fixed this by d/l the WTK from Sun Java site... [http://java.sun.com/javame/downloads/?intcmp=3161]("http://java.sun.com/javame/downloads/?intcmp=3161") and pointing the IDE to it.

---

### Post by awshanks on 2009-11-13
Im having this problem as well (Ubuntu 9.10). Installed Netbeans 6.7.1, than added mobility plugin.
Installed sun WTK 2.5.2.

I can write the mobile apps but emulater wont run due to:

 wrong ELF class: ELFCLASS32 (Possible cause: architecture word width mismatch)

I seen a possible solution [here]("http://blog.decabyte.it/?p=44") but its not in english.

Grr, i really want to get ubuntu to be my primary os, just need this niggle sorted.

---

### Post by awshanks on 2009-11-13
This fixes it for me:

[http://forums.sun.com/thread.jspa?messageID=9738850#9738850](http://forums.sun.com/thread.jspa?messageID=9738850#9738850)

The last post solves the issue, takes 2 minutes.

---

