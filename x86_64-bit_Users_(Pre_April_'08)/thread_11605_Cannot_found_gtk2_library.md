---
title: "Cannot found gtk2 library"
date: 2005-01-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by Gataca on 2005-01-18
I downloaded and installed sunbird GTK2-XFT enabled (calendar projet)  on my ubuntu amd64.

When I run sunbird , a error message appears 
```
user@machine:~ $ /usr/local/sunbird/sunbird
/usr/local/sunbird/sunbird-bin: error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory
user@machine:~ $

```

It seems that gtk2 library is not found although I can locate it in the /usr/lib/ directory.
```
user@machine:~ $ ll /usr/lib/libgtk-x11-2.0.so.0
lrwxrwxrwx  1 root root 25 2005-01-12 14:57 /usr/lib/libgtk-x11-2.0.so.0 -> libgtk-x11-2.0.so.0.600.1
user@machine:~ $
```

Any ideas how I can sort it out ?
-> how to define to sunbird that my gtk2 lib is located in the /usr/lib/ directory ?
-> may be my problem comes from the fact I downloaded a i686 version of sunbird ? (in this case where can I find an AMD64 version of sunbird ?)

downloaded file : sunbird-i686-linux-gtk2+xft.tar.gz

Thanks for your help.

---

### Post by Dylanby on 2005-01-18
"Sunbird" is in the repositories as "mozilla-calendar".
Apt should see it if you enable "universe".

---

