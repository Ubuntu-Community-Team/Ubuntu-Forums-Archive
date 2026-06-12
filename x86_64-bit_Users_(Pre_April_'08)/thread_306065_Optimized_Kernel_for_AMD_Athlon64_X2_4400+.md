---
title: "Optimized Kernel for AMD Athlon64 X2 4400+"
date: 2006-11-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by charlie. on 2006-11-24
I see that "linux-amd64-k8-smp" has been marked as obsolete and that Edgy for amd64 has installed with a "generic" kernel. How then, do I install an optimized kernel that will make use of the features of my AMD Athlon64 X2 4400+ processor?

In the past (Dapper), I used the "amd64-K8-smp" kernel.

Thanks for any answers.

---

### Post by Pinoy915 on 2006-11-24
That generic kernel is already optimized for any 64-bit processors. They wanted to make it easier for the users so that we don't have to choose different kernels. If you do the cat /proc/cpuinfo it should show you that you have both processors listed.

---

### Post by Kilz on 2006-11-24
> **charlie. said:**
> I see that "linux-amd64-k8-smp" has been marked as obsolete and that Edgy for amd64 has installed with a "generic" kernel. How then, do I install an optimized kernel that will make use of the features of my AMD Athlon64 X2 4400+ processor?

In the past (Dapper), I used the "amd64-K8-smp" kernel.

Thanks for any answers.

Dapper amd64 didnt have a special smp kernel. All 64bit kernels in dapper were smp. As such smp was not in the name. But all the different kernels are gone in Edgy. So the generic one may be the best you have available without compiling your own.

---

### Post by charlie. on 2006-11-24
Ok, right.

Perhaps the descriptions of the old packages should have said why they were no longer necessary, instead of just saying they've become obsolete. Some of us like to know these things.

Thanks.

---

### Post by incubus on 2006-11-24
> **charlie. said:**
> Ok, right.

Perhaps the descriptions of the old packages should have said why they were no longer necessary, instead of just saying they've become obsolete. Some of us like to know these things.

Thanks.

That is actually a good idea. Many people have asked the same question for the same reasons around here. A short explanation would suffice. 

I don't know if the developers would still be up for doing that, but it could be worth suggesting. They will probably argue that the vast majority of users have no idea about the different kernels.

incubus

---

### Post by charlie. on 2006-11-25
Somebody had to type that message about those modules being obsolete. Another line stating that the features formerly provided by those modules where now included in the generic kernel would have been little extra work.

Does the same hold true for the i386 platform?

---

### Post by incubus on 2006-11-25
As far as I know, yes.

The idea, to present it poorly, is that if you're savvy enough to notice any difference in the kernel performance, you're probably savvy enough to compile your own kernel and get exactly what you want. This takes some work load from the developers, who now have to worry about only one, generic kernel.

They did some benchmarks before deciding for this. They found that there was little performance gain across the different (now obsolete) kernels.

If you think about it, it does make sense. Compiling your own kernel is easy in Debian/Ubuntu. Release kernels are usually a little on the heavy side, because they have to offer support to everybody.

incubus

---

### Post by konstk on 2006-11-25
As long as they didn't make all the packages generic instead of amd64 it's all good. Compiling your kernel is easy compared to comipling the packages

---

### Post by finite9 on 2006-11-27
This feels like a quick way out of doing some work from my point of view.  Seems like the devs don't have time/resources to support multiple kernels so that make one generic and say the rest are obsolete.  How can they be obsolete?  The wording is very poor.  There is still a want/need for an optimised 64-bit kernel, as this thread suggests, and the generic kernel does not include the optimisations present in the generic kernel.  That's why its called generic.

This, put together with the fact that the 2.6.17-10 generic kernel is unstable with AMD Turion64 (ML-28) chips, so much so that an Edgy system is unusable on these systems, and you have a situation whereby Canonical have alienated a large group of 64-bit users with the Edgy release.

---

