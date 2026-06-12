---
title: "Nvidia 8762 with AMD64 k8 kernel"
date: 2006-06-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by BobW on 2006-06-03
It looks like the nvidia 8762 driver is only available with the and64-generic kernel but not the amd64-k8 kernel.

Am I stuck with a manual install of the driver if I want to use the k8 kernel?

---

### Post by JoWilly on 2006-06-03
Are you sure ? Its also icluded in the -xeon package.

Have you checked that the -k8 restricted-modules package is installed ?

... if so then post a bug on launchpad, as it should be in.

---

### Post by BobW on 2006-06-03
The restricted-modules package package is available, but I can't install nvidia-glx which I thought was also needed. nvidia-glx wants to install the amd64-generic kernel.

---

### Post by JoWilly on 2006-06-03
[QUOTE=BobW]The restricted-modules package package is available, but I can't install nvidia-glx which I thought was also needed. nvidia-glx wants to install the amd64-generic kernel.[/QUOTE]


It should not do this...

You have to install nvidia-glx. But this is not a problem. You will just have 2 kernel choices at boot...

Dont forget to post a bug report on launchpad to inform the developpers.

---

