---
title: "Make yourself a backport with a single command"
date: 2008-02-27
forum: openSUSE and SUSE Linux Enterprise
---

### Post by RedDwarf on 2008-02-27
openSUSE doesn't updates software versions (sometimes does if there are security fixes). If openSUSE 10.3 was released with xmoto 0.3.2 that will be the available version forever, even if upstream xmoto is at version 0.4.1.
In some cases, like this one, the openSUSE Build Service has unsupported* updates (xmoto is available in games:arcade), but sometimes there are no updates at all.
mkvtoolnix is a good example. Last upstream version is 2.1.0, openSUSE Factory (the development version) has the last version... but openSUSE 10.3 was released with mkvtoolnix 2.0.2 and it will not be never updated. There isn't any update for mkvtoolnix avalable in the openSUSE Build Service, so what can you do?
- First
Go to [https://build.opensuse.org/](https://build.opensuse.org/) and open a openSUSE Build Service account. Here you can create RPM packages for software not packaged in openSUSE (you can also create packages for other distros).
- Second
Install package "osc"
- Third
Even if you don't know how to create a RPM. Just execute
> osc linkpac "openSUSE:Factory" mkvtoolnix "home:<yourUserName>"
This way you will create a backport from the mkvtoolnix Factory package to openSUSE 10.3 (or previous versions). This package will not be available just to you, anyone that search mkvtoolnix in [http://software.opensuse.org/search](http://software.opensuse.org/search) will find your backport.
If openSUSE Factory updates to mkvtoolnix 2.1.1 your backport will be also updated automatically. And if you add your home repository the updated packages will be installed automatically in the next update with your favorite package manager.

So you can have a backport of any package available in openSUSE Factory.


* There is no "official" support, so you can't complain if something fails. But it doesn't fails, and when does you can report bugs and they are fixed, don't worry.

---

