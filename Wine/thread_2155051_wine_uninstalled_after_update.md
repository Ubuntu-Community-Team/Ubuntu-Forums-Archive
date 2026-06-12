---
title: "wine uninstalled after update"
date: 2013-06-16
forum: Wine
---

### Post by Synoc on 2013-06-16
I updated my 12/04 machine and wine completely uninstalled itself, it seems. and trying to re-install tells me the package system is broken. any idea what happened here? I don't knwo what information it you need. it says it was a distribution upgrade. if that helps and it was only a partial upgrade.

---

### Post by Cheesehead on 2013-06-16
Your package manager sessions are saved to to logs: /var/log/apt/term.log and /var/log/apt/history.log
Each session is timestamped, for your convenience.

Open the files using gedit or any text editor (not word processor).
Find the relevant session in each file.
Copy-and-paste them here. Remember to use CODE tags.

---

### Post by Synoc on 2013-06-17
var/log/apt/term.log
```

Selecting previously unselected package unixodbc.
Unpacking unixodbc (from .../unixodbc_2.2.14p2-5ubuntu3_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Errors were encountered while processing:
 /var/cache/apt/archives/wine1.6_1.6~rc2-0ubuntu1~ppa1_amd64.deb
Log ended: 2013-06-16  23:08:00


Log started: 2013-06-16  23:08:33
(Reading database ... 412805 files and directories currently installed.)
Unpacking wine1.6 (from .../wine1.6_1.6~rc2-0ubuntu1~ppa1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/wine1.6_1.6~rc2-0ubuntu1~ppa1_amd64.deb (--unpack):
 trying to overwrite '/usr/bin/wine64-preloader', which is also in package wine1.6-amd64 1.6~rc2-0ubuntu1~ppa1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/wine1.6_1.6~rc2-0ubuntu1~ppa1_amd64.deb
Log ended: 2013-06-16  23:08:35


Log started: 2013-06-16  23:09:18
(Reading database ... 412805 files and directories currently installed.)
Unpacking wine1.6 (from .../wine1.6_1.6~rc2-0ubuntu1~ppa1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/wine1.6_1.6~rc2-0ubuntu1~ppa1_amd64.deb (--unpack):
 trying to overwrite '/usr/bin/wine64-preloader', which is also in package wine1.6-amd64 1.6~rc2-0ubuntu1~ppa1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/wine1.6_1.6~rc2-0ubuntu1~ppa1_amd64.deb
Log ended: 2013-06-16  23:09:19

```

var/log/apt/history.log
```

Start-Date: 2013-06-16  23:07:03
Commandline: apt-get install wine1.6
Install: libopenal1:i386 (1.13-4ubuntu3, automatic), wine1.6-amd64:amd64 (1.6~rc2-0ubuntu1~ppa1, automatic), libpam-winbind:amd64 (3.6.3-2ubuntu2.6, automatic), libldap-2.4-2:i386 (2.4.28-1.1ubuntu4.2, automatic), libv4l-0:i386 (0.8.6-1ubuntu2, automatic), libroken18-heimdal:i386 (1.6~git20120311.dfsg.1-2, automatic), libgphoto2-port0:i386 (2.4.13-1ubuntu1.2, automatic), wine1.6:amd64 (1.6~rc2-0ubuntu1~ppa1), libsane:i386 (1.0.22-7ubuntu1, automatic), libasn1-8-heimdal:i386 (1.6~git20120311.dfsg.1-2, automatic), libxslt1.1:i386 (1.1.26-8ubuntu1.3, automatic), libcapi20-3:amd64 (3.12.20071127-0ubuntu11, automatic), libcapi20-3:i386 (3.12.20071127-0ubuntu11, automatic), libgssapi3-heimdal:i386 (1.6~git20120311.dfsg.1-2, automatic), libv4lconvert0:i386 (0.8.6-1ubuntu2, automatic), unixodbc:amd64 (2.2.14p2-5ubuntu3, automatic), libwind0-heimdal:i386 (1.6~git20120311.dfsg.1-2, automatic), libosmesa6:i386 (8.0.4-0ubuntu0.5, automatic), libgif4:i386 (4.1.6-9ubuntu1, automatic), libieee1284-3:i386 (0.2.11-10build1, automatic), libxpm4:i386 (3.5.9-4, automatic), libusb-0.1-4:i386 (0.1.12-20, automatic), libhcrypto4-heimdal:i386 (1.6~git20120311.dfsg.1-2, automatic), wine1.6-i386:i386 (1.6~rc2-0ubuntu1~ppa1, automatic), libhx509-5-heimdal:i386 (1.6~git20120311.dfsg.1-2, automatic), libgd2-xpm:i386 (2.0.36~rc1~dfsg-6ubuntu2, automatic), libheimbase1-heimdal:i386 (1.6~git20120311.dfsg.1-2, automatic), libmpg123-0:i386 (1.12.1-3.2ubuntu1, automatic), libsasl2-2:i386 (2.1.25.dfsg1-3ubuntu0.1, automatic), libheimntlm0-heimdal:i386 (1.6~git20120311.dfsg.1-2, automatic), winbind:amd64 (3.6.3-2ubuntu2.6, automatic), libodbc1:amd64 (2.2.14p2-5ubuntu3, automatic), libexif12:i386 (0.6.20-2ubuntu0.1, automatic), libglu1-mesa:i386 (8.0.4-0ubuntu0.5, automatic), libsasl2-modules:i386 (2.1.25.dfsg1-3ubuntu0.1, automatic), libltdl7:i386 (2.4.2-1ubuntu1, automatic), libkrb5-26-heimdal:i386 (1.6~git20120311.dfsg.1-2, automatic), libgphoto2-2:i386 (2.4.13-1ubuntu1.2, automatic)
Error: Sub-process /usr/bin/dpkg returned an error code (1)
End-Date: 2013-06-16  23:08:00


Start-Date: 2013-06-16  23:08:33
Commandline: aptdaemon role='role-fix-broken-depends' sender=':1.77'
Install: wine1.6:amd64 (1.6~rc2-0ubuntu1~ppa1, automatic)
Error: Sub-process /usr/bin/dpkg returned an error code (1)
End-Date: 2013-06-16  23:08:35


Start-Date: 2013-06-16  23:09:18
Commandline: aptdaemon role='role-fix-broken-depends' sender=':1.77'
Install: wine1.6:amd64 (1.6~rc2-0ubuntu1~ppa1, automatic)
Error: Sub-process /usr/bin/dpkg returned an error code (1)
End-Date: 2013-06-16  23:09:19

```

---

### Post by Cheesehead on 2013-06-17
> **Synoc said:**
> 
```

Log started: 2013-06-16  23:08:33
(Reading database ... 412805 files and directories currently installed.)
Unpacking wine1.6 (from .../[COLOR="#FF0000"]wine1.6_1.6~rc2-0ubuntu1~ppa1_amd64.deb[/COLOR]) ...
dpkg: error processing /var/cache/apt/archives/wine1.6_1.6~rc2-0ubuntu1~ppa1_amd64.deb (--unpack):
 trying to overwrite '/usr/bin/wine64-preloader', which is also in package [COLOR="#FF0000"]wine1.6-amd64 1.6~rc2-0ubuntu1~ppa1[/COLOR]
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/wine1.6_1.6~rc2-0ubuntu1~ppa1_amd64.deb
Log ended: 2013-06-16  23:08:35

```

Looks like you are trying to install debs from two different Wine PPAs. One is already installed.
Check your /etc/apt/sources.list and remove (or comment out) the older PPA.
Uninstall (or reinstall) the current package.

Best practice during a release upgrade is to uninstall all PPA software and disable all PPAs before running the upgrade. After the upgrade is complete, add new PPAs and install PPA software.  It prevents precisely this kind of problem. PPAs are not supported software, and are not included in pre-release upgrade testing.

---

### Post by Synoc on 2013-06-18
if I read this right, the one PPA with AMD is the old one? or should I just try commenting out the first one in the list?

---

### Post by neilhuang on 2013-06-18
I had the same issue too, and it just so happened to be related to wine1.6.
What I did was to go into synaptic and then filter by the "Broken packages" (Custom Filters buttton on bottom right).
There, I see my 2 broken wine1.6 packages and removed them both. It'll also automatically remove any other wine/playonlinux that depends on wine1.6, but that's fine. 

After the packages are removed, I did a regular sudo apt-get udpate and then a sudo-apt-get install wine, and everything seems fine.
Hope it helps.

---

### Post by Synoc on 2013-06-26
ok I finally got enough free time to fix this, but the wine PPA won't install wine1.6 "no release candidate'" or wine 1.5 for the same reason. only one it installs is 1.4 if I do an apt-get install wine.

Nevermind, it's wine 1.6-rc3 perhaps... we're good. I only needed 1.5 for a game a while back and 1.4 has it standard now anyway.

---

