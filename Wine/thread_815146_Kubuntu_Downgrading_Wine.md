---
title: "Kubuntu Downgrading Wine"
date: 2008-06-01
forum: Wine
---

### Post by SarcasmMonster on 2008-06-01
How do I downgrade wine to version 0.9.46 in Kubuntu? When I was using Ubuntu, it was fairly simple with synaptic. Clue in a nub :confused:

---

### Post by DoktorSeven on 2008-06-01
You can just go grab Synaptic again and use it:

**sudo apt-get install synaptic**

---

### Post by SarcasmMonster on 2008-06-01
Thanks for the solution, nice and elegant (I'm such a dope). But the problem is that the lowest version is 0.9.59 which isn't the version i want :(

---

### Post by mc4man on 2008-06-01
that was part of the development repo. long gone. if you had had it installed you may be able to force the version back or find it in /var/cache/apt/archives (not on a kubuntu install atm- may be something similar but named different)
otherwise here are 2 posted .debs
[http://nerdymark.com/hardy-wine-0.9.56-deb](http://nerdymark.com/hardy-wine-0.9.56-deb)
[http://files.filefront.com/wine+0956+1+i386deb/;9690336;/fileinfo.html](http://files.filefront.com/wine+0956+1+i386deb/;9690336;/fileinfo.html)
 note; I believe both were built with checkinstall (you may lose some of the wine menu ) and will install to usr/local 
otherwise the source is still available if you want to build
[https://launchpad.net/ubuntu/hardy/+source/wine/0.9.56-0ubuntu1](https://launchpad.net/ubuntu/hardy/+source/wine/0.9.56-0ubuntu1)  or
[http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=77449](http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=77449)

---

