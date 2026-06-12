---
title: "Wireless Problem"
date: 2007-03-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by gilbert_ke on 2007-03-02
I just ran the latest security update on my laptop - amd turion, Atheros AR5005G wireless card. The wireless was working fine before I ran the update, now the wireless is not recognized in the neworking tools and I get:

*-network:1 UNCLAIMED when running lshw -C network

Any ideas on how to fix this problem. Note there were errors in updating the linux-restricted-modules - the files were not found for Edgy.

The wiki has a TODO on this item - time to do it.

---

### Post by Princey on 2007-03-02
> **gilbert_ke said:**
> I just ran the latest security update on my laptop - amd turion, Atheros AR5005G wireless card. The wireless was working fine before I ran the update, now the wireless is not recognized in the neworking tools and I get:

*-network:1 UNCLAIMED when running lshw -C network

Any ideas on how to fix this problem. Note there were errors in updating the linux-restricted-modules - the files were not found for Edgy.

The wiki has a TODO on this item - time to do it.

You have to install the restricted modules for the kernel for the wireless to work. When you say you had errors in updating restricted modules, what exactly do you mean?

---

