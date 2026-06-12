---
title: "Anyone had success with new ubuntu on nvraid using dmraid?"
date: 2007-05-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by arfett on 2007-05-06
I've recently attempted installing ubuntu 7.0.4 using drive D and E on my raptor raid-0 setup and dmraid allowed me to see the individual partitions, but when I attempted to format them and begin install it gave me an error and deleted all partitions so I had to repartition and install windows again.  Is anyone else able to install ubuntu 7.0.4 x64 on nvidia raid setups?

---

### Post by kuja on 2007-05-17
I've done it before, with Kubuntu 6.10. What error did you get? What partitioner did you use? If you have trouble with something like gparted, I recommend trying fdisk (yes, a cli app, so sue me), as it's what I used. For the most part I recommend following the **manual** method in the FakeRaidHowto (in the ubuntu wiki). I can't recall if there are additional steps I'd recommend throwing into that wiki, as I've not done it in forever, but it worked well for me.

---

### Post by sdhog2002 on 2007-10-27
Can I resurrect this question? I have dmraid working my Gutsy 32 bit nvraid perfectly. I cannot get dmraid to activate my RAID1 when I try the 64 bit install CD. (I get no response at all to dmraid -ay). Has anyone got it working?

---

