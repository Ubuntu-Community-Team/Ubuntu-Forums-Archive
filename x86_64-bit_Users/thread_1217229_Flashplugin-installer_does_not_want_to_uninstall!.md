---
title: "Flashplugin-installer does not want to uninstall!"
date: 2009-07-19
forum: x86 64-bit Users
---

### Post by tjeremiah on 2009-07-19
Its driving me crazy. It was recommended that I uninstall flashplugin-nonfree before I install the 64bit version of flash. While doing so, the normal flashplugin-nonfree uninstalls fine, the problem is, flashplugin-installer does not want to uninstall (this had to be removed along with nonfree). It is now a error, no matter what I try to install, the flashplugin-installer error pops up. If I try to reinstall, I get an error. How do I get rid of this thing or make it error free once again?

---

### Post by tjeremiah on 2009-07-19
Also, I get this:```
blacksnake@vaio-notebook:~$ sudo apt-get remove flashplugin-nonfree nspluginwrapper
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flashplugin-nonfree is not installed, so not removed
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.30-8 linux-headers-2.6.31-2 linux-headers-2.6.31-2-generic
  linux-headers-2.6.30-8-generic
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  flashplugin-installer nspluginwrapper
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 741kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 155925 files and directories currently installed.)
Removing flashplugin-installer ...
update-alternatives: error: no alternatives for iceape-flashplugin.
update-alternatives: error: no alternatives for iceape-flashplugin.
dpkg: error processing flashplugin-installer (--remove):
 subprocess installed pre-removal script returned error exit status 2
postinst called with argument `abort-remove'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Removing nspluginwrapper ...
Processing triggers for man-db ...
Errors were encountered while processing:
 flashplugin-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

```
blacksnake@vaio-notebook:~$ sudo apt-get remove flashplugin-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.30-8 linux-headers-2.6.31-2 linux-headers-2.6.31-2-generic
  linux-headers-2.6.30-8-generic
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  flashplugin-installer
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 180kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 155899 files and directories currently installed.)
Removing flashplugin-installer ...
update-alternatives: error: no alternatives for iceape-flashplugin.
update-alternatives: error: no alternatives for iceape-flashplugin.
dpkg: error processing flashplugin-installer (--remove):
 subprocess installed pre-removal script returned error exit status 2
postinst called with argument `abort-remove'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 flashplugin-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
blacksnake@vaio-notebook:~$ 

```

---

### Post by wojox on 2009-07-19
You may need to manually remove the old on in ~/.mozilla/plugins/

```
rm ~/.mozilla/plugins/libflashplayer.so
```

---

### Post by tjeremiah on 2009-07-19
> **wojox said:**
> You may need to manually remove the old on in ~/.mozilla/plugins/

```
rm ~/.mozilla/plugins/libflashplayer.so
```

no matter what I do, I still get an error for flashplugin-installer

---

### Post by Anubis on 2009-07-19
apt-get -f install

READ your output it tells you EXACTLY what is wrong.


The following packages will be REMOVED:
  flashplugin-installer nspluginwrapper
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
[SIZE="5"]1 not fully installed or removed.[/SIZE]

---

### Post by Yellow Pasque on 2009-07-19
Suggestion:
```
sudo update-alternatives --remove-all iceape-flashplugin
```
The you should be able to remove flashplugin-installer.

---

### Post by gekkio on 2009-07-22
I've had the same problem on all my Karmic installations and it seems that you too are using Karmic.

There's a relevant bug report at launchpad: [https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/398042]("https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/398042")

Or if you just want a quick fix for the problem, just run
```
wget http://launchpadlibrarian.net/29383483/flash.patch -O- | sudo patch /var/lib/dpkg/info/flashplugin-installer.prerm
```

and then remove the package normally.

---

### Post by Preach08 on 2009-10-29
> **gekkio said:**
> I've had the same problem on all my Karmic installations and it seems that you too are using Karmic.

There's a relevant bug report at launchpad: [https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/398042]("https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/398042")

Or if you just want a quick fix for the problem, just run
```
wget http://launchpadlibrarian.net/29383483/flash.patch -O- | sudo patch /var/lib/dpkg/info/flashplugin-installer.prerm
```

and then remove the package normally.

Thanks, that worked.

---

