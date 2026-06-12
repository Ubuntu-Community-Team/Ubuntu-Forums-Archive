---
title: "Blizzard updater hanging in Wine"
date: 2013-08-02
forum: Wine
---

### Post by dmonk2 on 2013-08-02
Hello all and thank you for any help up front.

I have downloaded the Blizzard installer but it keeps hanging during trying to update itself.  I am on Ubuntu 13.04 and using WINE from the software catalogue which is version wine 1.4.1.4.1-0ubuntu5.

Please see below

```
fixme:iphlpapi:GetExtendedTcpTable ulAf = 2, TableClass = 5 not supportted
fixme:process:GetLogicalProcessorInformation (0x131e318,0x131e918): stub
fixme:process:GetLogicalProcessorInformation (0xdee314,0xdee914): stub
fixme:process:GetLogicalProcessorInformation (0xdee2e4,0xdee8e4): stub
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
```

is there any advice out there for this?  I have also tried in PlayonLinux and it hangs as well

Br,
DMonk

---

### Post by Doomspark on 2013-08-06
Have you checked the Wine AppDB?  There's a lot of good information there.

---

### Post by Toz on 2013-08-06
*Moved to the **Wine** subforum.*

---

### Post by LinXNut on 2013-08-06
I have read that in the 1.4 version of wine, the launch screen downloader may APPEAR to be hung. However, some have said if you wait it completes the download.... You may want to upgrade wine version to 1.6. I have created a guide to do so here: [http://ubuntuforums.org/showthread.php?t=2165833](http://ubuntuforums.org/showthread.php?t=2165833)

Hope this helps!! (:

---

