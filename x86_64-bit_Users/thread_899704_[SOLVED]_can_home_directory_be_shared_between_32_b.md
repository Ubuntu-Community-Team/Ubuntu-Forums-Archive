---
title: "[SOLVED] can home directory be shared between 32 bit and 64 os install?"
date: 2008-08-24
forum: x86 64-bit Users
---

### Post by skunkTrader on 2008-08-24
My /home is installed on a separate partition.  Is it possible to install (k)ubuntu 64-bit on a new / partition but use the same /home partition?  Will all my application settings made with 32 bit OS install still work with 64 bit install?  Or will I need to set up a separate /home and reconfigure all my apps?

---

### Post by unca.paka on 2008-08-24
64bit apps should use the same configuration files(preferences, etc). They are just written in a way that makes use of a 64bit architecture.

---

### Post by Thelasko on 2008-08-25
You will basically doing [this.]("http://ubuntuforums.org/showthread.php?t=896762")  It could pose some problems.  I'm not saying it isn't possible, but it's not a good idea.  Especially with the way Flash operates between the two distributions.

P.S.  Remember, they don't have to be [primary partitions]("http://ubuntuforums.org/showthread.php?t=897682"), they can be extended partitions, Ubuntu doesn't care, it's only Windows that you have to worry about.

---

### Post by skunkTrader on 2008-08-29
Sorry for not making the OP clearer.  I was trying to find out if the format of the configuration files created with the 32bit version would be compatible with the 64bit version.  I installed 64 bit 8.04.1.  After making sure that my UID and GID were identical on both installs, I setup my login to point at the partition containing my 32 bit home directory and EVERYTHING worked as expected.

---

