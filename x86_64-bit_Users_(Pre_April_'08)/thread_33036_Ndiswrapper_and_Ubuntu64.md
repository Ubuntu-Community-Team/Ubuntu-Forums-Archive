---
title: "Ndiswrapper and Ubuntu64"
date: 2005-05-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by Hagen Kaiser on 2005-05-09
Could it be ndiswrapper doesnt work?
I cant find it in Syanptic
I tried to download it and compile it.
But make deb 
tells me amd64 isnt supported.
Is there a way?

---

### Post by mthaddon on 2005-05-09
I just installed it from source: download the tgz from sourceforge, ([http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/))

tar -zxvf ndis...

change to the appropriate directory and then:

./configure
make
make install (as root/sudo).

Then follow the installation instructions to load your specific driver.

Worked for me.

---

### Post by BigCdaAnswer3 on 2005-05-25
if that didn't work for you like it didn't work for me, the guide at [http://www.ubuntulinux.org/wiki/HowtoUseNdiswrapperOnAmd64Ubuntu](http://www.ubuntulinux.org/wiki/HowtoUseNdiswrapperOnAmd64Ubuntu) worked beautifully for me

---

