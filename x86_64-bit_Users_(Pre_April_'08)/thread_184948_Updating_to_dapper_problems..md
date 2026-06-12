---
title: "Updating to dapper problems."
date: 2006-05-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by blurredbrain on 2006-05-30
I didn't know if this goes into Breezy Badger or the Dapper Drake forums but I was trying to upgrade to the recently released Dapper Drake LTS using the update manager.  I open the terminal type in **gksudo "update-manager -d"** and it opens up the update manager I click on the new version button it says its downloading two files at unknown speeds and then the update manager dies.  Here's the error I'm getting

(gksudo:26550): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
(update-manager:26552): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
/usr/lib/python2.4/site-packages/UpdateManager/MetaRelease.py:171: DeprecationWarning: Class MetaRelease is already GObject-registered; Please note that classes containing any of the attributes __gtype_name__, __gproperties__, or __gsignals__ are now automatically registered.
  gobject.type_register(MetaRelease)
extracting '/tmp/tmpUuMFTa/dapper.tar.gz'
authenticate '/tmp/tmpUuMFTa/dapper.tar.gz' against '/tmp/tmpUuMFTa/dapper.tar.gz.gpg'
/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)

(dapper:26552): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
Warning update-manager unsupported locale setting
can't find DistUpgradeViewGtk

---

### Post by barbarian on 2006-05-30
> I was trying to upgrade to the recently released Dapper Drake LTS using the update manager.

Dapper is not released yet, it will be released after official announcement, so, wait 2 days.

---

### Post by blurredbrain on 2006-06-12
I'm still getting the same problems.  Gah.  Any help at all out there?

---

### Post by mattlach on 2006-06-13
[QUOTE=blurredbrain]I'm still getting the same problems.  Gah.  Any help at all out there?[/QUOTE]

Me too.

If I run the upgrade manager I and select to upgrade it downloads the "upgrade tool" and when it completes it quits.

If I run GKSUDO the terminal states the following:

> 
matt@matt:~$ gksudo update-manager
  warnings.warn("apt API not stable yet", FutureWarning)
/usr/lib/python2.4/site-packages/UpdateManager/MetaRelease.py:171: DeprecationWarning: Class MetaRelease is already GObject-registered; Please note that classes containing any of the attributes __gtype_name__, __gproperties__, or __gsignals__ are now automatically registered.
  gobject.type_register(MetaRelease)
extracting '/tmp/tmpw5fQ_q/dapper.tar.gz'
authenticate '/tmp/tmpw5fQ_q/dapper.tar.gz' against '/tmp/tmpw5fQ_q/dapper.tar.gz.gpg'
/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
can't find DistUpgradeViewGtk


I'm thinking this can probably be solved by reinstalling whatever package "DistUpgradeViewGtk" is a part of, but I have no idea what that migh be.

Any ideas?

---

### Post by enered on 2006-10-02
If someone's getting the "can't find DistUpgradeViewGtk" problem when upgrading to edgy, try:

sudo aptitude install python-vte

Solved the problem for me...

---

