---
title: "Problem: XEN kernel and nvidia video drivers"
date: 2008-01-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by EnkiduinNZ on 2008-01-27
When I use the Xen version of the kernel and the nvdia drivers I get a blank screen and a hard lockup. When I use the generic kernel and the nvdia drivers it works fine. When I use the nv drivers it works fine with the Xen and the generic kernels. This has been an ongoing problem. 

Has anyone any ideas?


Ubuntu: 7.10 
CPU: AMD Athlon(tm) 64 Processor 3200+
Kernel: 2.6.22-14-xen or 2.6.22-14-generic
Video card: G-Force 6200
Monitor: Philips 170B.

Cheers,

Cliff

---

### Post by cjac on 2008-02-08
Hi there,

I'm sorry to be the bearer or bad news, but Xen virtual machines (both dom0 and domU) do not have direct access to PCI devices, and therefore there are some limitations as to the capabilities of these virtual machines.

The specific problem here is that the Xen hypervisor provides an abstraction between the guest virtual PCI devices and the hardware devices.  One of the side-effects of this abstraction layer is an offset between the memory address presented to the guest and the memory address of the physical device.

Since video cards use memory-mapped IO to perform much of their device interaction, this causes a bit of a problem.

It *may* be possible to correct for this problem by forwarding the PCI device to a domU guest, but I expect that this will either not work at all or cause other various problems.

I recommend bringing this issue up on one of the Xen user mailing lists.

Cheers,

C.J.

---

