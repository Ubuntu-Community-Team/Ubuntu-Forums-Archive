---
title: "jdk-6u12-linux-x64.bin installation-there mus be an easy way."
date: 2009-03-04
forum: x86 64-bit Users
---

### Post by hoboy on 2009-03-04
I have download jdk-6u12-linux-x64.bin and was interested to install it but it, is there an easy to do this ? I have googled but....

---

### Post by ahbart on 2009-03-04
What do you mean by easy?

```
Remove all current java files you might have by :

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
```
Source: [link](http://ubuntuforums.org/showthread.php?t=1080431) and here: [link](http://ubuntuforums.org/showthread.php?t=1063635)

---

