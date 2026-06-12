---
title: "Can't install wine in Xubuntu 7.10"
date: 2008-07-15
forum: Wine
---

### Post by bermuda.sunset on 2008-07-15
Tried via add/remove, synaptic and command and gave me this:

wine:
 Dépend: libldap-2.4-2 (>=2.4.7) but it is not installable
  Pré-Dépend*: dpkg (>=1.14.12ubuntu3) mais 1.14.5ubuntu16 doit être installé

Added the medibuntu source and still nothing

Any help?

---

### Post by LinuxRocks713 on 2008-08-03
> **bermuda.sunset said:**
> Tried via add/remove, synaptic and command and gave me this:

wine:
 Dépend: libldap-2.4-2 (>=2.4.7) but it is not installable
  Pré-Dépend*: dpkg (>=1.14.12ubuntu3) mais 1.14.5ubuntu16 doit être installé

Added the medibuntu source and still nothing

Any help?
Try:
```

sudo apt-get -f install libldap-2.4.2 dpkg libldap
sudo apt-get install wine

```

---

