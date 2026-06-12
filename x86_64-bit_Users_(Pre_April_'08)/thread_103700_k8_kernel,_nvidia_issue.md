---
title: "k8 kernel, nvidia issue"
date: 2005-12-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by rplantz on 2005-12-14
I installed the k8 kernel using Synaptic and lost the ability to start xserver.

I had changed my /etc/X11/xorg.conf file for my screen's refresh rates, and I had run nvidia-glx-config enable, which noted that my xorg.conf had been changed.

I could still run by selecting the generic kernel during boot time.

I fixed things by restoring /etc/X11/xorg.conf to the original (yes, do backup the original!). Rebooting into the k8 kernel worked. I then applied my changes to /etc/X11/xorg.conf and ran nvidia-glx-config enable again.

It all works fine, but I don't know why. If anyone can enlighten me, I would appreciate it.

---

### Post by RAOF on 2005-12-14
It's possible that you hadn't installed the linux-restricted-modules package for the k8 kernel.  That contains the nvidia kernel module you need for the nvidia X drivers to work.

To avoid this in the future, install kernels from synaptic with the "linux-amd64-k8" metapackage - it's an empty package that simply depends upon the latest k8 kernel, & all the associated stuff like restricted modules.

---

### Post by rplantz on 2005-12-14
You are right. I did not install the meta package.

But why would it work when I simply reverted back to the original xorg.conf, then applied my changes to that file?

Everything seems to be working okay now, so I don't *need* an answer to this question. But I would like to learn about this, so I would be most appreciative is someone can point me to some documentation.

---

### Post by RAOF on 2005-12-14
I'm not sure.  Maybe nvidia-glx-config enable does more than just edit the xorg.conf?  Maybe it also copies the kernel module to the right place?  The amd64-generic kernel module would work just fine for the k8 kernel.

---

### Post by Hoop on 2005-12-15
If you have nvidia frame buffer support enabled in your kernel or the nvidia display support enabled, they clash with the nvidia driver that loads on boot causing it to error. Just switching back to an old xorg.conf wouldn't help. Like with alsa support. You can't have it pre-loaded into the kernel and then use the alsa-driver. If you want to use alsa-driver. then in the kernel you have to have alsa support as a module.

---

