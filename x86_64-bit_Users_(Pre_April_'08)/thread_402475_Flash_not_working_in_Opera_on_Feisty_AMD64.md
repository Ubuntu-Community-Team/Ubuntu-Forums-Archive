---
title: "Flash not working in Opera on Feisty AMD64"
date: 2007-04-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by Anthelion on 2007-04-05
I'm running Feisty on AMD64, and I cannot get Opera to recognize the flash plugin. I have tried both the 9.10 and 9.20 beta with the same results.

I copied both flashplayer.xpt and libflashplayer.so to /usr/lib/opera/plugins and made sure the directory was enabled in Opera's plug-in paths. I also tried enabling /usr/lib/firefox/plugins and copying the files there. I even added the original directory to which I unzipped the plugin files to Opera's plugin paths. No matter what I do, Opera is unable to find the plugins when I click "find new."

How can I get Opera to detect the files?

---

### Post by sharke on 2007-04-05
Take a look here.[http://ubuntuforums.org/showthread.php?t=191205](http://ubuntuforums.org/showthread.php?t=191205)
Regards
Sharke

---

### Post by Colonel Kilkenny on 2007-04-06
> **Anthelion said:**
> I'm running Feisty on AMD64, and I cannot get Opera to recognize the flash plugin. I have tried both the 9.10 and 9.20 beta with the same results.

I copied both flashplayer.xpt and libflashplayer.so to /usr/lib/opera/plugins and made sure the directory was enabled in Opera's plug-in paths. I also tried enabling /usr/lib/firefox/plugins and copying the files there. I even added the original directory to which I unzipped the plugin files to Opera's plugin paths. No matter what I do, Opera is unable to find the plugins when I click "find new."

How can I get Opera to detect the files?

That sounds quite strange. Opera should recognize normal flash plugin without any problems. If you have libflashplayer.so in a directory which is one of the dirs Opera searches plugins from, you could try to start opera with "operan -debugplugin" and see if it says something.

---

### Post by Anthelion on 2007-04-06
Thanks, "opera -debugplugin" detected it right away. I'm not sure why this would work over the normal method, but I now have flash, so I'm happy!

---

