---
title: "Cannot find wine config file"
date: 2017-06-09
forum: Wine
---

### Post by theredwarrior on 2017-06-09
When I downloaded wine through the software center, it was an outdated version of wine. It had a configuration file though that came in the form of an application. I upgraded to the stable 2.01 build and I can't seem to find a config file anywhere. 
Thanks for the help,
                             A relatively new Ubuntu user

---

### Post by howefield on 2017-06-09
Thread moved to the "*Wine*" forum.

---

### Post by sccman on 2017-07-07
Wine moved away from a configuration file since [June 2005]("https://www.winehq.org/docs/wineusr-guide/config-wine-main#USING-WINECFG") and uses an emulated Windows registry instead.

You can configure Wine using the command **winecfg** on 2.01.

---

