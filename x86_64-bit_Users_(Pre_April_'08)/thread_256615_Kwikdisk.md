---
title: "Kwikdisk"
date: 2006-09-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by DaveQB on 2006-09-13
I have never had this problem before, so might not be a 64bit issue.

Kwikdisk and kdiskfree both wont start; crash on start-up.

kwikdisk outputs this 

```

kwikdisk: [DiskList::DiskList(QObject*, const char*)]
kwikdisk: df gives no FS_TYPE
kwikdisk: [void DiskList::loadSettings()]
kwikdisk: [KwikDisk::KwikDisk()]
kwikdisk: [void KwikDisk::loadSettings()]
kwikdisk: [void KwikDisk::setUpdateFrequency(int)]
kwikdisk: [void KwikDisk::updateDF()]
kwikdisk: [int DiskList::readFSTAB()]
kwikdisk: [void DiskList::loadSettings()]
kwikdisk: [int DiskList::readDF()]
kwikdisk: [void DiskList::dfDone()]
Error running df command... got [(null)]
KCrash: crashing... crashRecursionCounter = 2
KCrash: Application Name = kwikdisk path = <unknown> pid = 943



```

kwikdisk: df gives no FS_TYPE
and
Error running df command... got [(null)]

seem to be the key problems...

---

### Post by kuja on 2006-09-13
Well, it could still potentially be a 64-bit issue, but the fact that it "works-for-me" sheds some doubt on that.

---

