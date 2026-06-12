---
title: "Another Hardy 64 bootchart request"
date: 2008-08-04
forum: x86 64-bit Users
---

### Post by Mugzilla on 2008-08-04
I've been googling this to death, and haven't found an answer.  Attached is my bootchart.  If requested, I can post the dmesg output.  As you can see, I appear to be getting a few decent hangups.

Here are the DMESG lines of interest:

The first:
[    0.000000] TSC calibrated against PM_TIMER
[   23.719676] Marking TSC unstable due to TSCs unsynchronized

The 2nd:

[   28.331726] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   29.815000] ata1: classification failed
[   29.815004] ata1: reset failed (errno=-22), retrying in 9 secs
[   39.813631] ata1: classification failed
[   39.813634] ata1: reset failed (errno=-22), retrying in 9 secs
[   49.812263] ata1: classification failed
[   49.812265] ata1: reset failed (errno=-22), retrying in 34 secs
[   83.159700] ata1: limiting SATA link speed to 1.5 Gbps
[   83.799610] ata1: classfication failed, assuming ATA
[   83.799614] ata1: SATA link up <unknown> (SStatus 103 SControl 310)
[  113.795508] ata1.00: qc timeout (cmd 0xec)
[  113.795512] ata1.00: failed to IDENTIFY (I/O error, err_mask=0x4)
[  113.795515] ata1: failed to recover some devices, retrying in 5 secs
[  119.438732] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)



Specs: (I can get more specific if needed...)
AMD X2 5000
MSI k9n sli
evga 8800gts
4 gig ram
SATA HD



I am uncertain where to go from here.  The goal is to speed up the boot time, and increase my knowledge of my new found primary OS.

---

### Post by porchrat on 2008-08-04
I'm having a similar problem.

Don't get any crashes although I seem to be getting a heck of a lot of pagefaults and I think this might be the cause.

```
TSC calibrated against HPET
Marking TSC unstable due to TSCs unsynchronized
```

Pagefaults happen with an in-house piece of java software that was running fine on an older Gentoo system.

Hopefully someone out there has an answer or at least some suggestions.

---

### Post by Mugzilla on 2008-08-04
Why don't you run the bootchart for your startup also?  It might help others to diagnose the issues....

---

