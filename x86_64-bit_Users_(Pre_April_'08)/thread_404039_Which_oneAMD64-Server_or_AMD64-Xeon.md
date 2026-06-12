---
title: "Which one?AMD64-Server or AMD64-Xeon"
date: 2007-04-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by datayoung on 2007-04-07
I using Dell1425 have 1 CPU xeon 3.0
To upgrade kernel image which one would be suite for my Xeon ?
I saw AMD64-server and AMD64-xeon while use aptitude
and what is difference of them?

---

### Post by Kilz on 2007-04-07
> **datayoung said:**
> I using Dell1425 have 1 CPU xeon 3.0
To upgrade kernel image which one would be suite for my Xeon ?
I saw AMD64-server and AMD64-xeon while use aptitude
and what is difference of them?

That depends on what version of Ubuntu or Kubuntu you are using. Because in Edgy and above the different kernel packages like xeon dont exist. There are dummy packages, but they dont install anything, they were left over from Dapper. There is only generic and server left.
If you are running Dapper, install them both and see what one you like the best. You will be able to boot the different kernels in grub.

---

### Post by datayoung on 2007-04-08
using dapper (6.06.1)
In amd64-server is it supported xeon?
or in amd64-xeon it have server+xeon?

I using for web hosting server

---

### Post by Kilz on 2007-04-08
> **datayoung said:**
> using dapper (6.06.1)
In amd64-server is it supported xeon?
or in amd64-xeon it have server+xeon?

I using for web hosting server

Since its Dapper both are avilable.
amd64-server = specifically written for servers. It is probably your best bet. Secondly, with this kernel installed you have upgrades/patches untill 2011.
amd64-xeon = written for any computer built with a xeon processor. The optimizations are based on the processor.

---

