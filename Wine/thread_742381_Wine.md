---
title: "Wine"
date: 2008-04-01
forum: Wine
---

### Post by phoronixy on 2008-04-01
Hello,

is it possible to have multiple installs of different versions of Wine on one machine? I'm using Ubuntu Hardy Heron. I've installed the most current release of Wine from the repositories and like to install Wine 0.47 additionally to a different path to prevent collisions because of an application that requires this version.

Thanks in advance for your help.

Best regards,
Phoronixy

---

### Post by Oldsoldier2003 on 2008-04-02
> **phoronixy said:**
> Hello,

is it possible to have multiple installs of different versions of Wine on one machine? I'm using Ubuntu Hardy Heron. I've installed the most current release of Wine from the repositories and like to install Wine 0.47 additionally to a different path to prevent collisions because of an application that requires this version.

Thanks in advance for your help.

Best regards,
Phoronixy

yes it is possible to run different versions of wine. you need to use the command [wineprefixcreat]("http://wiki.winehq.org/wineprefixcreate")e to setup the different versions.

here is a good read about wine and it has a section on using wineprefixcreate : [http://gaming.gwos.org/doku.php/wine:winestuff#special_configuration_stuff](http://gaming.gwos.org/doku.php/wine:winestuff#special_configuration_stuff)

---

### Post by Lord Illidan on 2008-04-02
> **Oldsoldier2003 said:**
> yes it is possible to run different versions of wine. you need to use the command [wineprefixcreat]("http://wiki.winehq.org/wineprefixcreate")e to setup the different versions.

here is a good read about wine and it has a section on using wineprefixcreate : [http://gaming.gwos.org/doku.php/wine:winestuff#special_configuration_stuff](http://gaming.gwos.org/doku.php/wine:winestuff#special_configuration_stuff)


I'm not a wine guru, but you're still not using different versions of wine with wineprefixcreate..

As in, you can't have wine0.5.8 and wine 0.4.6 installed at the same time on the computer, and still referred to by the command wine.

Unless you install them in their own directories and not under a system wide installation, of course.

---

### Post by Oldsoldier2003 on 2008-04-02
> **Lord Illidan said:**
> I'm not a wine guru, but you're still not using different versions of wine with wineprefixcreate..

As in, you can't have wine0.5.8 and wine 0.4.6 installed at the same time on the computer, and still referred to by the command wine.

Unless you install them in their own directories and not under a system wide installation, of course.

thats exactly what you do. In order to use multiple versions of wine they need to be separately installed (in different paths- meaning you'll have to compile). there is also a neat little utility called [winestart]("http://www.david-guembel.de/index.php?id=13") that is helpful if you run multiple versions of wine.

---

### Post by Hairy_Palms on 2008-04-03
i ran two versions for a while i had 0.9.47 in /usr/local because versions after that had a nasty bnet bug that wasnt fixed for 3-4 versions you dont have to compile, just download the deb for the version you want and extract it and once changed to how you want just rebuild it with 
dpkg-deb -b

---

### Post by YokoZar on 2008-04-03
What is the application that you think needs 0.9.47?  A regression that old should have been fixed by now.

---

