---
title: "Ubuntu 64, Dual Core"
date: 2006-01-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by ATAQ on 2006-01-03
does ubuntu 64 use both cores of my cpu, becuase it system monitor I cant see two cores listed.

---

### Post by koverg on 2006-01-03
Hello!

I have Asus P5WD2 P4 D 820@3.2 GHz.

My system is:
Linux ubuntu 2.6.12-9-amd64-xeon #1 SMP Mon Oct 10 13:22:55 BST 2005 x86_64 GNU/Linux

If you also see SMP in "uname -a", than sure it uses both cores.
If you have other kernel try installing 2.6.12-9-amd64-xeon.

You may also try running System Monitor. It show both CPUs for me.

Cheers,

Gabor

---

### Post by ATAQ on 2006-01-03
I just installed 2.6.12.10-amd64-k8-smp,

It now shows both cores and is running pretty well.
Thanks a mill!!

Regards Ant.

---

### Post by Suger on 2006-01-03
k8 ? Isn't that for AMD processors ?

---

### Post by nbhaskar on 2006-01-03
[QUOTE=ATAQ]I just installed 2.6.12.10-amd64-k8-smp,

It now shows both cores and is running pretty well.
Thanks a mill!!

Regards Ant.[/QUOTE]

And how did you do that?

Thanks a lot.

---

### Post by RAOF on 2006-01-04
[QUOTE=Suger]k8 ? Isn't that for AMD processors ?[/QUOTE]
Yup.  But it will probably run on Intel processors, too.  If you have an Intel processor, the kernel you want is linux-amd64-xeon-smp, rather than -k8-smp.

In order to install the SMP kernel, you just need to go to synaptic (System->Administration->Synaptic Package Manager), search for "linux-amd64-xeon-smp" (or whatever variant you're after), and select it for installation.  Then hit "apply".  Done.

---

### Post by Aphorism on 2006-01-04
amd64 bit architecture is only compatible with amd k8 chips and the newer intel em64 chips (which are a clone of the arch)

Don't bother trying it unless you have one of those varieties. 

Hope this helps...

---

### Post by koverg on 2006-01-04
[QUOTE=Aphorism]amd64 bit architecture is only compatible with amd k8 chips and the newer intel em64 chips (which are a clone of the arch)

Don't bother trying it unless you have one of those varieties. 

Hope this helps...[/QUOTE]
See the original post!
Pentium D 820 is one of those newer chips. It's dual core, supports SSE3 and EM64T which Intel's name for AMD64 "compatibility".

So this chip is fully compatible with AMD64. The only reason there are separate versions is optimization and may be SSE3. If I remember correctly early AMD64 CPUs had no support of SSE3.

Gabor

---

### Post by heartsglory on 2006-01-04
That's true.  early AMD64 cpu's didn't support SSE3 instruction set.  If I'm not mistaken the Socket 939 CPU's do support SSE3 instruction set (Venice core for AMD64?)

---

### Post by nbhaskar on 2006-01-05
I've a AMD Athlon 64 X2 3800+ processor running on a ECS nForce4 A939 mobo with 2GB RAM. I installed the AMD64 version of breezy. It works just fine.

---

### Post by koverg on 2006-01-05
[QUOTE=nbhaskar]I've a AMD Athlon 64 X2 3800+ processor running on a ECS nForce4 A939 mobo with 2GB RAM. I installed the AMD64 version of breezy. It works just fine.[/QUOTE]
Yup! That's evident. The question is: which kernel suites better for 820?
- the AMD k8
- or the amd64-xeon.
I think that's the xeon, because
1. It's Intel optimized.
2. It can rely on SSE3 since all 64 bit Intel CPU supports it.

Gabor

---

