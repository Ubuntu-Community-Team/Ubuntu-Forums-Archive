---
title: "Internet Dying"
date: 2007-08-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by gaylapdancer on 2007-08-01
Hey guys, After an update this afternoon, my internet connection dies after maybe 15 minutes and I have to restart to get it back. This only started happening after todays updates from update manager. 

How can I check what I installed, and if you guys think it is the problem, remove them? 

This isn't just my machine either, All the local 7.04 users have the same deal, and the disconnections are simultaneous throughout the city.

Any advice?

---

### Post by PaulFr on 2007-08-01
As far as what have been installed recently, ```
grep ' installed' /var/log/dpkg.log*|cut -d: -f2-|sort
``` should do the trick. As far as synchronized Internet disconnects, I dont see anything like that here. The last update I installed was **firefox 2.0.0.6+1-0ubuntu1** and its accompanying libraries. Could it be your ISP ?

---

### Post by gaylapdancer on 2007-08-01
The only thing that looks like it could have the slightest thing to do with is appears to be 

```
tcpdump 3.9.5-2ubuntu1

```

It could be the ISP, If it persists I'll try them. Thanks

---

