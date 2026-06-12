---
title: "&quot;arch: exit&quot;?"
date: 2006-03-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by phibxr on 2006-03-12
This should probably belong in the Dapper testing forums, but since the majority of their visitors seem to tend to be non-ppc folks I think the questions would be better suited here, since a search for the message seemed to indicate that the string only exists in PPC-code.

When I boot the Live and Installation CD:s of Dapper Flight 4 and 5, the initialization process stops with "arch: exit". Just to test if there was something wrong with the discs, I upgraded my Breezy via dist-upgrade to Flight 5, and now the computer refuses to boot, giving "arch: exit" and hard freezing.

The Installation CD for 5.10 still works perfectly, and so does OS X 10.4.

I'm using an iMac G4 700mhz.

---

It seems like strange things are up with this new kernel and PPC overall. Look at this bug: [https://launchpad.net/distros/ubuntu/+bug/34508](https://launchpad.net/distros/ubuntu/+bug/34508)

"The 2.6.15 kernel fails to boot on Dapper. The boot process appears to stop with the lines:

"loading ramdisk
Ramdisk loaded at 01900000, size: 4625 Kbytes"

When booted with "linux debug" at the yaboot prompt, the same thing happens, but the the added effect of the monitor turning off after the line "Ramdisk loaded at 01900000, size: 4625 Kbytes" is displayed.

Machine is a 2002 g4 imac (800 mhz)

[sidenote] This bug appears to be very similar to bug #183278 in the Fedora bug trackers. ([https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=183278](https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=183278)) Is this a problem in kernel main, or is it caused by a mutual patch between the two distros?[/sidenote]"

---

### Post by BoneKracker on 2006-03-12
I'm running dapper fine on G4 500 AGP by way of dist-upgrade (haven't attempted the flight cds).

---

