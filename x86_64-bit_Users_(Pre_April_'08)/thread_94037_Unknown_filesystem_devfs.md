---
title: "Unknown filesystem devfs"
date: 2005-11-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by ioan123 on 2005-11-23
I just installed Ubuntu64 on my new Prescott 630 --> works like a charm. I have noticed though that the Hypertreading is not enabled.

I have then downloaded the latest kernel (2.6.14.2), recompiled using the Ubuntu config and turned on Hypertreading support.

It works well now, except that I get the error message "Unknown filesystem devfs" at boot. I have seen on forums that devfs is deprecated on kernel > 2.6.13 and it should be replaced by udev.

Does anybody know how to do this? I have no idea how to proceed.

In addition to the message, the forward and backwards button of my mouse doesn't work anymore - I assume it is related to devfs

Any help highly appreciated

Thanks

Ioan

---

### Post by bonzodog on 2005-11-23
there is a version of the current kernel with smp enabled for 64 bit. it will be in the repositories. It sounds like a easy-to-make mistake during the config. You can either re-compile the kernel and try again, or use the pre-built amd64-smp kernel.

---

### Post by ioan123 on 2005-11-23
Hello bonzodog

Thanks for your suggestion. Actually, I have already tried, but it is worse:
- the SMP kernel doesn't recognize le multithreading (maybe it is compile for "true" smp support only)
- my sound card (Intel HDA) is not built into that kernel, so no sound

It seems that to get the Hypertreading working, I need 2.6.13+

Thanks anyway! Any other idea appreciated!

Ioan

---

