---
title: "[SOLVED] x86_64 specific kernel package"
date: 2007-10-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by ORi0N on 2007-10-01
Are there actually specific architecture kernel packages in the repositories? Even in 7.04 x86_64 the generic kernel is used, which actually causes problems with the Sound Blaster X-Fi driver installer.

You see the *uname -i* command returns *Unknown* in the output, where a *x86_64* is expected.

If you know if there's  a 64-bit specific kernel package in the repositories, please, let me know, because I didn't find one so far...

---

### Post by John.Michael.Kane on 2007-10-01
> **ORi0N said:**
> Are there actually specific architecture kernel packages in the repositories? 
No. x86_64 specific kernel packages are depreciated. Ubuntu now uses one kernel for all which is the generic one.

> **ORi0N said:**
> Even in 7.04 x86_64 the generic kernel is used, which actually causes problems with the Sound Blaster X-Fi driver installer.
Are you sure it's not an issue with the X-Fi driver, As last time I checked this driver was just released, and is a beta driver on top of that.

> **ORi0N said:**
> You see the *uname -i* command returns *Unknown* in the output, where a *x86_64* is expected.

If you know if there is a 64-bit specific kernel package in the repositories, please, let me know, because I didn't find one so far...

Your options are
1) find out exactly what the issue is with the X-Fi driver.

2) Recompile a newer kernel.

3) Wait for the release of gutsy to see if the issue is resolved by the kernel it uses.

---

