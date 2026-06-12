---
title: "New and Lost"
date: 2006-01-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by Stevenony on 2006-01-25
Hello, I am new to Linux and only marginally computer literate.  I have a Acer Aspire 5002 laptop and I have succesfully loaded Ubuntu with the exception of I CANT GET MY WIRELESS TO WORK.  I have a Ti PCI-1410 card and a Broadcom 802.11g network adapter.  Ubuntu doesnt recognize the wireless at all.  Please help me if you can.  
Thank You,
Stevenon[-o< y

---

### Post by Dr. Nick on 2006-01-25
[quote=Stevenony]Hello, I am new to Linux and only marginally computer literate.  I have a Acer Aspire 5002 laptop and I have succesfully loaded Ubuntu with the exception of I CANT GET MY WIRELESS TO WORK.  I have a Ti PCI-1410 card and a Broadcom 802.11g network adapter.  Ubuntu doesnt recognize the wireless at all.  Please help me if you can.  
Thank You,
Stevenon[-o< y[/quote] 

Since you posted in the 64bit forum I assume you are using ubuntu 64bit and not 32. If linux does not have native drivers for your wireless card which appears to be the case for you, then you need to use ndiswrapper, but if you have the 64bit ubuntu then you need 64bit windows drivers to use with ndiswrapper, which are rare since windows hasnt really gone 64bit yet, and odds are your laptop came preloaded with 32bit xp whose drivers wont work with 64bit ubuntu. I hate to say it, but if you must use ndiswrapper then you are most likely better off using the 32bit ubuntu, then search forums for ndiswrapper instructions for your card

---

