---
title: "failed installation of wine1.4 on ubuntu12.04"
date: 2013-02-27
forum: Wine
---

### Post by beanpoo on 2013-02-27
i am trying to root my android phone and in order to use the .exe programs i thought i'd try wine. 

when i go to install wine on the ubuntu software manager it comes back with this:

The following packages have unmet dependencies:

wine1.4: PreDepends: dpkg (>= 1.15.7.2~) but 1.16.1.2ubuntu7.1 is to be installed
         Depends: libc6 (>= 2.14) but 2.15-0ubuntu10.3 is to be installed
         Depends: wine1.4-amd64 (= 1.4.1-0ubuntu1~precise1~ppa4) but 1.4.1-0ubuntu1~precise1~ppa4 is to be installed
         Depends: wine1.4-i386 (= 1.4.1-0ubuntu1~precise1~ppa4) but it is a virtual package


when i go to install wine on the terminal it comes back with:

The following packages have unmet dependencies:
 wine1.4 : Depends: wine1.4-i386 (= 1.4.1-0ubuntu1~precise1~ppa4)
E: Unable to correct problems, you have held broken packages. 

i have also used the autoclean script as well as the -f script in order to try to resolve dependencies, as i thought that might be the first thing to try and work out. 

also after using the apt-get update script i am getting no errors.

>.< help would be appreciated 
macbean

---

