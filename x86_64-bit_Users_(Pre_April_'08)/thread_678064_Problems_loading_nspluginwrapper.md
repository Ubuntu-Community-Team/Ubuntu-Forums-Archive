---
title: "Problems loading nspluginwrapper"
date: 2008-01-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by jasper-two on 2008-01-25
Hi Kilz
Sorry to be a pain but
After you said that it is a proxy server problem I removed my  ADSL wireless connection and connected direct to my adsl modem so I could download the nspluginwrapper but I still get the same error.

I do not no what to do now can you help

Jasper

The following packages were automatically installed and are no longer required:
libswscale1d libboost-date-time1.34.1 libqt4-core libqt4-gui libept0
libboost-thread1.34.1 libxapian15 debtags
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
tar: install_flash_player_9_linux.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
mv: cannot stat `/tmp/nsplugwrapper/install_flash_player_9_linux/l ibflashplayer.so': No such file or directory
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
dpkg: error processing *.deb (--install):
cannot access archive: No such file or directory
Errors were encountered while processing:
*.deb
sudo: nspluginwrapper: command not found   :confused:

---

### Post by Kilz on 2008-01-25
go to System -> Preferences -> NetworkProxy and make sure it is set to direct innernet connection. If its set to a socks proxy, you will have to reset it back afterwards if you want to socks proxy to work.

---

### Post by jasper-two on 2008-01-26
Thanks KILZ

You are so cool. it works now thanks

---

