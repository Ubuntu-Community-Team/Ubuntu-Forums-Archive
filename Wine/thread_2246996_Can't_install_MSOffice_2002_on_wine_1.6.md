---
title: "Can't install MSOffice 2002 on wine 1.6"
date: 2014-10-04
forum: Wine
---

### Post by ken18 on 2014-10-04
Trying to install a licensed copy of MSOffice 2002 using wine.  Under wine, I can launch the MSOffice installer, enter the license keys, pick the components to install, but the install aborts with the following error:

```
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory

```

I have a /usr/lib/i386-linux-gnu directory but no pkcs11 directory.  What should I do to resolve?

---

### Post by TheFu on 2014-10-05
Don't know, but winehq is the best resource that I know: [https://appdb.winehq.org/objectManager.php?sClass=version&iId=3514](https://appdb.winehq.org/objectManager.php?sClass=version&iId=3514)

---

### Post by ken18 on 2014-10-05
Thanks, I found the following (very disappointing):

```
**Office 2002/XP does not install due to bug 5163. This bug is unlikely to ever be fixed. ** 

The platinum test reports above are from users who had  slipstreamed, volume licensed installers that did not ask for a  registration key, 
and hence were not affected by bug 5163. Unless you have such a copy, you will not be able to install Office XP in Wine.
```

---

### Post by TheFu on 2014-10-05
Ouch. I've installed MS-Office into WINE from 1997 - 2007. Haven't done that in a while. Most things worked, but after 2007, teh "ribbon" drove me away to openoffice, then libreoffice when Oracle was less-than-nice.  Hopefully, libreoffice is an option for your needs. 

Or there is always virtualization if you have
* C2D or better CPU
* 2+G of RAM
* Windows-something license that isn't tied to the hardware (retail, not OEM)

---

### Post by ken18 on 2014-10-05
The trouble with virtualization is that the excel user files aren't exposed.  Already got burned because of that, so currently doing it the old fashioned way, which is dual boot to XP so I can use Excel.  Not worth it to me to purchase a newer version of Excel.  I may gradually migrate to LibreCalc, but not likely in the near term.

---

### Post by Vladlenin5000 on 2014-10-18
It may or may not work for your intended purpose but there's also WPS Office (former Kingsoft Office).
[http://wps-community.org/download.html](http://wps-community.org/download.html)

Obs.: Free as in "free beer" but closed source software.

---

