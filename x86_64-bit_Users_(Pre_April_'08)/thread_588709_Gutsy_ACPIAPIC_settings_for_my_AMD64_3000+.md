---
title: "Gutsy ACPI/APIC settings for my AMD64 3000+"
date: 2007-10-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by ecowarrior on 2007-10-23
Hi all

I'm a very happy UBUNTU user now, having made the switch a couple of months ago.  No Vista for me!!!!

Most things work perfectly, and I'm now on Gutsy.  One thing that has never worked properly is power saving, and in this eco-in-danger world, I think I really should be able to get this working.

The problem, I think, is down to my requirement of adding:

noapic nolapic acpi=off

to the end of the kernel boot settings in grub.  If I don't have these, Ubuntu locks up either during boot up or a little while after.

Now I don't really know what each of the above settings do.  I just know that without them the system freezes.

Are there any other settings I could try that might solve the freezing issue while still allowing power-saving to work?

I have an AMD64 3000+ processor (socket 754) and I'm running a tuned vanilla 2.6.22.9 kernel (but the freezing problem has happened with any kernel I've tried) in the past, and happened with Feisty before.

Thanks

Eco

---

