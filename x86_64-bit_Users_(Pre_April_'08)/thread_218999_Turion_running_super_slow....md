---
title: "Turion running super slow..."
date: 2006-07-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by itsdaveperdue on 2006-07-19
Hey Folks,
At first I thought it might be just the installation cd, but after installing 6.06 (64-bit) I've realized that the problem must be elsewhere. 
I've got a Turion ML-37 (2.0GHz).  It runs VERY slow.  The system shows it running at 800MHz.  I've tried stopping powernowd, but that doesn't fix it.  I've used cpufreq-selector, but that doesn't fix it.  I've setup the Scaling Monitor to let me manually change the frequency, but that doesn't fix it.  I've even disabled powernow in my BIOS.  The system then runs at 2GHz, but still seems very very slow.  

The processor works and scales fine in SuSe, Gentoo, and Fedora.

Any help would be greatly appreciated.

---

### Post by hizaguchi on 2006-07-24
Wish I could help you, but I have the same problem with a 1.6 GHz Turion.  Maybe this would be a good time to check out Suse.  Heard it's buggy though.

---

### Post by hizaguchi on 2006-07-25
Well, I installed the k8 SMP kernel, which I'm sure is at least good for my performance, but still 800MHz.

When yours was working with those other distros, were you using apm or acpi?

---

### Post by dasyar613 on 2006-07-25
I am curious, how did you determine that your processor is running slow. I would like to try it on my machine using your methods, that way we will be talking oranges-oranges. I have a turion64, just one processor though.

---

### Post by hizaguchi on 2006-07-25
> **dasyar613 said:**
> I am curious, how did you determine that your processor is running slow. I would like to try it on my machine using your methods, that way we will be talking oranges-oranges. I have a turion64, just one processor though.
You can get information on your processor(s) with
```
cat /proc/cpuinfo
```

Anyhow, I'm understanding things a little more clearly now.  I installed powersaved (to replace powernowd) and kpowersave.  With the kpowersave applet I can set my profile to "performance" and both cores jump right up to 1.6 GHz where they should be.  So it looks like (at least with powersaved) the processor is capable of running full speed.  I'll have to go find something really CPU intensive to see if it will scale up automatically.  And something more fine-grained than 1/2 speed or full speed would be nice.

itsdaveperdue, is yours actually running poorly, or is the problem just that it says its running at 800MHz?  Does installing powersaved make any difference?

---

### Post by itsdaveperdue on 2006-08-17
My system is running very poor, hardly useable.  I don't know what's going on with it, heh.  Right now SuSE is on it running fine, but I'd rather have Ubuntu.

Has anyone figured this out?  How would I boot the install with no-apic, and would that even do anything?

---

### Post by itsdaveperdue on 2006-08-17
Aha, add noapic nolapic to your boot options and it will work just fine...!!

---

