---
title: "ntfs-3g 20061115 and fuse 2.6.0 amd64 packages"
date: 2006-11-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by raptor_ on 2006-11-23
hi, i created the deb packages for the lastest avaiable ntfs-3g beta drivers and fuse.

although ntfs-3g is really stable you shoud consider that it's still [COLOR="Red"]BETA[/COLOR]

the fuse pkg was created with --enable-kernel-module parameter to create new fuse module kernel.

there are the [COLOR="Red"]links[/COLOR]:

[http://nod84.interfree.it/fuse_2.6.0-1_amd64.deb](http://nod84.interfree.it/fuse_2.6.0-1_amd64.deb)
[http://nod84.interfree.it/ntfs-3g_0.20061115-1_amd64.deb](http://nod84.interfree.it/ntfs-3g_0.20061115-1_amd64.deb)


to [COLOR="Red"]install[/COLOR] open a terminal session and type:

sudo dpkg -i ntfs-3g_0.20061115-1_amd64.deb

sudo dpkg -i --force-overwrite fuse_2.6.0-1_amd64.deb





to [COLOR="Red"]autoload[/COLOR] fuse module at startup add a line with "fuse" into /etc/modules




more informations on ntfs-3g,fuse and their installation can be found here:

[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)
[http://ntfs-3g.org](http://ntfs-3g.org)
[http://fuse.sourceforge.net/](http://fuse.sourceforge.net/)

---

