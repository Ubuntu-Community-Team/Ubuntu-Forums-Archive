---
title: "Can I run 32-bit kernel and use SMP on AMD64 dual-core CPU?"
date: 2006-01-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by rick333 on 2006-01-05
I'm new to Ubuntu, trying to get it working on a new system running a dual-core AMD64 CPU. I'm running vmlinuz-2.6.12-10-amd64-k8-smp currently, but am a bit daunted by the instructions for running 32-bit apps, chroot, etc., reports of bugs in 64-bit OpenOffice, and would rather punt until better 64-bit support is forthcoming in Ubuntu.

Has anyone tried building a 32-bit kernel that will utilize both CPUs in SMP? Is this possible, or will it not work?

Thanks,

Rick

---

### Post by koverg on 2006-01-06
I have not tried and I have an Intel Dual Core CPU, but I'am sure that:

1. Ubuntu 5.10 32 bit should work fine on your machine since AMD64 is fully 32 bit compatible.
2. Building a 32 bit kernel is not enough, since 32 bit kernel cannot run your distro where most apps are 64 bit.

If you want a 32 bit kernel reinstall your system from a 32 bit Ubuntu distro. There are precompiled kernels for your SMP CPU, but of cource can compile a new kernel is you need that.

Gabor

---

### Post by rick333 on 2006-01-06
[QUOTE=koverg]
If you want a 32 bit kernel reinstall your system from a 32 bit Ubuntu distro. There are precompiled kernels for your SMP CPU, but of cource can compile a new kernel is you need that.
Gabor[/QUOTE]

Oh, ok I didn't know that. So you're saying that simply booting a 32-bit kernel will not be sufficient to switch to 32-bit operation. I must reinstall? Is this because the 32 vs. 64 bit installs setup the /lib directories differently and won't be able to obtain the correct libraries? is smp

I just checked in /boot on another machine I have that's running Ubuntu 32-bit 386 and it only has 2 kernels: vmlinuz-2.6.12-10-386 and vmlinuz-2.6.12-9-386. I don't see a kernel that identifies itself as SMP compatible. If I ran one of these kernels, won't the 2nd CPU be ignored? I don't want that -- I'd choose to stay with 64-bit.

Rick

---

### Post by koverg on 2006-01-06
[QUOTE=rick333]
I just checked in /boot on another machine I have that's running Ubuntu 32-bit 386 and it only has 2 kernels: vmlinuz-2.6.12-10-386 and vmlinuz-2.6.12-9-386. I don't see a kernel that identifies itself as SMP compatible. If I ran one of these kernels, won't the 2nd CPU be ignored? I don't want that -- I'd choose to stay with 64-bit.

Rick[/QUOTE]
32 bit and SMP are two different things. There are SMP kernels for both 32 and 64 bit.

What do you mean by that you'd choose to stay with 64 bit? On 32 bit kernel you won't be able to run 64 bit applications as I already told you. That is why you must install a new system.

Gabor

---

### Post by rick333 on 2006-01-06
[QUOTE=koverg]32 bit and SMP are two different things. There are SMP kernels for both 32 and 64 bit.
Gabor[/QUOTE]

Yes, I do realize that. My question really was whether I could run a 32-bit SMP capable kernel on an AMD64 dual core CPU and have it use both CPUs. I just installed Ubuntu x86 (32 bit) on my machine and have installed the k7-smp kernel. I assume that is the right choice rather than the 686-smp kernel. Correct? Anyway, I'll try it.

Thanks... Rick

---

### Post by rick333 on 2006-01-06
OK, I installed the linux k7-smp kernel (package linux-image-xxx-k7-smp) and it appears to work very nicely on my machine. If anything, things seem faster, not slower than the 64 bit installation I had before. 

So, for anyone else who is struggling with AMD64 dual-core, it appears that doing a 32-bit install is a very reasonable alternative. I'll post here again if I run into problems with this but so far so good.

Thanks,

Rick

---

