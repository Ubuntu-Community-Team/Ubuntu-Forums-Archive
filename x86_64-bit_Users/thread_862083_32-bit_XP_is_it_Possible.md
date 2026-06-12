---
title: "32-bit XP is it Possible?"
date: 2008-07-17
forum: x86 64-bit Users
---

### Post by Zer0Nin3r on 2008-07-17
It's been a couple of versions of Ubuntu since I last tried virtualization.  The reason why I never stuck with it (VMware) was that I was unable to use my Wacom tablet with Photoshop under virtual XP

Recently I"ve been contemplating on moving from 32-bit Ubuntu to 64-bit.  I want to give it a whirl to make sure things work out properly first, but my true question is this:

[B]Will I be able to run a virtualized version of 32-bit XP with Sun's VirturalBox running under Ubuntu 64-bit?  
[/B]
(I am running a dual core AMD and a first gen Athalon 64 on the laptop.)

---

### Post by jocko on 2008-07-17
> **Zer0Nin3r said:**
> It's been a couple of versions of Ubuntu since I last tried virtualization.  The reason why I never stuck with it (VMware) was that I was unable to use my Wacom tablet with Photoshop under virtual XP

Recently I"ve been contemplating on moving from 32-bit Ubuntu to 64-bit.  I want to give it a whirl to make sure things work out properly first, but my true question is this:

[B]Will I be able to run a virtualized version of 32-bit XP with Sun's VirturalBox running under Ubuntu 64-bit?  
[/B]
(I am running a dual core AMD and a first gen Athalon 64 on the laptop.)

Virtualbox can only run 32 bit guests, no matter what host os you have, so the answer to your question is "yes".

---

### Post by neilius on 2008-07-17
Yes, I run a 32 bit XP on my 64 bit Ubuntu inside VirtualBox. Works great.

---

### Post by Zer0Nin3r on 2008-07-17
Excellent!!  Thanks for the info!  I'll give it a whirl and close out this thread when I'm done.

---

### Post by dcstar on 2008-07-18
> **jocko said:**
> Virtualbox can only run 32 bit guests, no matter what host os you have, so the answer to your question is "yes".

Interesting, I run 64 and 32 bit VMs using VMWare server on my 64 bit Ubuntu, I would have thought most VM environments would have had this capability - obviously not!

---

### Post by jespdj on 2008-07-18
> **dcstar said:**
> Interesting, I run 64 and 32 bit VMs using VMWare server on my 64 bit Ubuntu, I would have thought most VM environments would have had this capability - obviously not!
VirtualBox is not VMWare. Just because VMWare has a certain feature (support fo 64-bit guest OSes) doesn't mean that VirtualBox has the same feature.

Another limitation of VirtualBox is that it supports only a single core in a VM. If you have a multi-core processor, then the OS in the VM will see only a single core. VMWare doesn't have that limitation.

---

