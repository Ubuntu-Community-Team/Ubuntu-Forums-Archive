---
title: "Is there something wrong with my WINE install?"
date: 2012-04-19
forum: Wine
---

### Post by venom104 on 2012-04-19
Okay here is the story. I compiled wine 1.5 with the directions from here [http://appdb.winehq.org/objectManager.php?sClass=version&iId=25022](http://appdb.winehq.org/objectManager.php?sClass=version&iId=25022) . I HAD to install a patch to get SWTOR to work.

The "problem" I'm having with wine is that last month something weird started happening. Almost (yes, ALMOST) every time I open up an application, the winecfg popup says "updating your wine configuration" and I have to wait like 10 seconds to for it to end, then the application loads fine.

Wine was not doing this before...is this normal? If not, how can I fix it?

---

### Post by nothingspecial on 2012-04-19
*Thread moved to **Wine**.*

---

### Post by cogadh on 2012-04-19
Your configuration should usually only update when you install a new version of Wine, however, I have seen that kind of behavior when running multiple versions of Wine on the same system and not using multiple Wine prefixes; the configuration will get updated each time you switch between Wine versions. Do you use multiple versions of Wine, like your custom compiled version for TOR and the "normal" Wine for everything else?

---

### Post by venom104 on 2012-04-20
> **cogadh said:**
> Your configuration should usually only update when you install a new version of Wine, however, I have seen that kind of behavior when running multiple versions of Wine on the same system and not using multiple Wine prefixes; the configuration will get updated each time you switch between Wine versions. Do you use multiple versions of Wine, like your custom compiled version for TOR and the "normal" Wine for everything else?

Thanks for the reply...actually NO, I don't believe I am running multiple versions of wine...I did a sudo apt-get purge wine, and uninstalled wine that way before I compiled it. Also, I'm not updating wine either. 

What should I do?

---

### Post by venom104 on 2012-04-21
/bump

---

