---
title: "error while install wine"
date: 2013-03-10
forum: Wine
---

### Post by wildan angga on 2013-03-10
please help me when I install wine i get this error

```

wildan@wildan:~$  sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
wine is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 ttf-umefont : Depends: fonts-horai-umefont but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
wildan@wildan:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-29 linux-headers-3.2.0-29-generic-pae
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  fonts-horai-umefont
The following NEW packages will be installed:
  fonts-horai-umefont
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0 B/45.4 MB of archives.
After this operation, 89.4 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 171463 files and directories currently installed.)
Unpacking fonts-horai-umefont (from .../fonts-horai-umefont_434-1_all.deb) ...
dpkg-deb (subprocess): data: internal gzip read error: '<fd:4>: data error'
dpkg-deb: error: subprocess <decompress> returned error exit status 2
dpkg: error processing /var/cache/apt/archives/fonts-horai-umefont_434-1_all.deb (--unpack):
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Processing triggers for fontconfig ...
Errors were encountered while processing:
 /var/cache/apt/archives/fonts-horai-umefont_434-1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by QIII on 2013-03-10
*Moved to **Wine***

---

