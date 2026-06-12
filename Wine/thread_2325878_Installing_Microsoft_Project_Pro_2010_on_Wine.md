---
title: "Installing Microsoft Project Pro 2010 on Wine"
date: 2016-05-26
forum: Wine
---

### Post by alka5eltzer on 2016-05-26
Hi All,

Has anyone ever installed Project Pro 2010 using Wine?

I have Ubuntu 16.04... when I try to install it by clicking on the Setup file... its starts to install then crashes out.

Is there a step by step anywhere?

My 1st time using Wine so I'm not sure where I'm going wrong?

Thanks

---

### Post by grahammechanical on 2016-05-26
The first place to go is to 

[https://appdb.winehq.org/](https://appdb.winehq.org/)

And check out their database and see if anyone has rated that software. How are you trying to install it? Are you using the Wine application that installs Windows exe files. Simply double clicking setup.exe or install.exe will not work.

You need to launch a utility called Uninstall Wine Software. That will produce a Windows type add/remove dialog that will let you browse to the directory where the setup/install exe file is. There will also be an Install button in that dialog. From then on you should experience the usual Windows style program installation method.

Regards.

---

### Post by howefield on 2016-05-26
Thread moved to the "*Wine*" forum.

---

### Post by Mark Phelps on 2016-05-26
Installing practically any MS app in Wine involves additional work beyond just running the installer.

Here is a link to the WineHQ page for MS Project 2010 with additional actions needed:  [https://appdb.winehq.org/objectManager.php?sClass=version&iId=25397](https://appdb.winehq.org/objectManager.php?sClass=version&iId=25397)

Realize that this is for an old version of Ubuntu (2 years ago) and there are bugs associated with it, as well.

---

### Post by alka5eltzer on 2016-05-30
Thanks for your help guys... I've went ahead and installed a VM with windows 10, so I'm running Project 2013 on that and its 100%.

---

