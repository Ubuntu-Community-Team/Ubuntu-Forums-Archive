---
title: "Bad crash on Feisty"
date: 2007-05-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by Nuro on 2007-05-15
Hi Everyone.

I have spent the last week looking for an answer on Google and this forum with no luck. I'm running Feisty (64 Bit) on my AMD Athlon 64 (Sempron 3500+), NForce 4 Mobo (Gigabyte GA-K8N51GMF, Integrated NVidia 6100, 1 Gig Ram. I'm also using the onboard LAN.

I can boot fine and  run X for some time, but then I get a bad crash that corrupts my display (yellow blocks all over display). The time seems to be random. I have run for 5 minutes to 5 hours before this happens.

I have sofar tried booting with noapic, running 32Bit Feisty with no luck. I have tried running X with the default NV driver, NVidia driver, and the VESA driver, and it crashes on all three. When I reset my machine, I get VGA error beeps from my motherboard, so I have to completely power down ,and back up. As a side note, this also happens with Mandriva 2007 spring. When I revert back to an old Ubuntu release, the problem goes away.

I though my hardware was stuffed, but what confuses me is that Windows XP runs fine for weeks on end with no crashes.

Any ideas?

Thanks

---

### Post by Nuro on 2007-05-15
Oh, forgot to mention: I get no errors before the crash in any of my logs, so I don't have much to post.

---

### Post by QwUo173Hy on 2007-05-26
Try disabling the onboard LAN from the BIOS and see how far you get. Also try disabling Network Manager once you log in. I have a similar problem to you and I think the LAN is the problem. These steps seem to have helped me. Please try this and let me know.

---

