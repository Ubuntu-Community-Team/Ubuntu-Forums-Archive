---
title: "Ubuntu 8.04.1 won't install on AMD x64 Dual core"
date: 2008-10-06
forum: x86 64-bit Users
---

### Post by MSBriggs on 2008-10-06
> **useroflinux said:**
> I downloaded the new ISO disk file 8.04.1 and checked it.  Then created the 8.04.1 x86-AMD64 loading program on CD.  On boot up it reported "Error Kernel Requires X86-64 only detected an i1586 CPU unable to boot".

I'm having the same prob..

Any fixes?

Thanks,

---

### Post by Sef on 2008-10-06
From the Live CD:

System > Administration > Terminal

type or paste in this code:

```
cat /proc/cpuinfo
```

---

### Post by MSBriggs on 2008-10-06
Thank you.

But how can I make the change if I'm using an iso image?

:confused:

---

### Post by uidb4056 on 2008-10-06
> **MSBriggs said:**
> Thank you.

But how can I make the change if I'm using an iso image?

:confused:

Before to change nothing it's necessary to know what is the result of what Sef has proposed to run from the Live CD after it has booted, with this info available we can suggest you the next steps.

---

### Post by Sef on 2008-10-06
>  But how can I make the change if I'm using an iso image?

It won't make any changes, it will just read the information on your cpu.

---

### Post by MSBriggs on 2008-10-07
Ok, I appologize for my lack of knowledge using Linux. This is my first attempt, and I'm loading it on a virtual drive being run with W2k3 R2 x64. I cfg. my V-client to load the .isa file on boot.

Where do I add your code? As a switch to the .iso load path? Or do I edit the iso?

---

### Post by Yellow Pasque on 2008-10-07
> Where do I add your code? As a switch to the .iso load path? Or do I edit the iso?
No, it's a command to be run in the terminal, but since you can't boot the CD, it does not help you. From reading the original thread, I gather that it's a regression in the Hardy install code and should be reported as a bug on Launchpad.

---

### Post by MSBriggs on 2008-10-09
My thought exactly.

Thanks everyone. 32bit is just fine. :)

---

### Post by benoybose on 2008-10-09
Please specify your processor model. I was thinking to buy a AMD64 based machine for Ubuntu Server 8.04

---

### Post by dabl on 2008-10-09
> **MSBriggs said:**
> 

 I'm loading it on a virtual drive being run with W2k3 R2 x64.



There's your problem.  If your real machine (not the virtual one) is an AMD x64, then boot the 64-bit Live CD on your real machine.  Play with it and satisfy yourself that it works.

Obviously the Live CD is detecting your virtual machine as being 32-bit, regardless of the W2k architecture that you set up on it.

---

### Post by MSBriggs on 2008-10-09
Acpi\authenticamd_-_amd64_family_15_model_67\_0

---

