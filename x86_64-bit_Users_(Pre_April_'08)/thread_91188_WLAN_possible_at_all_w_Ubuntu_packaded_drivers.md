---
title: "WLAN possible at all w/ Ubuntu packaded drivers?"
date: 2005-11-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by blazko on 2005-11-16
Hello all,

I have a Ralink (rt2500) PCI WLAN card and an USB ZD1211 WLAN adapter. Both work pretty out of the box (REALLY PNP after givin the WEP key! That was great!) on my 32bit box.

On my AMD64 X2 (dual core), none of these work. No matter what I try, as soon as entering the properties page of network-admin or as soon as doing an iup ra0 or wlan0 (after having done a minimal entry in /etc/network/interfaces), the sys completely freezes. So both adapters do not work on breezy 64 (SMP Kernel) but like a charm on the 32bit boxen (Athlon XP 2600).

Some idea?

Thanks and regards, Timo

---

### Post by SleepyHollow on 2005-11-17
[QUOTE=blazko]Hello all,

I have a Ralink (rt2500) PCI WLAN card and an USB ZD1211 WLAN adapter. Both work pretty out of the box (REALLY PNP after givin the WEP key! That was great!) on my 32bit box.

On my AMD64 X2 (dual core), none of these work. No matter what I try, as soon as entering the properties page of network-admin or as soon as doing an iup ra0 or wlan0 (after having done a minimal entry in /etc/network/interfaces), the sys completely freezes. So both adapters do not work on breezy 64 (SMP Kernel) but like a charm on the 32bit boxen (Athlon XP 2600).
[/QUOTE]

My Ralink rt2500 works out of the box under Breezy 64 AMD-generic. :smile:

---

