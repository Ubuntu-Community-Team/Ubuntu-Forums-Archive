---
title: "Seamless Virtualization Between Ubuntu Gutsy and Windows Vista Ultimate"
date: 2008-02-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by lancerocke on 2008-02-14
I haven't seen any tutorials on this.
Was wondering if someone could point me in the right direction.
All I found was outdated XP and Feisty threads.

Thanks for any help in advance.

---

### Post by gsmanners on 2008-02-14
I think Ubuntu is shifting toward KVM these days.

[https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM)

---

### Post by lancerocke on 2008-02-14
> **gsmanners said:**
> I think Ubuntu is shifting toward KVM these days.

[https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM)
Very cool.
Thanks.
That's a lot to read into tonight.
So this KVM is seemless out the box?

---

### Post by gsmanners on 2008-02-15
I haven't used it in a while, but it worked darn good for testing other Linux distros. I can't say for sure what Vista is like in a VM.

I think it's fairly safe to say that as long as you don't need 3D or a lot of CD activity, it's should perform well.

---

### Post by VMan on 2008-02-16
Just for fun (OK, I live a very boring life:lolflag:), I put Windows Vista into a VMware virtual machine.  I dedicated 1G of RAM and tried to get the installation into the smallest disk space possible.  For the OS, I used VMware converter and converted an existing Vista installation into a virtual machine.  The smallest amount of disk space I was able to use was well over 15G!  The virtual machine ran very slowly.  It also slowed the hose (Ubuntu 7.10 64bit) down so much my laptop was almost unusable when Vista was running.  This is the same machine that can run three different virtual machines with XP at the same time.  I copied the virtual machine setup off onto a backup disk and haven't touched it since.  Vista just hogged too much in the way of machine resources for it to be a viable OS in this setup.

---

### Post by Marshalus on 2008-02-16
Vista does not virtualize well at all. Even using Microsoft Virtual PC in Windows it runs like a dog.

---

### Post by stmiller on 2008-02-17
I run Vista in virtualbox. I turned off ALL effects, changed the theme to classic windows, turned off system restore, and so forth. It looks like XP and runs faster. Also I disabled UAC, and it boots 10 times faster after that, strangely enough.

It's a weird beast, but you can turn a lot of the crap off.

---

