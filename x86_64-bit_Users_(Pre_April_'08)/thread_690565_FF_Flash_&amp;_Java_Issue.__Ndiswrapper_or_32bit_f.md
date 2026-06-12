---
title: "FF Flash &amp; Java Issue.  Ndiswrapper or 32bit fix?"
date: 2008-02-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by FooAtari on 2008-02-07
So I just upgraded from 32-Bit Kubuntu to 64-bit Ubuntu with out realising the Firefox issues.

It looks like Java and Flash are still problematic.  I've seen both common fixes, installing 38bit firefox or using ndiswrapper.  Are these the only fixes?  And if so which is the best.  Are the any disadvantages to using one over the other?

Thanks

---

### Post by jrib on 2008-02-08
See [https://help.ubuntu.com/community/FirefoxAMD64FlashJava](https://help.ubuntu.com/community/FirefoxAMD64FlashJava) .

nspluginwrapper only allows you to run 32bit flash in your 64bit browser.  You won't be able to run sun's java plugin.  Your best chance then is to use blackdown's java (older version).  Sun doesn't care.  The bug on their tracker is several years old.

Your other option (also on the wiki) is to run 32bit firefox with all the plugins.  You can run flash, java, etc...

---

### Post by FooAtari on 2008-02-08
Would appear using the 32bit Firefox is the better solution then.

thanks

---

