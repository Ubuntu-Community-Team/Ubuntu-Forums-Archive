---
title: "Random freeze on Ubuntu64-intrepid"
date: 2008-10-29
forum: x86 64-bit Users
---

### Post by mattva01 on 2008-10-29
I have a Core 2 Q9450 , 4 gigs of memory and a nvidia 650i mobo, with 2 8800 gt's ( its just a dell 630i)

I tried installing the release candidate,which installed fine. However within 10 minutes the system will hard lock. It seems to happen faster when I run firefox(its only frozen once when I have not run it) 

Logs in /var/log show nothing.

Any obvious fixes or a way to diagnose?

---

### Post by Thelasko on 2008-10-29
As far as obvious fixes, open the system monitor and watch your system resources as it crashes.  If that doesn't work, you might want to look at temperature issues.

When it seems like a machine has a built in timer controlling when it crashes, it's usually either a memory leak or heat.  The heat thing [applies to cars too.]("http://en.wikipedia.org/wiki/Ignition_coil")

---

### Post by mattva01 on 2008-10-29
What I meant to say is that it varies a large deal, but its never longer then 10-15 minutes.When I get back to that comp, I will check system resource use but I don't think its a memory leak. Performance doesn't degrade at all(in fact, it runs ridiculously fast)until the point of the freeze. Heat is possible as the fans seem louder then they are in Vista(which I normally use for gaming).

---

### Post by ptn107 on 2008-10-29
It sounds to me like a [physical] problem with the memory.  Reboot and press ESC when you see the grub menu.  Select 'Ubuntu 8.10, memtest86+' and see if it reports any problems.

---

### Post by L0rd_D4rk on 2008-10-30
> **mattva01 said:**
> I have a Core 2 Q9450 , 4 gigs of memory and a nvidia 650i mobo, with 2 8800 gt's ( its just a dell 630i)

I tried installing the release candidate,which installed fine. However within 10 minutes the system will hard lock. It seems to happen faster when I run firefox(its only frozen once when I have not run it) 

Logs in /var/log show nothing.

Any obvious fixes or a way to diagnose?


I have the same problem, also with x64, when ubuntu loads the NetworkManager runs at 100% and is constantly growing in memory usage. If I kill NetworkManager I still have some kind of memory leak, but I can't find it. My computer also locks when there is no more free memory (I have 2 gigs).

I have upgraded to 8.10 from 8.4

---

### Post by Thelasko on 2008-10-30
> **L0rd_D4rk said:**
> I have the same problem, also with x64, when ubuntu loads the NetworkManager runs at 100% and is constantly growing in memory usage. If I kill NetworkManager I still have some kind of memory leak, but I can't find it. My computer also locks when there is no more free memory (I have 2 gigs).

I have upgraded to 8.10 from 8.4

I think this is a different problem entirely.

---

### Post by vievie on 2008-10-30
Is this the super old and popular bug with 7.04?

Just google: freeze feisty fawn drives me insane

That's the longest thread I've seen in this forum, and the problem is not solved. It drives me away from Ubuntu.

Now the ghost is still there? Hope it's just for Halloween :)

---

