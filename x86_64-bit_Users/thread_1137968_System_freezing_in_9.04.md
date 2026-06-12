---
title: "System freezing in 9.04"
date: 2009-04-26
forum: x86 64-bit Users
---

### Post by beef623 on 2009-04-26
I just built a new system and I'm having trouble with it deadlocking in 9.04.

My system freezes without fail any time I try to install packages through the package manager. Sometimes I can get as far as actually starting the download for new packages, other times I can just be browsing the list. I can do system updates just fine, just no new stuff. It let me update the codecs for Amarok just fine(the little system tray notification). It also freezes randomly without trying to install anything. XP 64 runs without any trouble, as does the express gate os that's on the motherboard. OpenSuse 11.1 has the same freezing problem.

Any ideas?

System specs:
Intel Core i7 965
6Gb ram
Asus p6t deluxe v2 mobo
ATI Radeon 9250 (will be replaced by a Nvidia gtx 295 next week)

---

### Post by lowkey3d on 2009-04-26
I have the same issue with Studio. It's not X related related because I got it to hang down in recover mode commandline  using aptitude. It seems kernel/network related. What nic card are you running? I'm running a onboard Intel Pro/100 chipset

---

### Post by beef623 on 2009-04-26
I'm running an onboard nic as well, but mine is a Marvel Yukon. I dug through the message log in Kubuntu and Suse and it looks like my problem may be related to the video card I'm using right now. It was just an old ati card I had laying around, I should have my new one later this week. I'm going to hold off messing with it any more until my new card is in.

---

### Post by beef623 on 2009-04-30
I just put my new graphics card in and that appears to have fixed the problem. I haven't ran it very long yet, but so far everything works great. The sound works now too! I was messing with my freezing problem so much that I hadn't realized it wasn't working.

So Radeon 9250 + linux = bad

---

