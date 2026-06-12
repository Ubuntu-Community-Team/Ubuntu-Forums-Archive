---
title: "What can QEMU user mode emulation be used for?"
date: 2006-05-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by n00bWillingToLearn on 2006-05-15
supposedly "QEMU has two operating modes:

 * User mode emulation: QEMU can launch Linux processes compiled for
   one CPU on another CPU.
 * Full system emulation: QEMU emulates a full system, including a
   processor and various peripherials. It enables easier testing and
   debugging of system code. It can also be used to provide virtual
   hosting of several virtual PC on a single server."

What can actually be done with user mode emulation on PPC?

Can I get flash to work using it?

Can I use proprietary nvidea drivers? ( would the GPU acceleration make up for the emulation?)

Can I run wine in it? Or even better compile wine for PPC so that libraries are native and only the actuall binary of the program would need to be emulated?

What are the possible applications?

What are the limitations?

Am I just a dreamer?

 Is this complicated / specific enough that I should try QEMU specific forums?

---

### Post by Ptero-4 on 2006-05-16
the user mode in qemu can run user apps made for x86 in ppc. You can run apps like skype or wine. But you can't run libraries like flash or the nvidia drivers.

---

### Post by ssam on 2006-05-17
as i understand it you could run any x86 linux application. the trouble is that you also need the x86 version of any libraries they use. i think qemu comes with the standard C libraries, which would do for very simple apps. for a graphical program you need a lot of libraries.

there was an effort to merge qemu and wine together to allow running of windows apps in mac os x, [http://darwine.opendarwin.org/](http://darwine.opendarwin.org/) but i think these days they are mostly working on wine for intel macs.

i think getting x86 drivers to work would be a bigger challenge. drivers are part of the kernel, and i dont think an x86 driver would work with a powerpc kernel.

---

