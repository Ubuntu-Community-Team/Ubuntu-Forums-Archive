---
title: "AMD-64 smp kernel freeze"
date: 2005-04-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by bkgwatfiv on 2005-04-22
I am running a dual proc Xeon with the intel 64-bit procs.  I have tried various versions of the smp kernels with no success.  The machine locks up at boot--though everything is fine in default (non-smp) kernel.  My scan of old posts indicates that others have encountered this error--but no solution was mentioned.  Does anyone have ideas on this?  Perhaps I missed something in installing this--Is installing the smp kernel in synaptic enough or do other changes need to be made?

---

### Post by gomadtroll on 2005-04-29
Do you see any mesages when it freezes.  I have a smp box that does this, stops on IO/APIC, I edit my grub entry to include 'noapic' and it boots. Not sure if that is your problem but it is one item to check. Passing parameters during boot may isolate the issue.

greg

---

### Post by bkgwatfiv on 2005-05-02
Actually, I did try this and was able to get it to boot, but it froze soon afterwards.  It seems that maybe others have had this problem--it must be something with smp kernel integration.  Thanks.
BG

---

