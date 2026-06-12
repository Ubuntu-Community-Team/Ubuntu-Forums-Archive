---
title: "Edgy install: qparted hangs, and hangs, and...."
date: 2007-01-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by dekalbave on 2007-01-30
I booted the 64-bit Live CD, started the installer and when it got to partitioning, I chose "manually" as I have 3 other OS (two Linux, one WinXP)
installed.  But the cursor just keeps "spinning" and I never get to a partitioning tool.  This happened with Edgy 32-bit, so I assumed that I must need the 64-bit version, but same problem.

Any ideas?

TIA

---

### Post by foxmulder881 on 2007-01-30
Try defragmenting your other partitions first maybe.

It might be struggling to figure out your other paritions.

How long have you waited for?

---

### Post by nemanaldin on 2007-01-30
hi
i have this problem too
but with dapper 64 bit

---

### Post by dekalbave on 2007-01-31
Actually, I solved the problem by downloading and using the alternate install .iso and running it in text mode (Debian-installer).  I still don't know what caused the problem -- too many partitions on my hard drives,
hardware incompatibility, or something else.  I don't know what the debian-installer uses to partition, but I'm pretty sure it isn't Gparted.

Hope this helps someone.

---

### Post by foxmulder881 on 2007-01-31
Actually, it's funny you say that.

I am testing Feisty Fawn atm and we are currently having problems with the partitioner. Very buggy at this stage.

---

