---
title: "Can I replace Wine with older version?"
date: 2011-07-27
forum: Wine
---

### Post by xhepera on 2011-07-27
Can someone point me to instructions, if such exist, on how to go back to an earlier version of Wine?
Can someone point me to instructions, if such exist, on how to go back to an earlier version of Wine?

I have had World of Warcraft installed for some time and it worked well. I allowed an automatic update from Wine 1.2 to 1.3 and (although it may be a coincidence) have not been able to play because of massive graphics distortion. I can play the cinematics just fine, but even the opening/login screen of WoW is completely hosed.

This problem started after an update. It may not be due to Wine at all, but I'd like to revert, if possible, just to test and make sure.

In case anyone is wondering, the computer is a laptop (HP 8510p).
Specs are:
CPU: Intel Core2 Duo T7300 2 GHz
2 GB RAM
Ubuntu 10.04 lucid
linux 2.6.32-33
ATI Radeon HD2600

I'd be really grateful for help in reverting. Thanks!
I have had World of Warcraft installed for some time and it worked well. I allowed an automatic update from Wine 1.2 to 1.3 and (although it may be a coincidence) have not been able to play because of massive graphics distortion. I can play the cinematics just fine, but even the opening/login screen of WoW is completely hosed.

This problem started after an update. It may not be due to Wine at all, but I'd like to revert, if possible, just to test and make sure.

In case anyone is wondering, the computer is a laptop (HP 8510p).
Specs are:
CPU: Intel Core2 Duo T7300 2 GHz
2 GB RAM
Ubuntu 10.04 lucid
linux 2.6.32-33
ATI Radeon HD2600

I'd be really grateful for help in reverting. Thanks!

---

### Post by lkjoel on 2011-07-28
> **xhepera said:**
> Can someone point me to instructions, if such exist, on how to go back to an earlier version of Wine?
Can someone point me to instructions, if such exist, on how to go back to an earlier version of Wine?

I have had World of Warcraft installed for some time and it worked well. I allowed an automatic update from Wine 1.2 to 1.3 and (although it may be a coincidence) have not been able to play because of massive graphics distortion. I can play the cinematics just fine, but even the opening/login screen of WoW is completely hosed.

This problem started after an update. It may not be due to Wine at all, but I'd like to revert, if possible, just to test and make sure.

In case anyone is wondering, the computer is a laptop (HP 8510p).
Specs are:
CPU: Intel Core2 Duo T7300 2 GHz
2 GB RAM
Ubuntu 10.04 lucid
linux 2.6.32-33
ATI Radeon HD2600

I'd be really grateful for help in reverting. Thanks!
I have had World of Warcraft installed for some time and it worked well. I allowed an automatic update from Wine 1.2 to 1.3 and (although it may be a coincidence) have not been able to play because of massive graphics distortion. I can play the cinematics just fine, but even the opening/login screen of WoW is completely hosed.

This problem started after an update. It may not be due to Wine at all, but I'd like to revert, if possible, just to test and make sure.

In case anyone is wondering, the computer is a laptop (HP 8510p).
Specs are:
CPU: Intel Core2 Duo T7300 2 GHz
2 GB RAM
Ubuntu 10.04 lucid
linux 2.6.32-33
ATI Radeon HD2600

I'd be really grateful for help in reverting. Thanks!
Try this into a Terminal window:
```
sudo apt-get purge wine1.3
sudo apt-get install wine1.2
```

---

### Post by xhepera on 2011-07-31
> **lkjoel said:**
> Try this into a Terminal window:
```
sudo apt-get purge wine1.3
sudo apt-get install wine1.2
```

Thank you very much. I did that and it is, indeed, at the earlier version. It stopped one graphics glitch but the rest is still there and it's unplayable. I'll post in the WoW-related forum. Thanks again!

---

### Post by thecolorifix on 2011-11-13
Thanks for this info. I searched when Wine 1.3 uninstalled LMMS and this was the top result.

---

