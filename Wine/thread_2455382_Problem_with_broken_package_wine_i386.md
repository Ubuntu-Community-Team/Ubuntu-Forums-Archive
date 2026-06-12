---
title: "Problem with broken package wine i386"
date: 2020-12-18
forum: Wine
---

### Post by levalsac on 2020-12-18
Hi Guys,

I hope you can help me with this problem.
I got the following notification in the package manager on Ubuntu 20.04

-------
Broken dependencies    Package -> wine:i386     Installed Version -> 1:16.5-0ubuntu14   Description -> Microsoft Windows Compatibiliity Layer (meta-package)
--------

And then I tried to update and upgrade my system but there is an error

------
You might want to run 'apt --fix-broken install' to correct these
The following packages have unmet dependencies:
wine:i386 : Depends: wine1.6:i386
-----

I tried the suggested command but there are some errors at the output

```
-----
Do you want to continue? [Y/n] 
(Reading database ... 304384 files and directories currently installed.)
Preparing to unpack .../wine1.6-i386_1%3a1.6.2-0ubuntu14_i386.deb ...
Unpacking wine1.6-i386:i386 (1:1.6.2-0ubuntu14) ...
dpkg: error processing archive /var/cache/apt/archives/wine1.6-i386_1%3a1.6.2-0u
buntu14_i386.deb (--unpack):
 trying to overwrite '/usr/lib/i386-linux-gnu/wine/jscript.dll.so', which is als
o in package libwine:i386 5.0-3ubuntu1
dpkg-deb: error: paste subprocess was killed by signal (Broken pipe)
YPreparing to unpack .../wine1.6_1%3a1.6.2-0ubuntu14_i386.deb ...
Unpacking wine1.6:i386 (1:1.6.2-0ubuntu14) ...
dpkg: error processing archive /var/cache/apt/archives/wine1.6_1%3a1.6.2-0ubuntu
14_i386.deb (--unpack):
 trying to overwrite '/usr/share/wine/fonts/wingding.ttf', which is also in pack
age fonts-wine 5.0-3ubuntu1
dpkg-deb: error: paste subprocess was killed by signal (Broken pipe)
Preparing to unpack .../libp11-kit-gnome-keyring_3.18.3-0ubuntu2_i386.deb ...
Unpacking libp11-kit-gnome-keyring:i386 (3.18.3-0ubuntu2) ...
dpkg: error processing archive /var/cache/apt/archives/libp11-kit-gnome-keyring_
3.18.3-0ubuntu2_i386.deb (--unpack):
 trying to overwrite '/usr/share/p11-kit/modules/gnome-keyring.module', which is
 also in package gnome-keyring-pkcs11:amd64 3.36.0-1ubuntu1
Preparing to unpack .../libpng12-0_1.2.54-1ubuntu1_i386.deb ...
Unpacking libpng12-0:i386 (1.2.54-1ubuntu1) ...
dpkg: error processing archive /var/cache/apt/archives/libpng12-0_1.2.54-1ubuntu
1_i386.deb (--unpack):
 unable to install new version of '/usr/lib/i386-linux-gnu/libpng12.so.0': No su
ch file or directory
No apport report written because MaxReports is reached already
                                                              Errors were encoun
tered while processing:
 /var/cache/apt/archives/wine1.6-i386_1%3a1.6.2-0ubuntu14_i386.deb
 /var/cache/apt/archives/wine1.6_1%3a1.6.2-0ubuntu14_i386.deb
 /var/cache/apt/archives/libp11-kit-gnome-keyring_3.18.3-0ubuntu2_i386.deb
 /var/cache/apt/archives/libpng12-0_1.2.54-1ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
-----
```

---

### Post by deadflowr on 2020-12-19
Ubuntu's developers have removed most 32-bit packages from the archives of recent releases.
Holding onto a select few (a comparably select few)
See this thread about which packages are supported and how you might make request for additional packages to make the list:
[https://discourse.ubuntu.com/t/community-process-for-32-bit-compatibility/12598/1]("https://discourse.ubuntu.com/t/community-process-for-32-bit-compatibility/12598/1")

---

