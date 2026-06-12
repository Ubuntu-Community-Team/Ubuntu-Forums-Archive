---
title: "VMware Server 2 beta 2 on Hardy - Intel VT mode?"
date: 2008-04-30
forum: x86 64-bit Users
---

### Post by jharrop on 2008-04-30
/var/log/messages contains:

/dev/vmmon10178: Task_Switch: Intel VT mode is in use by some other software
/dev/vmmon10178: Vmx86_RunVM: Task_Switch failed

and the virtual machine won't start. Event details say "VMware Server unrecoverable error: (vcpu-0) VCPU 0 RunVM failed: Operation not permitted."

I only upgraded to VMware Server 2 beta 2, because after upgrading Ubuntu x86_86 from 7.10 to 8.04, the system froze whenever I started a VM (in VMware Server 1.0.2 and 1.0.5).

Interestingly, I now see [http://bugzilla.kernel.org/show_bug.cgi?id=9894](http://bugzilla.kernel.org/show_bug.cgi?id=9894) which seems to explain what I was seeing on 1.0.x.

At a guess, I did rmmod kvm_intel and rmmod kvm, but /var/log/messages still says "Intel VT mode is in use by some other software" when I try to start a VM.

My host is a Dell Precision Workstation 490, running a Xeon quad core, which is reported as 4 x E5335 @ 2.00GHz

Any idea how I find out what other software is using VT mode? Or other suggestions?

thanks

Jason

---

### Post by marvin1969 on 2008-06-04
I had a similar issue.  Uninstalling KVM and restarting cured it for me.  The kernel module conflicts with VMMON.

fwiw,
m

---

