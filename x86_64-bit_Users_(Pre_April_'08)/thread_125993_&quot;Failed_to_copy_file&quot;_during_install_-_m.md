---
title: "&quot;Failed to copy file&quot; during install - many tries"
date: 2006-02-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by doon41 on 2006-02-05
I am trying to install Ubuntu for first time. Config:
AMD Athlon 64 3700+
Asus A8N-SLI Motherboard
ATI Radeon X300 (on PCI-Express bus)
1GB RAM non-ECC, no overclocking
LSI 20320R SCSI controller, 4 U320 drives
WDC 740GD SATA drive on motherboard controller
Sony DRU-810A DVD/CD multi-format 

Problem: While loading the "busy beaver" 5.10 CD, it gets about 20% in and says "failed to copy file".  This is in the "loading installer components" step.  Of course, I suspected bad media, bad burn, whatever.

So I have downloaded the Install CD, the Live CD, four times.  Used both Nero and DeepBurner to make bootable CDs.  All combinations lead to this same loading error. 

Any advice?  Can I download a better/newer install CD somewhere?  Is a safe mode, text based install possible? (how?)

I am now trying download of the install CD again on a completely different machine.

(Oh yeh, Win XP Pro x64 runs just fine. :-( .  I have also had various, weird install problems with SuSE 9.3 and 10.0.  Fedora at least installs, but crashed after the first kernel update.  Various diagnostics run just fine, as expected.  System is 2 mo. old.  Win XP is rock solid. )

TIA and may the Highest Powers bless Linux.

---

### Post by cdhotfire on 2006-02-05
Try running the install with "noapic acpi=off", thats what happened to me before.

So when you pop in the cd and it comes to the Ubuntu screen, type in F1 and look for the command to run different options, I think it was "setup noapic acpi=off", but I dont remember.  If anyone knows it please feel free to post it. :)

---

