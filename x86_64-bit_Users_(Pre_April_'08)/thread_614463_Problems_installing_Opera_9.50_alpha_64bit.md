---
title: "Problems installing Opera 9.50 alpha 64bit"
date: 2007-11-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by azenz on 2007-11-16
When trying to install the new 64 bit version of Opera (9.50 alpha) I get this error:

dpkg: dependency problems prevent configuration of opera:
 opera depends on libqt3-mt (>= 3:3.2.1); however:
  Package libqt3-mt is not configured yet.

However, I have libqt3-mt installed, version: 3:3.3.8. Does anyone have any ideas?

---

### Post by Cappy on 2007-11-16
Try
```
sudo dpkg --configure libqt3-mt
```
in the terminal and post the output back on the forums if it doesn't solve the problem.

---

### Post by azenz on 2007-11-16
It worked! Thanks!

---

### Post by t_anjan on 2007-11-16
U can get the 64 bit version of Opera 9.5 beta 2 from here:
[http://snapshot.opera.com/unix/snapshot-1662/x86_64-linux/opera_9.50-20071109.2-shared-qt_amd64.deb](http://snapshot.opera.com/unix/snapshot-1662/x86_64-linux/opera_9.50-20071109.2-shared-qt_amd64.deb)

---

### Post by John Jason Jordan on 2007-11-16
> **t_anjan said:**
> U can get the 64 bit version of Opera 9.5 beta 2 from here:
[http://snapshot.opera.com/unix/snapshot-1662/x86_64-linux/opera_9.50-20071109.2-shared-qt_amd64.deb](http://snapshot.opera.com/unix/snapshot-1662/x86_64-linux/opera_9.50-20071109.2-shared-qt_amd64.deb)
I want to wait until it is final. I looked all over opera.com but couldn't find a hint of when 64-bit Opera might be final. I realize vendors of proprietary software hate stating a definite date for fear that someone will be upset if they don't make it. But a general statement or a statement like "our goal is to ..." would be nice.

---

### Post by matiz on 2007-11-16
After install it, please at the next line to /usr/bin/opera at the very first line:

export QT_IM_MODULE=XIM

It prevent the confiliction of scim input method with other software.

---

### Post by Ehtetur on 2007-11-17
> **t_anjan said:**
> U can get the 64 bit version of Opera 9.5 beta 2 from here:
[http://snapshot.opera.com/unix/snapshot-1662/x86_64-linux/opera_9.50-20071109.2-shared-qt_amd64.deb](http://snapshot.opera.com/unix/snapshot-1662/x86_64-linux/opera_9.50-20071109.2-shared-qt_amd64.deb)

Thanks... you read my mind!

---

