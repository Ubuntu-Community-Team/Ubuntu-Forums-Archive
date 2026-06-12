---
title: "Cannot upgrade kernel from generic to k8? Fresh gutsy install"
date: 2007-12-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by gardener on 2007-12-13
First, here is what I have:
Linux alpha-desktop 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64 GNU/Linux

I would like to update to the k8 version of this kernel.

I am unable to find the packages through apt-get or synaptic? I have searched extensively through the forums, but all of the answers seem to require I have access to a kernel version which I cannot find. I would rather download it through apt-get, but I have compiled a kernel before and although it would not be ideal I would do it again. 
I have already seen most of the tutorials on the subject, and I understand how to use apt to install kernel images and headers, but I do not find those images or headers, which I had assumed were
2.6.22-14-amd64-k8 or 2.6.22-14-k8. Neither of those (after linux-image, etc.) work correctly.
TIA

---

### Post by Kilz on 2007-12-13
> **gardener said:**
> First, here is what I have:
Linux alpha-desktop 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64 GNU/Linux

I would like to update to the k8 version of this kernel.

I am unable to find the packages through apt-get or synaptic? I have searched extensively through the forums, but all of the answers seem to require I have access to a kernel version which I cannot find. I would rather download it through apt-get, but I have compiled a kernel before and although it would not be ideal I would do it again. 
I have already seen most of the tutorials on the subject, and I understand how to use apt to install kernel images and headers, but I do not find those images or headers, which I had assumed were
2.6.22-14-amd64-k8 or 2.6.22-14-k8. Neither of those (after linux-image, etc.) work correctly.
TIA

The k-8 kernel does not exist in Gutsy. Dapper was the last version with a k-8 kernel if memory serves me correctly.

---

### Post by Melcar on 2007-12-13
Those kernels are all deprecated.  We only have "generic" kernels now that have all the proper modules.  If you want to have a kernel for your own CPU arc. then the only option is to compile your own.  I have done so plenty of times and I can tell you that unless you do some serious CPU crunching operations, you won't notice much of a difference.  It's always fun to compile kernels thought :).

---

### Post by gardener on 2007-12-14
Thank you both.

---

