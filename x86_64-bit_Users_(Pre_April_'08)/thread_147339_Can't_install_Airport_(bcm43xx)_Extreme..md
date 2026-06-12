---
title: "Can't install Airport (bcm43xx) Extreme."
date: 2006-03-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by slooksterpsv on 2006-03-20
I'm having troubles installing Airport Extreme. I've installed the new Kernel Image along with the Headers that were directed from another thread (the one about the bcm43xx). Here's how far I got:
I installed bcm43xx-fwcutter no problem.
I try to install softmac-whatever it is, but it and the bcm43xx-latest... but it gives me the following errors when doing make:
ERROR nothing to (build or make) in /lib/modules/2.6.15.1/build

Anyone else have this issue? the build directory is empty. too. All other packages on are on my desktop.

---

### Post by slooksterpsv on 2006-03-20
Ok so I figured out there is a syntax error in the bcm43xx code. It's trying to do static struct ..... and it says it canf find nr_frags etc. etc. etc.
I'm going to install Kubuntu later on tonight (get rid of Ubuntu) and see if that works better or works at all. If someone has a complete detailed instructions for how to do this, please post here or email me.

---

### Post by ssam on 2006-03-20
i doubt changing from ubuntu to kubuntu will make much difference. at the level of kernels, dirvers and networking they are identical. you may have better luck switching to dapper, the development branch of ubuntu. it has a snapshot of the driver from the 14th of march in the kernel.

---

### Post by slooksterpsv on 2006-03-20
I'm downloading Kubuntu PPC Flight 4 or 5 (whichever is out) so I'm gonna install that tomorrow after I get home from Brainshare and that.

---

### Post by utnubu! on 2006-03-21
Can anyone write a foolproof tuturial (or give me a link to one) To get the airport working on my powerbook.

---

