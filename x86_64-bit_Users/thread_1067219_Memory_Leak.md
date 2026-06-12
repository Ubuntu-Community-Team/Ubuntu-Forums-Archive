---
title: "Memory Leak"
date: 2009-02-11
forum: x86 64-bit Users
---

### Post by TayfuN on 2009-02-11
How to view all processes ? With "Top" I can see only some of them and in summary whole memory(RAM) used less then 1.1GB. When I reboot machine All ~2GB is Free, after some time less and less... Any ideas ?

Ubuntu 8.04 all latest updates. Apache2 + MySQL. 3.8GHz 2GB Ram.

---

### Post by tripolitan on 2009-02-11
Why do you think there is a leak? What do you want to see exactly? "top" lists all running processes. What you described is normal. The "free" command will list RAM and swap space, the values will change as the system uses/releases memory. "nmap localhost" lists running servers, netstat for network statistics and there is also prstat or prstat -a -p <process id>

---

### Post by TayfuN on 2009-02-11
Where can lost 1GB ? And there is no prstat :)

---

### Post by movieman on 2009-02-11
Linux uses free memory to cache disk files, so after a while you'll see most of your RAM in use; as soon as a program needs it, the old files will be thrown out of the disk cache to make space.

BTW, when running top you can press M to list programs by memory usage rather than activity.

---

### Post by lensman3 on 2009-02-11
What does the "free" command say?

---

### Post by u-slayer on 2009-02-11
> **lensman3 said:**
> What does the "free" command say?

That's irrelevant. Instead type in $apt-get moo and tell me what it says.

---

### Post by tripolitan on 2009-02-12
> **TayfuN said:**
> Where can lost 1GB ? And there is no prstat :)

1 Gig of what? RAM or swap or diskspace?

---

### Post by OrangeCrate on 2009-02-12
> **TayfuN said:**
> How to view all processes ? With "Top" I can see only some of them and in summary whole memory(RAM) used less then 1.1GB. **When I reboot machine All ~2GB is Free, after some time less and less...** Any ideas ?

Ubuntu 8.04 all latest updates. Apache2 + MySQL. 3.8GHz 2GB Ram.

As has been said by others, it's more than likely disk caching. You can read how it works here:

[http://forums.gentoo.org/viewtopic-t-175419-postdays-0-postorder-asc-start-0.html?sid=619cda6e4dae2a0651c474f9f5e4dfcf](http://forums.gentoo.org/viewtopic-t-175419-postdays-0-postorder-asc-start-0.html?sid=619cda6e4dae2a0651c474f9f5e4dfcf)

---

