---
title: "Java under swiftfox 64BIT"
date: 2006-07-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by McMarley on 2006-07-30
Hey to all

I just got Dapper=P~  and i installed Java and then later macromadia:D , and by intalling the second, Java just refuses to wark at all:( . has anyone had this problem before:confused: 
:!: :!: I need help bad:!: :!:

---

### Post by jamesford on 2006-07-30
this worked for me:
-------------
sudo wget -c [http://ubuntu.mirrors.tds.net/ubuntu/pool/multiverse/j/j2se1.4-i586/j2re1.4_1.4.2.02-1ubuntu3_i386.deb](http://ubuntu.mirrors.tds.net/ubuntu/pool/multiverse/j/j2se1.4-i586/j2re1.4_1.4.2.02-1ubuntu3_i386.deb)
sudo dpkg --force-architecture -i j2re1.4_1.4.2.02-1ubuntu3_i386.deb
sudo ln -s /usr/lib/j2se/1.4/jre/plugin/i386/mozilla/libjavaplugin_oji.so /PATH/TO/swiftfox/plugins
--------------------

---

### Post by McMarley on 2006-07-30
I did the first 2, but it said that i have no such directory when i tried the third

---

### Post by jamesford on 2006-07-30
```
sudo wget -c http://ubuntu.mirrors.tds.net/ubuntu/pool/multiverse/j/j2se1.4-i586/j2re1.4_1.4.2.02-1ubuntu3_i386.deb
sudo dpkg --force-architecture -i j2re1.4_1.4.2.02-1ubuntu3_i386.deb
sudo ln -s /usr/lib/j2se/1.4/jre/plugin/i386/mozilla/libjavaplugin_oji.so /PATH/TO/swiftfox/plugins
```

try this, the forum cut off the url a bit

---

### Post by McMarley on 2006-07-30
hey

I fidled around a bit with the first comands, it had  some file that bothered it, but everything is working now
thank you so much, it is so nice having y browser working now
you saved the day, well at least mine

---

