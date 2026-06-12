---
title: "Problem Installing Wine"
date: 2007-12-08
forum: Wine
---

### Post by t3h_h4ck3r on 2007-12-08
I have the .deb installer on my linux machine. It does not have internet. I am using a flashdrive to transfer all of the information. When I ran the file this popped up... help!!? 


[IMG]http://img135.imageshack.us/img135/2585/screenshotrp0.png[/IMG]

---

### Post by ruibernardo on 2007-12-08
Hi t3h_h4ck3r,

because you don't have an internet connection, you have to download and install the dependencies of that package. The package installer (gdebi) should say what the dependencies are. Then download them and install them. You can easily find the package files you need to download using [http://nonetdebs.homeip.net](http://nonetdebs.homeip.net).

To not spam you with it, I can tell you that for a fresh install of Ubuntu 7.10 Gutsy Desktop on a not PPC/amd64 computer (the normal i386 generic kernel - type "uname -a" on a terminal to verify) you have to download the following packages:[INDENT][http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine_0.9.50~winehq0~ubuntu~7.10-1_i386.deb]("http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine_0.9.50%7Ewinehq0%7Eubuntu%7E7.10-1_i386.deb")
[http://archive.ubuntu.com/ubuntu/pool/universe/b/binfmt-support/binfmt-support_1.2.10_all.deb](http://archive.ubuntu.com/ubuntu/pool/universe/b/binfmt-support/binfmt-support_1.2.10_all.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/n/nas/libaudio2_1.9-2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/n/nas/libaudio2_1.9-2_i386.deb)
[/INDENT]For other packages or architectures, check my signature.

Cheers.

---

