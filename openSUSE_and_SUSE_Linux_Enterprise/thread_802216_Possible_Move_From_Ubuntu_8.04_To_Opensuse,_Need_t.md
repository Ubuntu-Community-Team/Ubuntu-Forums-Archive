---
title: "Possible Move From Ubuntu 8.04 To Opensuse, Need to know a few things."
date: 2008-05-21
forum: openSUSE and SUSE Linux Enterprise
---

### Post by chrispche on 2008-05-21
Hi all,

I have a few questions. I'm really considering moving to OpenSuse from Ubuntu. Not there's anything wrong with Ubuntu. I just fancy a change. Also OpenSuse came highly recommended by a work colleague who is a professional Linux user and programmer.

My questions are! In no particular order, can I do on OpenSuse what I do on Ubuntu.

1. Can I run Crossover Games?
2. Is it easy to run mp3s, divx and DVD's etc.
2. Do the repos contain mostly the stuff Ubuntu does. In this case Tux Paint and other educational programs for my daughter.
4. I take it you can burn CD's and DVD's just as you can on Ubuntu using K3B.
5. Is KDE 4 stable and can you use Compiz on it.
6. Can you use Compiz anyway.
7. Can you use Avant Window Manager in Gnome. (Although I'm probably going to migrate to KDE)
8. Does OpenSuse update it's self with all the latest security updates, aka ubuntu style.
9. What packages can I run on OpenSuse .deb files? .rpm files? I'm thinking of the new beta here.
10. When a new version of OpenSuse comes out can you upgrade or do you have to re-install, again aka ubuntu style.
11. How extensive is the repos in comparison to Ubuntu?
12. Is it easy to configure GL Screensavers and an nVidia G8400? Also for working with games on Crossover.

That's it for now. Can't think of any other questions.

Oh and, Also can I run VMware Server on it? Can you install Azureus on there, and DC++ for Linux? Sorry if these questions seem simple or n00b like. I have only ever know Ubuntu, would like to know how easy OpenSuse is.

I have the OpenSuse 11.0 Beta 2 disk.

Thanks in advance for any input.

---

### Post by RedDwarf on 2008-05-21
> **chrispche said:**
> 1. Can I run Crossover Games?
Sure.
> **chrispche said:**
> 2. Is it easy to run mp3s, divx and DVD's etc.
Judge yourself...
Official repos hadn't VLC or MPlayer, and the official gstreamer and libxine packages are stripped to not support mp3s, divx and DVD's etc.
VLC, MPlayer, and full gstreamer and libxine packages are available in a 3rd party repository: Packman. libdvdcss, needed for commercial DVDs, is available in the 3rd party VLC repository.
So you need to add two repos and install/substitute the packages you want from there. There are 1-Click links to do this.

That's easy? For me yes...

> **chrispche said:**
> 2. Do the repos contain mostly the stuff Ubuntu does. In this case Tux Paint and other educational programs for my daughter.
Last Tux Paint upstream version, 0.9.19, is available, yes. For other things search yourself:
[http://software.opensuse.org/search](http://software.opensuse.org/search)
[http://packman.links2linux.org/](http://packman.links2linux.org/)
[http://download.opensuse.org/repositories/Education:/desktop/openSUSE_10.3/repodata/](http://download.opensuse.org/repositories/Education:/desktop/openSUSE_10.3/repodata/)

> **chrispche said:**
> 4. I take it you can burn CD's and DVD's just as you can on Ubuntu using K3B.
Sure.

> **chrispche said:**
> 5. Is KDE 4 stable and can you use Compiz on it.
openSUSE KDE4 is the best you will get from KDE4... I will use 3.5.9 on 11.0, at least until KDE 4.1.
You can use compiz, but KDE4 has his own composite window manager.

> **chrispche said:**
> 6. Can you use Compiz anyway.
Sure.

> **chrispche said:**
> 7. Can you use Avant Window Manager in Gnome. (Although I'm probably going to migrate to KDE)
Sure.

> **chrispche said:**
> 8. Does OpenSuse update it's self with all the latest security updates, aka ubuntu style.
Sure. But the openSUSE 10.3 libzypp software management stack is less than perfect. Is bad enough for me to not use it.
11.0 version will be a lot better ( [http://duncan.mac-vicar.com/blog/](http://duncan.mac-vicar.com/blog/) ), but I still have to try it seriously.

> **chrispche said:**
> 9. What packages can I run on OpenSuse .deb files? .rpm files? I'm thinking of the new beta here.
openSUSE is a RPM based distro.

> **chrispche said:**
> 10. When a new version of OpenSuse comes out can you upgrade or do you have to re-install, again aka ubuntu style.
You can upgrade without re-install from the install CD. You can also upgrade from the running OS, but that's an unsupported way.

> **chrispche said:**
> 11. How extensive is the repos in comparison to Ubuntu?
Less extensive. But extensive enough and more updated.

> **chrispche said:**
> 12. Is it easy to configure GL Screensavers and an nVidia G8400? Also for working with games on Crossover.
Once again judge yourself...
nVidia creates and updates packages for openSUSE, you have to add his repository. After that you can use nVidia or openSUSE specific tools to configure that card.

> **chrispche said:**
> Oh and, Also can I run VMware Server on it? Can you install Azureus on there, and DC++ for Linux?
Sure.

---

