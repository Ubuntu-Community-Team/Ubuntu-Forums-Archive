---
title: "AMD64 Kernel"
date: 2007-05-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by mburoff on 2007-05-16
I just upgraded to Feisty and was looking to upgrade my kernel from the generic x86_64 to the amd64-k8 kernel; however, synaptic says this is obsoleted by the generic packages.  I noticed that the version of the amd64-k8 was 2.6.20.15.14 whereas the generic version was 2.6.20-15.17.  Is k8 obsoleted because the generic packages are built upon a newer kernel or because k8 has been replaced by the generic?  Thanks for any help.

---

### Post by John.Michael.Kane on 2007-05-16
Ubuntu is now running one kernel which still enables optimizations for your CPU at boot. So theres no longer a need for separate kernels.

---

### Post by whyrlito on 2007-06-06
Hmm... alright...
I was searching for those good old k8 specific kernels.
Changing from amd64-generic to amd64-k8 on a Dapper notebook pretty much improved it's performance. Upgraded to Feisty, as [COLOR="Blue"]mburoff[/COLOR] did, and just noticed the same.

So, [COLOR="Blue"]SD-Plissken[/COLOR], do you know where can I find such kernel boot options (those that may be architecture - k8 - specific)?

Thanks a lot.

---

