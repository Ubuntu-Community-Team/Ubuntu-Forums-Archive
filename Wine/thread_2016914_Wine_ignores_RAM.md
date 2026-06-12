---
title: "Wine ignores RAM"
date: 2012-07-04
forum: Wine
---

### Post by CrimsonMagi on 2012-07-04
So as the title says, wine is ignoring my RAM. This is only tested in world of warcraft because I really don't have anything else to test, but i have 5 gigs of ram,all working fine for other applicaitons. Any ideas/suggestion? Thanks for reading

---

### Post by Zookey500 on 2012-07-05
Hi,
Sorry, I'm not quite understanding what you mean? Could you post a screenshot?
Also, does the game work?

If it doesn't it may not work with wine currently. You should check winehq for any issues with the game working under wine.

If it does not work under wine, you may want to look at virtualisation under virtualbox. However, if it can run virtualisation , depends on what speed your processor is. 

Best regards,
Matthew

---

### Post by Elfy on 2012-07-05
*Thread moved to **Wine**.*

---

### Post by Martin Marshalek on 2012-07-09
Well, this is just a guess, but I assume that you mean that wine, and by extension WoW is not seeing all 5GB? If that's the case, it's because wine is mainly a 32bit compatability layer (with preliminary support for 64 bit Windows programs) and WoW is probably a 32bit program. Even though you may be using a 64bit system, 32bit wine apps like WoW can only make use of up to 4GB of ram.

---

### Post by Grenage on 2012-07-09
It's worth mentioning that there is a 64-bit WoW client available; there has been for a while!

---

