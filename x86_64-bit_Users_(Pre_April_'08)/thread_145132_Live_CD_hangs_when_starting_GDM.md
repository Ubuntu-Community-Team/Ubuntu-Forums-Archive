---
title: "Live CD hangs when starting GDM"
date: 2006-03-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by nickj6282 on 2006-03-15
Hello all,

I bought a new PC on Sunday and of course I went home and tried to boot up the 64-bit live CD to see how well Ubuntu works on the new system. At first it would hang early in hardware detection, so I changed the boot parameters:

```
live acpi=off noapic nolapic
```

With that, I can boot all the way up to where Gnome is supposed to start and then it just hangs there with a blank screen. I'm not sure where to go from here so any help is appreciated.

One idea I came up with was to resize Windows' NTFS partition and create a swap space on the HDD, would this make any sense or be a waste of time?

Thanks!
-Nick

System details:

-HP Pavilion dv8000
-AMD Turion 64 1.8Ghz CPU
-768MB DDR 333 (soon to be 1.25GB, but that probably won't make a difference here)
-Pioneer DVD/RW-DL
-Broadcom 802.11g MiniPCI Wifi card (will probably upgrade to IPW2200 or 2915 eventually, but hopefully the Broadcom works under Ubuntu)

Other system details on request, thanks in advance for any help!

---

### Post by joe_bruin on 2006-03-16
The one important detail you forgot to give us: your video card.  I'm guessing it a fairly new nvidia card (7800 or so).  The live CD hangs on some of these, because the open source "nv" driver isn't very good at dealing with these new cards (at least on AMD64).  If you'll search these forums, you'll find plenty of people having the same problem.  When doing an installation, the solution is to install the binary "nvidia" driver.  For a live CD, i'm not quite if it's fixable.

---

### Post by nickj6282 on 2006-03-16
It's 4am where I am and I'm far too sleepy to go check, but it is an ATI card in that machine. Radeon Mobility Express M200 or something like that if I recall. I'll double check during waking hours and post back if I'm wrong (about the model, it's most definitely an ATI card). That's what I get for falling asleep on the couch and stopping to check my email on the trip to my real bed ;)

---

### Post by nickj6282 on 2006-03-16
Ok, I tried all of the same, but I ran it with the debug options turned on (can't remember the exact commands) and got nothing. I'm going to try the expert install and just skip the modules that I don't need.

Oh, and BUMP ;)

-Nick

---

