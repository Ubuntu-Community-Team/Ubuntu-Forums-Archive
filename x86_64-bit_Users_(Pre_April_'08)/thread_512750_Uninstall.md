---
title: "Uninstall"
date: 2007-07-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by timoschenko on 2007-07-29
Hi,

how can I reinstall a package apt-get tells me should be reinstalled before it can be uninstalled, but is in such a mess it can't be reinstalled? As long as I don't solve this, I can't apply any udates.

Thanks

---

### Post by Circuit99 on 2007-07-29
There is basically two ways of installing which are synaptic or open terminal and use apt-get.

Synaptic is a Gui way of apt-get.

Find Synaptic Package Manager in System>Administration>Synaptic Package Manager

OR 

Terminal in Applications>Accessories>Terminal


I would use in Terminal

```
sudo apt-get update
```

(You'll be asked for password same as login)

```
sudo apt-get upgrade

```
This will update your system.

To add package just 

sudo apt-get install "package name"

For more information found at this link scroll down section on Ubuntu Updates 


[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

---

### Post by Kilz on 2007-07-29
You can also try and fix the package database. This will remove packages that are broken.
```
sudo apt-get install -f
```

---

### Post by timoschenko on 2007-07-30
Hi,

thanks. The package apt-get wants me to reinstall is a .deb I made using alien from a rpm. I downloaded from the Internet.Doing "sudo dpkg --remove" gives "Package is in a very bad inconsistent state - you should reinstall it before attempting a removal." Trouble is, I can't reinstall it. "sudo dpkg -C" gives the following: "The following packages are in a mess due to serious problems during installation.  They must be reinstalled for them (and any packages that depend on them) to function properly:" "sudo dpkg -s" gives "Status: deinstall reinstreq half-installed
Priority: extra
Section: alien
Architecture: amd64"
What can I do?

---

### Post by kuja on 2007-07-30
What I would do would be to create a more or less empty deb package with the same name and a higher version number and try to install it ... it could work

---

