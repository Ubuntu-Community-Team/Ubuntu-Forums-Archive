---
title: "Virtualbox OSE headers not in repository"
date: 2008-12-07
forum: x86 64-bit Users
---

### Post by John Jason Jordan on 2008-12-07
This morning I installed the latest headers and stuff for 2.6.24-22-generic on my Hardy x86_64 laptop. Now when I try to start a guest OS Virtualbox gives me an error message.

I've had this error message just about every time I've upgraded a kernel. The solution is to go into Synaptic and search on "virtualbox." Sure enough, there are virtualbox-ose headers for the new kernel version that haven't been installed yet. You just install them and Virtualbox is back to normal.

Except that this time there is no package for 2.6.24-22-generic. The latest one in Synaptic is for 2.6.24-21-generic. Yes, I reloaded the repositories in Synaptic.

If I boot to the previous kernel Virtualbox works fine, as before.

Is this an oversight that will be fixed soon?

---

