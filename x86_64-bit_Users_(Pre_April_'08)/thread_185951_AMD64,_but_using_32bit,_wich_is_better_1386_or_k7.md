---
title: "AMD64, but using 32bit, wich is better 1386 or k7???"
date: 2006-06-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by terry98 on 2006-06-01
i have a question.... ok im using the i386 kernel with my amd64 but im wondering if the k7 kernel would give me more performance....????

---

### Post by Gustavo on 2006-06-01
I have an AMD64 processor and i386, i686 and k7 kernels. I don't see any difference in performance.

---

### Post by terry98 on 2006-06-01
so... i guess it aint worth it using k7 kernel, ok then im staying with i386.....

thanks for the help!

---

### Post by Gustavo on 2006-06-01
That's only my case. Install linux-k7 and see for yourself. ;)

---

### Post by JoWilly on 2006-06-01
Install k7; this will enable sse, 3dnow for multimedia apps, etc...

---

### Post by Bokonon on 2006-06-01
You really have nothing to lose trying k7.  I liked it.

---

### Post by RAOF on 2006-06-02
[QUOTE=JoWilly]Install k7; this will enable sse, 3dnow for multimedia apps, etc...[/QUOTE]
No, it won't.  Everything that can use sse, 3dnow, etc will do so regardless of what kernel you're using.  If you have a **dual core** Athlon chip (one of the X2s), then you **should** use something other than the -386 kernel - it doesn't have SMP support, so only one of your two cores will be working.  Either of the -686/-k7 kernels will use both cores, though.  This is pretty much the only time changing the kernel from -386 to -686 or -k7 will give you a noticable speed improvement.

That said, the placebo effect can be cool.  I always give out this advice, but **I** run the -k8 kernel.  Find which kernel you prefer - there are sometimes strange issues with one kernel that don't appear in the others.  As long as you install your kernels as the **linux-686** or **linux-k7** packages, it's totally safe.

---

### Post by JoWilly on 2006-06-02
[QUOTE=RAOF]No, it won't.  Everything that can use sse, 3dnow, etc will do so regardless of what kernel you're using.  If you have a **dual core** Athlon chip (one of the X2s), then you **should** use something other than the -386 kernel - it doesn't have SMP support, so only one of your two cores will be working.  Either of the -686/-k7 kernels will use both cores, though.  This is pretty much the only time changing the kernel from -386 to -686 or -k7 will give you a noticable speed improvement.

That said, the placebo effect can be cool.  I always give out this advice, but **I** run the -k8 kernel.  Find which kernel you prefer - there are sometimes strange issues with one kernel that don't appear in the others.  As long as you install your kernels as the **linux-686** or **linux-k7** packages, it's totally safe.[/QUOTE]

Sorry, but if what you say would be true, then on the x86 architecture we would only need 2 kernels : i386 and smp.

If you have ever compiled you own kernel you can see all the different versions are optmized for the cpu. K7 optimizes for the k7 series so the kernel will address all these registers (but of course not necessarily make use of them, as is most probably the case for 3dnow, for example). In the kernel you even have a distiction between amd64 and em64t optimizations...

If you want to learn more about this read the kernel docs, or search the kernel mailing lists, this has been discussed at lenght.

I agree with you in saying that you wont see any differences in performance, because applications need to actually "use" (as you say) the registers for them to be usefull, and there are only a handfull of them.

---

### Post by panurge77 on 2006-06-02
The k7 kernel looks faster here. It's certainly faster booting at least. (6secs on the chronometer)

---

