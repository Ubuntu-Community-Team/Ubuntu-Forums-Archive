---
title: "Airport Express driver trouble"
date: 2006-01-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by utnubu! on 2006-01-26
i am installing softmac (trying to get my airport express working) but when i enter the make command i get this error

make -C /lib/modules/`uname -r`/build SUBDIRS=`pwd`/net/ieee80211 CONFIG_IEEE80211=m CONFIG_IEEE80211_CRYPT_WEP=m CONFIG_IEEE80211_CRYPT_CCMP=m CONFIG_IEEE80211_CRYPT_TKIP=m CC="gcc -I`pwd`/include" modules
make: *** /lib/modules/2.6.15.1/build: No such file or directory. Stop.
make: *** [modules] Error 2

What shoud i do?

---

### Post by callipeo on 2006-01-26
Mayeb I'm wrong, but I think you should install the linux-headers-powerpc package.

---

### Post by dombleu on 2006-01-27
Get the whole kernel source anyway. It will be handy one day or another...

---

