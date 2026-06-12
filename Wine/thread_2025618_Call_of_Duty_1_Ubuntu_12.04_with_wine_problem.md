---
title: "Call of Duty 1 Ubuntu 12.04 with wine problem"
date: 2012-07-14
forum: Wine
---

### Post by sudo smith on 2012-07-14
Ok so I have COD1 with a 2-disk installation process. I open setup.exe with Wine on the first cd and everything works fine. Halfway through the installation it asks me to put in disk 2. I put it in and click ok. It asks me the same prompt again and I click ok. It seems to be fine, but then it says ERROR: The file F:\Setup\Data\main\pak1.pak3 could not be opened. (attached is a screen shot). This is such a great game and it has Platinum rating according to wine appdb ([http://appdb.winehq.org/objectManager.php?sClass=application&iId=1346](http://appdb.winehq.org/objectManager.php?sClass=application&iId=1346)). Please anyone help. Thanks.

---

### Post by Kirk Schnable on 2012-07-15
Take a look at winecfg and make sure F:/ is mapped to the correct location, and make sure the file it wants is truly there. Seems like a logical starting point.  Good luck!

Kirk

---

### Post by sudo smith on 2012-07-15
> **Kirk Schnable said:**
> Take a look at winecfg and make sure F:/ is mapped to the correct location, and make sure the file it wants is truly there. Seems like a logical starting point.  Good luck!

Kirk

I'm sorry I'm very new to Ubuntu. Where should F:/ be mapped to? and I can't access the second cd files. It seems like it doesn't automatically load so I can't make sure that the file is actually there. Thanks for the reply.

---

