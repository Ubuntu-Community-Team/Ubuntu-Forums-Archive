---
title: "Where do I install the java file jre-6u12-linux-x64.bin"
date: 2009-02-25
forum: x86 64-bit Users
---

### Post by philinux on 2009-02-25
Tried /usr/java and firefox doesn't pick it up.

---

### Post by howefield on 2009-02-25
I took these instructions from a previous poster, so apologies, can't give credit.

> Remove all current java files you might have by :

sudo su
apt-get -y purge icedtea6-plugin
rm -f /usr/lib/firefox-addons/plugins/libnpjp2.so
rm -f /usr/lib/firefox-addons/plugins/libjavaplugin_oji.so
rm -f /usr/lib/mozilla/plugins/libnpjp2.so
rm -f /usr/lib/mozilla/plugins/libjavaplugin_oji.so

Download the latest version of java RE here. move it to to /opt and install:

mv ~/Desktop/jre-6u12-linux-x64.bin /opt/
cd /opt/
sh jre-6u12-linux-x64.bin

after installing link the plugin to your firefox plugin directory.

cd /usr/lib/mozilla/plugins
ln -s /opt/jre1.6.0_12/lib/amd64/libnpjp2.so

---

### Post by philinux on 2009-02-25
Sorted now thanks.

---

