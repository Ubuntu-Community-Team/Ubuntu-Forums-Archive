---
title: "intel dual core T9300 -&gt; 64 bit version"
date: 2008-05-22
forum: x86 64-bit Users
---

### Post by JanRa on 2008-05-22
Hi all,

I just bought a new laptop with an intel dual core T9300 processor. I can't find references whether this is a 32 or 64 bit processor. I would like to install ubuntu and hence don't know which version to install.

Any help is much appreciated.

Jan

---

### Post by carlolovearianne on 2008-05-22
Use the 32 bit just to be on the safe side :)

---

### Post by prshah on 2008-05-22
> **JanRa said:**
> 
I just bought a new laptop with an intel dual core T9300 processor. I can't find references whether this is a 32 or 64 bit processor. I would like to install ubuntu and hence don't know which version to install.

Yes you can run 64bit, or 32 bit as per your choice.

This is a Core 2 Duo processor, not a simple "dual core" processor. All core 2 processors are EM64T capable, which means that they can run either 32bit or 64bit.

As the earlier poster has noted, you can use 32 bit as well; and from reading forums posts, it seems that 64bit is a little iffy. I have not tried 64 bit and my advice to _not_ use 64 bit is unqualified. 

If you dont have a particular reason for 64 bit (eg, number crunching, video editing, audio analysis) you can stick with 32bit for a (relatively) trouble-free experience.

If you still have a doubt about whether or not you can run 64 bit, get the amd64 (which is also used for Intel x86_64) live cd and if it boots up, you are OK for 64 bit, otherwise you will get an error message about the kernel not being suitable for this architecture.

---

### Post by jespdj on 2008-05-22
64-bit Ubuntu 8.04 works great on my Dell XPS M1530 with T9300 processor.

Read the sticky post at the top of the forum to learn more about 64-bit Ubuntu.

In my opinion, there's no reason to use the 32-bit version if you have 64-bit capable hardware.

---

### Post by NightwishFan on 2008-05-22
Always use 64bit. The processor was designed to use that why waste it.

---

### Post by prshah on 2008-05-22
> **jespdj said:**
> 
In my opinion, there's no reason to use the 32-bit version if you have 64-bit capable hardware.

> **NightwishFan said:**
> Always use 64bit. The processor was designed to use that why waste it.

I humbly withdraw my objections to 64 bit.

---

### Post by NightwishFan on 2008-05-22
It is fine to be wary of it. Personally it works just fine for me, and seems much faster. It may not work like so for everyone but it is improving. Also 32bit software can run on 64bit os.

---

### Post by felker2 on 2008-05-22
Jan,

On [http://en.wikipedia.org/wiki/List_of_Intel_Core_2_microprocessors](http://en.wikipedia.org/wiki/List_of_Intel_Core_2_microprocessors) you can see that the T9300 is a Core 2 Duo processor and that all Core 2 processors are 64-bit-enabled.

So you can both run 32-bit and 64-bit: 32-bit is safe and OK, but 64-bit is more interesting. And as you 'dare' to run Ubuntu, you probably should dare to use Ubuntu 64-bit. 64-bit works perfect for me and a lot of other people.

---

### Post by Sef on 2008-05-22
Run the 64-bit Live CD a few times and see how if everything works or not.  If you have problems installing with the Live CD, you can always use the alternate cd to install.

---

### Post by Zorael on 2008-05-22
(Opinionated.)

I like to pick the 64-bit flavors just to do my imaginative part in striving to make it the new standard. 32-bit, in turn, should be phased out. Rarr!

There are some difficulties getting certain applications to work, most/"all" of which are solvable. This is not a limitation of the 64-bit platform, the desktop environment, the distro or the operating system itself, but rather that the application authors won't/can't/don't prepare 64-bit alternatives.

Heck, even Adobe's new Flash player, which is beta and super brand new, won't come with 64-bit support.
> "Adobe is not currently providing a 64-bit version of Flash Player 10." On the bright side he went on to say, "we will evaluate that requirement, which has been requested before, for inclusion in possible future releases based on customer demand."

---

### Post by Yellow Pasque on 2008-05-22
One shouldn't even need an Ubuntu and/or 64-bit CD to see if the CPU is compatible. Any Linux CD should do and then run:
```
cat /proc/cpuinfo
```
If one is currently using Windows (he/she has my deepest sympathies), a freeware CPU info program like CPU-Z should have this info.

As noted, all Core2 CPU's have EMT64

---

### Post by JanRa on 2008-05-23
Thank you all for the info.

I'll try out the 64 bit version and see what happens.

Have a nice day,

Jan

---

### Post by emghufran on 2009-03-03
this is not directly related to this post but i read that a couple of people were successfully running it so i thought i might ask it here. 

I installed 8.04 and then 8.10 on my HP pavilion with the T9300 processor. Everything (important) worked fine except cpu frequency scaling. Ubuntu refused to let the processor at anything less than the maximum 2.5 GHz. I tried upgrading (8.04 -> 8.10) tried to make the cpu frequency scaling to work but it didnt. 

I was wondering if someone has successfully made it to work. If yes, HOW! I reverted back to Windows and desperately want to come back to civilization again!

---

