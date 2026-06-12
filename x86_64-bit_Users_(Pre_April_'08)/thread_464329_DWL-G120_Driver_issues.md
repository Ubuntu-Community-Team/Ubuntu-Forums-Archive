---
title: "DWL-G120 Driver issues"
date: 2007-06-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by Idura on 2007-06-04
I'm running 64-bit Feisty Fawn ubuntu. Once I have the driver installed and type in

```
sudo dmesg
```

I get an error something like this, "32-bit driver installed, 64-bit kernel, Bad Magic8050"

I'm a linux noob, **d****o I need to install a 32-bit version of linux in order to get my DWL-G120 adapter to work since there  is no 64-bit drivers for it**? I Google'd for some 64-bit drivers, but have found nothing at all.

---

### Post by Ken_Lewis81 on 2007-06-06
The googling I did showed that they're Prism-based and that efforts have begun to get a driver together.  The NDISWrapper driver may be needed.  Anyone else have experience of that on AMD64?  (I'm fighting with rt2500/mac80211 in Gutsy's 2.6.22 kernel...)

[http://prism54.org/newdrivers.html](http://prism54.org/newdrivers.html)
[http://jbnote.free.fr/](http://jbnote.free.fr/)

This was the Google search I used (and you're right, there's so little about this that this thread is fifth...):
[http://www.google.co.uk/search?q=DWL-G120+linux+driver](http://www.google.co.uk/search?q=DWL-G120+linux+driver)

Take care.
Ken.

---

