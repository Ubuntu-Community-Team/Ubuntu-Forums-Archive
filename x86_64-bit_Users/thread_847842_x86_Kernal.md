---
title: "x86 Kernal?"
date: 2008-07-02
forum: x86 64-bit Users
---

### Post by tuxxy on 2008-07-02
Hi,

I just stumbled upon an article for Ubuntu, I am interested to know if the following still applys or has there been a development in this situation, I was hoping so as the article dates 06.

 > 10. A new kernel

Ubuntu will install a 386 kernel for x86 machines, which probably isn't what you'd want if you've got a Pentium II or better CPU. The 386 kernel is compiled to work with just about any x86 CPU, but extensions that appear in later CPUs can give your system a boost, if they're taken advantage of. To replace the kernel, open Synaptic or Adept and search for linux-image. You'll see several choices. Pick the one that best suits your CPU -- probably the linux-image-686 package for Pentium II and later CPUs, and linux-image-k7 for later AMD processors. Note that if you're using the AMD64 line (or Intel's x86-64 CPUs) you should be using the amd64 images.

Of course, once you install the new kernel, you'll need to reboot. Another benefit to the 686 kernels is that they have SMP support, which is a bonus for multi-core and Intel HyperThread CPUs.


I have checked my kernal in synaptic and just says kernal on x86 so am assuming this is the correct kernal for an AMD x86 system? 

full article: [http://www.linux.com/articles/54945](http://www.linux.com/articles/54945)

---

### Post by jpkotta on 2008-07-02
Yeah, that's out of date.  You want the generic kernel for a desktop/laptop unless you have special requirements.

---

