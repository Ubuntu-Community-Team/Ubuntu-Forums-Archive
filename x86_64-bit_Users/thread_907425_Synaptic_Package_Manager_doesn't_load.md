---
title: "Synaptic Package Manager doesn't load"
date: 2008-09-01
forum: x86 64-bit Users
---

### Post by Mercedes300 on 2008-09-01
I'm having difficulty with three system applications in ubuntu:
1. Add/Remove Programs - doesn't add/remove anything, but you can check all the things you want to, to no avail.
2. Synaptic Package Manager - won't load from the System-Administration-Synaptic Package Manager menu. You can, however, you can load it through a terminal by running: *sudo synaptic*
3. Update Manager - loads but doesn't update anything and can't refresh the list of updates by clicking "Check".

All help to resolve this is much appreciated.

John

Dell precision 490 workstation
12 Gigs of ram
Dual quad-core Intel Xeons @ 3.0 GHz each

---

### Post by Stemp on 2008-09-01
You tried using the command line ?

```
sudo apt-get update
```

and then

```
sudo apt-get safe-update
```

---

