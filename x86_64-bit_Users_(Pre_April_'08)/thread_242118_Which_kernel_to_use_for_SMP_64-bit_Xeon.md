---
title: "Which kernel to use for SMP 64-bit Xeon?"
date: 2006-08-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by rif on 2006-08-23
I'm running 64-bit Dapper on a dual dual-core Xeon machine, and I'm not sure which kernel package to use.  Looking at the package list, I see a linux-amd64-k8-smp package, and I see a linux-amd64-xeon package (implying k8 and xeon want different kernels), and I don't see a linux-amd64-xeon-smp package.  Any suggestions?  Do I have to build my own kernel for this?

---

### Post by John.Michael.Kane on 2006-08-23
install them linux-amd64-xeon kernel. that kernel should be optimized for your cpu,and smp capable aswell.

---

### Post by Contivity on 2006-09-19
How do you choose that kernel? Do you do it after you install or do you do it before?

---

### Post by kuja on 2006-09-19
after

```

sudo apt-get install linux-amd64-xeon

```

---

### Post by Contivity on 2006-09-19
thanks kuja

---

