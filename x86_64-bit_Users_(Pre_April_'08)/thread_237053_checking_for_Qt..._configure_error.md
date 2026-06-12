---
title: "checking for Qt... configure: error"
date: 2006-08-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by janhenderson on 2006-08-15
I'm trying to compile Kat. I had the same problem with Knights. Everything goes well until 


checking for Qt... configure: error: Qt (>= Qt 3.3 and < 4.0) (headers and libraries) not found. Please check your installation!
For more details about this problem, look at the end of config.log.


Any ideas? Thanks.

---

### Post by kuja on 2006-08-15
Try install the kde-devel package, if you haven't already.
```
sudo apt-get install kde-devel
```

---

### Post by janhenderson on 2006-08-15
> **kuja said:**
> Try install the kde-devel package, if you haven't already.
```
sudo apt-get install kde-devel
```

Hi. That worked quite well for Kat, it compiled and installed. I still get the same problem though when I try that with Knights 

checking for Qt... configure: error: Qt (>= Qt 3.0) (headers and libraries) not found. Please check your installation!

I see that the knights installations says I should tell it where KDE is installed, [http://www.knights-chess.com/install.php](http://www.knights-chess.com/install.php)

How do I find out where it is installed? I installed ubuntu then I installed kubuntu-desktop from apt-get. 

Thanks.

---

### Post by kuja on 2006-08-15
Hm, do you have any specific reason why you're compiling it instead of just installing the package from the repository? It should be in Ubuntu's universe repository. If this is an option, try ```
sudo apt-get install knights
```

If you insist on building the package, try running ```
sudo apt-get build-dep knights
``` Also, try setting $QTDIR=/usr/lib/qt3

---

