---
title: "npviewer.bin"
date: 2008-11-29
forum: x86 64-bit Users
---

### Post by wfp on 2008-11-29
Wondering if anyone else has problems still with flash. I still get firefox freezing from time to time, and have found out that npviewer.bin has been the culprit. Was wondering if there is anything else i can do. I am running hardy with all the latest updates and flash 10. Each time that firefox has locked up i have been able to open a terminal with npviewer.bin using 100 %Cpu.

---

### Post by Yashiro on 2008-11-29
Kill the bugged npviewer processes. Usually works.

Go back to Flash 9 from the repository.

Or Uninstall gnash, swfdec, flashplugin-nonfree, nspluginwrapper etc
and try the new 64bit Flash Plugin. [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

---

### Post by bford16 on 2008-11-30
The link above is for an Alpha of a working 64-bit verision of flashplayer 10.  It does seem to work, however.  I would expect a release version to appear fairly quickly, as demand is high.

---

### Post by xebian on 2008-11-30
> **bford16 said:**
> The link above is for an Alpha of a working 64-bit verision of flashplayer 10.  It does seem to work, however.  I would expect a release version to appear fairly quickly, as demand is high.

It maybe alpha but it's working as good as a release, and way much better than the 64-bit wrapper workaround.

---

### Post by steveneddy on 2008-11-30
> **xebian said:**
> It maybe alpha but it's working as good as a release, and way much better than the 64-bit wrapper workaround.

agreed

---

### Post by ushimitsudoki on 2008-12-02
Yeah, better than the old workaround. I've only had one time in a couple of weeks where npviewer.bin got out of control and I had to kill it.

Before, with the wrapper, it would happen every day or so.

Far from perfect, but still a great improvement.

---

