---
title: "My experiences as a first-time Ubuntu user"
date: 2005-06-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by quickone on 2005-06-13
I thought I would put down my experiences with installing Ubuntu for the first time.

To start, I will list my specs:
1 IDE ATA 66 drive - 120GB.  Partitions: 0 - Win XP, 1 - Win 2K3, 2 - / (ext3), 3 - Swap, 4 - /home (ext3)

Crappy little audio card (ESS 1969 Solo?)

nVidia GeForce 4 ti 4200

K8S mobo

Athlon 64 3000

1 GB DDR 266

52X CDRW drive - Sony?

Linksys Wireless USB - 11b

My hardware is pretty standard stuff, nothing particularly out of the ordinary.

My installation of Ubuntu went well, it detected everything except my Linksys USB network connection.  No big surprise there, it's a pain to get working in Windows, much less Linux.  However, Mandrake 10.1 detected and used it perfectly the first time, so I had some hope it might work.

I couldn't get that to work, so I gave up and just installed an old Kingston 10 ethernet card - it installed and works fine.

Then the problems started:
1) Grub was not configured to allow for dual-booting into Windows by default.  Not that it was hard to make it do that, but for an end user who doesn't know Linux at all, it would have been next to impossible to figure out.
2) I cannot for the life of me get cdrecord to work properly with my CDRW.  It complains about the kernel being the wrong kind - i.e. AMD64 and dies.  I'm going to post a bug on it later.  I suspect this is mostly due to not having a good version of it for this kernel.
3) Why is it SO difficult to get Ubuntu to kill X?  Sometimes I want to not have X running!  There seems to be a problem with changing the runlevel too.  I've seen some posts about it, but it still doesn't quite make sense to me.
4) Aptitude, Synaptic package manager - man, these are NOT easy to use.  This being my first time, it took me hours to successfully install some libraries I was missing and get it working.  I believe that the system is a pretty good one, but it still seems to be non user-friendly to me.  
5) I cannot get some software that I would really like to use installed on my system.  A lot of it has to do with the fact that some of the libraries that are needed are not yet ported to AMD64.  Until that happens, I would not recommend Ubuntu AMD64 to anyone who is not willing to run on the bleeding edge.  

Overall my experiece has been good!  I just started using it and already like it better than Mandrake (bloated).  The fact that I can actually get the stupid nvidia-glx library running so easily was a BIG plus.  Nothing I tried in Mandrake could get it working.  

I look forward to doing testing and bug reporting on this system.  

My only major disappointment is that I still have not found a truly grandma friendly distro of Linux.  I had hoped Ubuntu might be close, but it's still a ways off.  Of course, I am basing this on running the latest version with a new processor that is not fully supported even by Windows yet.

No need to reply to this post to help me with my problems, I'll address those separately, I just wanted to point them out.

---

### Post by Seti on 2005-06-13
So you were using the AMD64 version of Hoary? Someone I know is getting an AMD64 soon, but I think I'll just put regular Hoary on it for them until some future time when there is a bit more software support for 64bit CPU architecture.

---

### Post by Plankman on 2005-07-12
[QUOTE=Seti]So you were using the AMD64 version of Hoary? Someone I know is getting an AMD64 soon, but I think I'll just put regular Hoary on it for them until some future time when there is a bit more software support for 64bit CPU architecture.[/QUOTE]
 I've just installed my first copy of Ubuntu on my AMD Athlon 64 3000+ machine with no hassles. Sure, some libraries aren't ready for 64bit, but on the whole it's quite a good system and more stable than other 32bit systems I've used before

---

