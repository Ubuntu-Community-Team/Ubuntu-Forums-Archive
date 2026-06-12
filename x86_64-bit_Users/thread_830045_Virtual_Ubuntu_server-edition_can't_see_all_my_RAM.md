---
title: "Virtual Ubuntu server-edition can't see all my RAM"
date: 2008-06-15
forum: x86 64-bit Users
---

### Post by jsgaarde on 2008-06-15
Hi.

I am trying to get an x86_64 ubuntu server running with 8Gb RAM. The system is virtualized using Microsoft's newest HyperV technology.

**Problem description**:
I have a HyperV virtual machine configured with 8Gb RAM and installed ubuntu server-edition (8.04). When I boot the server and log into a terminal and run the "free" command it only shows 4Gb RAM available.
I have a suspicion that it has to do with the kernel configuration or some boot options, because if I start the virtual machine and run memtest (from the grub menu) it sees all of the RAM and starts testing it.

**Question**:
Can somebody say something about what might be the problem or tell me to fire some commands to diagnostic the problem.

**Info**:
```
$ free
             total       used       free     shared    buffers     cached
Mem:       3933348     253620    3679728          0      52844     119232
-/+ buffers/cache:      81544    3851804
Swap:      1494004          0    1494004

```
```

$ uname -a
Linux UbuntuServer1 2.6.24-16-server #1 SMP Thu Apr 10 13:15:38 UTC 2008 x86_64 GNU/Linux

```

Best regards Jakob Simon-Gaarde

---

