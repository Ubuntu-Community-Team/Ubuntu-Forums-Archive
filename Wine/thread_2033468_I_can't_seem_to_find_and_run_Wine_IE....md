---
title: "I can't seem to find and run Wine IE..."
date: 2012-07-26
forum: Wine
---

### Post by codingman on 2012-07-26
I remember seeing somewhere  that there was a wine internet explorer on my system, but I can't find it... If anybody has a terminal command for it that would be nice.

---

### Post by mc4man on 2012-07-26
Not sure how well IE works but on 64 bit install this would start - 
 ```
wine '.wine/drive_c/Program Files (x86)/Internet Explorer/iexplore.exe'
```

on either a 32 bit or 64 bit install probably this
 ```
wine '.wine/drive_c/Program Files/Internet Explorer/iexplore.exe'
```

(just browse in home folder > .wine > ect, ect. to find

---

### Post by TheFu on 2012-07-26
> **codingman said:**
> I remember seeing somewhere  that there was a wine internet explorer on my system, but I can't find it... If anybody has a terminal command for it that would be nice.

Normally WINE programs get put under a WINE/Programs/ menu.
If you want IE installed since it isn't in your current WINE environment, the winhq.com is filled with how-to instructions. [http://appdb.winehq.org/objectManager.php?sClass=application&iId=25](http://appdb.winehq.org/objectManager.php?sClass=application&iId=25)

---

### Post by ajgreeny on 2012-07-26
I think that if you want to use the integral version of IE, you will need to install wine1.3-gecko, which has the following description in package properties
> This package includes the Gecko rendering engine from the Mozilla project for
displaying web pages in Wine's fake Internet Explorer.

I have never used it so can not tell you how well, or even if it works properly.  Even going back to my windows days I never used IE, so I certainly see no possible reason to start now.

---

### Post by Mark Phelps on 2012-07-26
Not a user of Wine, but from what I recall, the version installed by default with it is IE version 6 -- which is so old that MS is trying to do away with it.  I believe, that if you go to the Wine section, you can find out how to install newer versions -- but those stop at 7 or 8, not 9.

---

### Post by oldos2er on 2012-07-26
Moved to Wine.

---

