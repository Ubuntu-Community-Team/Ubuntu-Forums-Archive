---
title: "WINE not loading at all"
date: 2008-01-31
forum: Wine
---

### Post by KyyubiDX on 2008-01-31
Hi all,

I've installed the latest version of WINE from winehq.org's repository but still it won't work... I've tried to run winecfg using sudo on the terminal but I only get:

> wine: creating configuration directory '/home/kyuubidx/.wine'...
Segmentation fault (core dumped)
wine: wineprefixcreate failed while creating '/home/kyuubidx/.wine'.
wineserver: could not save registry branch to /home/kyuubidx/.wine-JVDCVd/system.reg : No such file or directory
wineserver: could not save registry branch to /home/kyuubidx/.wine-JVDCVd/user.reg : No such file or directory

I don't understand this, can anyone help? I'd be much appriciated...

---

### Post by Meow27 on 2008-01-31
try using synaptic package manager and search wine

install both wine and wine dev

---

### Post by KyyubiDX on 2008-01-31
roger i'll try that now... i'll edit this post asap with results

edit: did that reinstalled both using synaptic both same error...

---

### Post by Meow27 on 2008-02-11
bump 
someone here needs answers :/

---

### Post by PARTyZAN on 2008-02-14
I'm having the same problem. When I try to run winecfg I get "a nice" segmentation fault error on my 64-bit Ubuntu Gusty:

```
winecfg
Segmentation fault (core dumped)
```

There's quite a few complaints about this on Ubuntu forums, but it seems there's no solution to this problem yet.

---

### Post by blackdragon1157 on 2008-02-14
I've heard very very bad things happen when you run WINE related stuff as root.  I'm looking for the exact post I saw ?a week? ago that sounded like this.

---

