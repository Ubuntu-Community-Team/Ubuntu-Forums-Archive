---
title: "Outlook (DNS Host File?)"
date: 2008-09-02
forum: Wine
---

### Post by Aysah on 2008-09-02
so after a couple of days of surfing the net I finally installed Outlook via Crossover and even had it working in WINE.  I felt it was more stable in Crossover but I've kind of hit a brick wall at the moment.

In order to connect to our company exchange for whatever reason, the host file needs to be edited no matter what computer you are on.  It is located in: "c:\windows\system32\drivers\etc\" and then I add:

10.160.2.13    TBSHK-EXCH01.intranet.***.com


How do I emulate this in either wine or crossover so outlook knows 10.160.2.13 is TBSHK-EXCH01.intranet.***.com?  It seems this is my only obstacle at the moment.

---

