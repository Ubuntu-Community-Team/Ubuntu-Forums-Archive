---
title: "Boot Failure"
date: 2007-06-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by baileyone82 on 2007-06-03
Hello,

I have installed Ubuntu 6.10, Edgy Eft, and have been using happily for a few months now. When I built the machine, I had 4 SATA hard drives. I went ahead and installed on the first one and the other three were just sitting there unused the whole time.

I decided it was time to use them, so I cranked up gpartd and partitioned/formatted them (using ext3). I mounted them successfully using the mount command. Everything was going well, so I followed some directions to edit /etc/fstab so they would mount automatically at startup.

When I rebooted, nothing happened after BIOS. I figured that my /etc/fstab changes must have messed something up, so I used the install CD to mount the first primary hd and I put the original /etc/fstab back. But still nothing. When I tried to start the computer, I get nothing after BIOS. It just sits there.

Any ideas what I messed up or how to fix it? Thanks!

---

### Post by david_2001 on 2007-06-03
My first thought would be to check BIOS settings for the SATA interface.  Formatting those three other drives may have confused the BIOS into thinking that you now have a RAID.  For example, the BIOS in my system defaults to RAID for SATA drives - I have two and they are not set up as a RAID - and it will not boot unless the RAID functionality is disabled.

---

### Post by baileyone82 on 2007-06-04
Thanks - that was a great idea. My motherboard has two software raid controllers.

Unfortunately, I double-checked and both are disabled. I am not getting an error message from BIOS about invalid boot disk - it is simply frozen after listing out a bunch of items/addresses. I think the last one it spits out is ACPI 9.

Any other good ideas?

---

### Post by david_2001 on 2007-06-04
> **baileyone82 said:**
> Thanks - that was a great idea. My motherboard has two software raid controllers.

Unfortunately, I double-checked and both are disabled. I am not getting an error message from BIOS about invalid boot disk - it is simply frozen after listing out a bunch of items/addresses. I think the last one it spits out is ACPI 9.

Any other good ideas?
Even though there is a lack of an invalid boot disk message, I would still want to check that:
[LIST=1]
[*]The disk with Ubuntu installed is connected to the primary SATA connector of the first SATA controller on the motherboard.
[*]This drive is selected in BIOS as the first hard disk boot device.
[/LIST]
EDIT: "ACPI 9" is probably just information about the IRQ assigned to the acpi service.
EDIT: Try also resetting the BIOS, i.e. by selecting the load optimized defaults, or whatever it might be called, option.  (Check that the SATA interfaces aren't set to RAID afterwards.)

---

