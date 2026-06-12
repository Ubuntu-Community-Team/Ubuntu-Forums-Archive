---
title: "fb_lock_mgr segfault on AMD64"
date: 2007-07-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by epix_ian on 2007-07-04
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/firebird2/+bug/123943](https://bugs.launchpad.net/ubuntu/+source/firebird2/+bug/123943) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				We are using firebird2 [1.5.3.4870 Firebird 1.5] on Ubuntu 7.04 and an AMD Athlon(tm) 64 X2 Dual Core Processor 5600+.

Every 5 minutes we get an entry in /var/log/messages like the following:

"fb_lock_mgr[4635]: segfault at 00000000000034e2 rip 0000000000407430 rsp 00007fffd5807000 error 4"

I have posted this to a firebird-support forum and they have suggested that I posted the problem to an Ubuntu forum - mostly because in the Ubuntu notes for the package it says:

* For classic, fb_lock_mgr, the lock manager, is built with
-DTERMINATE_IDLE_LOCK_MANAGER option to avoid leaving stale processes
on build machines. This option causes fb_lock_mgr to terminate after
5 minutes of inactivity.

-which seems to fit with the 5 minute segfaults. 

I [maybe erroneously] have posted this as a bug against the firebird2 package - but thinking about it maybe I should have posted here first before unilaterally declaring it a bug.

Any help would be appreciated, and if I can provide more information then please ask.

Thanks

Ian

---

### Post by epix_ian on 2007-07-05
If this isn't the correct forum to post this sort of problem to, please could you point me to the correct one.

Thanks

Ian

---

### Post by Cappy on 2007-07-05
What have you tried? 
It looks like there may be a lock file for firebird in your filesystem that is making the lock manager mess up. Unfortunately, I don't know where the firebird's lock file (or any lock file) would be located so you can delete it.

Is this causing firebird to crash for you or just give these messages?

---

### Post by epix_ian on 2007-07-06
fb_lock_mgr is used [by my understanding] to allow signals to be passed between different process groups, and not as it sounds, to directly manage locks :o

There is no "officially" supported 64 bit build of firebird 1.5.3, which could be significant.

However, there is a 64 port from Ubuntu, which has lead me to post the problem here to see if someone else recognizes the problem, or if someone else can help. I am also about to post back to firebird-support to see of they have any other ideas.

The release notes for the Ubuntu 64 bit version of firebird mention that fb_lock_mgr has been changed to terminate after 5 minutes. What we are seeing is a regular 5 minute segfault, which we thought could be related. After a number of segfaults we end up unable to make further connections to any databases, with a variety of error messages including:

isql: error while loading shared libraries: libfbembed.so.1: cannot open shared object file: No such file or directory

and

operating system directive open failed
-Permission denied

A reboot "fixes" this, but we still get the segfaults like clockwork once the box is back up.

We are trying the official firebird 32 bit release, but dont know if this will work. After that we are going to try Suse plus our own built 64 bit firebird [we don't seem to be able to build our own from firebird source on Ubuntu 7.04 for some reason...]

Failing all that we might cry a little :(

I have a feeling that I need to try and get in contact with the maintainer for Ubuntu's version as this sounds like a very specific problem we are having.

Thanks

Ian

---

### Post by Cappy on 2007-07-06
```

sudo apt-get install libfbembed1

```
which says it is included with the firebird package so that is weird.
Maybe
```

sudo apt-get install libfbclient2

```
instead.

Maybe this page too:
[http://www.firebirdsql.org/index.php?op=doc&sub=contrib&id=connect_to_linux](http://www.firebirdsql.org/index.php?op=doc&sub=contrib&id=connect_to_linux)

Since ubuntu's firebird2 is actually 1.5 something you may just want to install the actual AMD64 package from here:
[http://www.firebirdsql.org/index.php?op=files&id=engine_201](http://www.firebirdsql.org/index.php?op=files&id=engine_201)

Quick start guide:
[http://www.firebirdsql.org/index.php?op=guide](http://www.firebirdsql.org/index.php?op=guide)

---

### Post by epix_ian on 2007-07-09
Thanks for the fbclient suggestion - however the installation is all working fine most of the time and not raising errors [except the regular as clockwork segfault] so its not that.

We think we have "fixed" the problem. I did an "apt-get source firebird*", and then built it from there and we have been running since Friday with no segfaults and no strange problems.

I'm not really happy that this is a fix as building should give me just the same as the binary download. One suggestion here is that we have updated some other library that is causing the problem, and the fresh build has smoothed over this...

Who knows :confused:

Thanks,

Ian

---

