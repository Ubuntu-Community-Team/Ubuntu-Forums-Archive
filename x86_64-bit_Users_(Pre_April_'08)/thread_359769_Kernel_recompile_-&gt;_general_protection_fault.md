---
title: "Kernel recompile -&gt; general protection fault"
date: 2007-02-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by mr.f on 2007-02-12
I'd like to apply a single patch to the stock kernel, but it means a recompile (it is not a module). I've done this successfully before by downloading the ubuntu kernel source (not vanilla from kernel.org), use the config stored in /boot, and use the procedure described here: [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

Both the successful and failed attempts were with Edgy, but on different computers. The one I get stuck on is a HP nx9420 laptop.

Now, without applying any patch, I follow this Howto and compile the current 2.6.17-11 kernel, install, and reboot. But I get stuck when running modprobe. This is the short version of what happens during boot:

TPM found ....
General protection fault...
/sbin/modprobe abnormal exit

If anyone has an idea of what the problem is, any help would be appreciated.

---

### Post by mr.f on 2007-02-13
As a follow-up, I recompiled the kernel again but disabled TPM support, since it seemed like it was when trying to load this module that modprobe failed.

Without TPM the system booted with my new kernel. The system seems mostly functional, however, I've noticed so far that the wifi card is not detected during boot so perhaps I can't use wireless? There may be other stuff too, but nothing I noticed immediately.

Some new questions if anyone has a clue:

Does anyone know more about the TPM modules? When are they useful? Do you need some sort of certified modules, is that why I can't compile them myself (I've figured out it has something to do with trusted computing)? Can the lack of TPM be the reason why wifi does not work or are these problems likely to be unrelated?

---

