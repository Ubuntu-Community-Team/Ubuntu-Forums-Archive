---
title: "Trying to install wine 1.6, broke software center"
date: 2014-03-05
forum: Wine
---

### Post by keshek on 2014-03-05
I have been trying to get wine 1.6 to install. I was having issues installing from the software center so I did it from the terminal following the instructions on [http://www.winehq.org/download/ubuntu](http://www.winehq.org/download/ubuntu)

```

sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get install wine1.6

```

There was a issue with one package downloading initially and wine isn't installed, so I tried another install and got all of this:

```

Building dependency tree       
Reading state information... Done
wine1.6 is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libio-socket-ssl-perl : Depends: libnet-ssleay-perl but it is not going to be installed
 libsane:i386 : Depends: libgphoto2-2:i386 (>= 2.4.10.1) but it is not going to be installed
 wine1.6 : Depends: wine1.6-amd64 (= 1:1.6.1-0ubuntu1~ppa1~precise1)
           Depends: wine1.6-i386 (= 1:1.6.1-0ubuntu1~ppa1~precise1)
           Recommends: fonts-horai-umefont but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

So I tried a "sudo apt-get -f install" and got this:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libcups2:i386 libgphoto2-2:i386 libnet-ssleay-perl wine-gecko2.21:i386
  wine-mono0.0.8 wine1.6-amd64 wine1.6-i386:i386
Suggested packages:
  cups-common:i386 gphoto2:i386
Recommended packages:
  wine1.5-i386:i386
The following NEW packages will be installed:
  libcups2:i386 libgphoto2-2:i386 libnet-ssleay-perl wine-gecko2.21:i386
  wine-mono0.0.8 wine1.6-amd64 wine1.6-i386:i386
0 upgraded, 7 newly installed, 0 to remove and 27 not upgraded.
8 not fully installed or removed.
Need to get 0 B/119 MB of archives.
After this operation, 314 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 170672 files and directories currently installed.)
Unpacking libgphoto2-2:i386 (from .../libgphoto2-2_2.4.13-1ubuntu1.2_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libgphoto2-2_2.4.13-1ubuntu1.2_i386.deb (--unpack):
 './usr/share/libgphoto2/2.4.13/konica/english' is different from the same file on the system
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Unpacking wine1.6-amd64 (from .../wine1.6-amd64_1%3a1.6.1-0ubuntu1~ppa1~precise1_amd64.deb) ...
dpkg-deb (subprocess): data: internal gzip read error: '<fd:4>: invalid block type'
dpkg-deb: error: subprocess <decompress> returned error exit status 2
dpkg: error processing /var/cache/apt/archives/wine1.6-amd64_1%3a1.6.1-0ubuntu1~ppa1~precise1_amd64.deb (--unpack):
 short read on buffer copy for backend dpkg-deb during `./usr/lib/x86_64-linux-gnu/wine/winhlp32.exe.so'
No apport report written because MaxReports is reached already
                                                              Unpacking wine1.6-i386:i386 (from .../wine1.6-i386_1%3a1.6.1-0ubuntu1~ppa1~precise1_i386.deb) ...
dpkg-deb (subprocess): data: internal gzip read error: '<fd:4>: invalid literal/lengths set'
dpkg-deb: error: subprocess <decompress> returned error exit status 2
dpkg: error processing /var/cache/apt/archives/wine1.6-i386_1%3a1.6.1-0ubuntu1~ppa1~precise1_i386.deb (--unpack):
 short read on buffer copy for backend dpkg-deb during `./usr/lib/i386-linux-gnu/wine/gdi32.dll.so'
No apport report written because MaxReports is reached already
                                                              Unpacking libnet-ssleay-perl (from .../libnet-ssleay-perl_1.42-1build1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libnet-ssleay-perl_1.42-1build1_amd64.deb (--unpack):
 corrupted filesystem tarfile - corrupted package archive
No apport report written because MaxReports is reached already
                                                              Unpacking libcups2:i386 (from .../libcups2_1.5.3-0ubuntu8_i386.deb) ...
dpkg-deb (subprocess): data: internal gzip read error: '<fd:4>: invalid block type'
dpkg-deb: error: subprocess <decompress> returned error exit status 2
dpkg: error processing /var/cache/apt/archives/libcups2_1.5.3-0ubuntu8_i386.deb (--unpack):
 short read on buffer copy for backend dpkg-deb during `./usr/lib/i386-linux-gnu/libcups.so.2'
No apport report written because MaxReports is reached already
                                                              Unpacking wine-gecko2.21:i386 (from .../wine-gecko2.21_2.21-0ubuntu1~ppa1~precise1_i386.deb) ...
dpkg-deb (subprocess): data: internal gzip read error: '<fd:4>: invalid stored block lengths'
dpkg-deb: error: subprocess <decompress> returned error exit status 2
dpkg: error processing /var/cache/apt/archives/wine-gecko2.21_2.21-0ubuntu1~ppa1~precise1_i386.deb (--unpack):
 short read on buffer copy for backend dpkg-deb during `./usr/share/wine/gecko/wine_gecko-2.21-x86.msi'
No apport report written because MaxReports is reached already
                                                              Unpacking wine-mono0.0.8 (from .../wine-mono0.0.8_0.0.8-0ubuntu1~ppa2_all.deb) ...
dpkg-deb (subprocess): data: internal gzip read error: '<fd:4>: invalid block type'
dpkg-deb: error: subprocess <decompress> returned error exit status 2
dpkg: error processing /var/cache/apt/archives/wine-mono0.0.8_0.0.8-0ubuntu1~ppa2_all.deb (--unpack):
 short read on buffer copy for backend dpkg-deb during `./usr/share/wine/mono/wine-mono-0.0.8.msi'
No apport report written because MaxReports is reached already
                                                              Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/libgphoto2-2_2.4.13-1ubuntu1.2_i386.deb
 /var/cache/apt/archives/wine1.6-amd64_1%3a1.6.1-0ubuntu1~ppa1~precise1_amd64.deb
 /var/cache/apt/archives/wine1.6-i386_1%3a1.6.1-0ubuntu1~ppa1~precise1_i386.deb
 /var/cache/apt/archives/libnet-ssleay-perl_1.42-1build1_amd64.deb
 /var/cache/apt/archives/libcups2_1.5.3-0ubuntu8_i386.deb
 /var/cache/apt/archives/wine-gecko2.21_2.21-0ubuntu1~ppa1~precise1_i386.deb
 /var/cache/apt/archives/wine-mono0.0.8_0.0.8-0ubuntu1~ppa2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

And now when I try to open the software center I get the message "Items cannot be installed or removed until the package catalog is repaired. Do you want to repair it now?"
Upon trying to repair the package catalog I basically get the same error message from the apt-get -f install:

```

installArchives() failed: (Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 170672 files and directories currently installed.)
Unpacking libgphoto2-2:i386 (from .../libgphoto2-2_2.4.13-1ubuntu1.2_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libgphoto2-2_2.4.13-1ubuntu1.2_i386.deb (--unpack):
 './usr/share/libgphoto2/2.4.13/konica/english' is different from the same file on the system
No apport report written because MaxReports is reached already
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Unpacking wine1.6-amd64 (from .../wine1.6-amd64_1%3a1.6.1-0ubuntu1~ppa1~precise1_amd64.deb) ...
dpkg-deb (subprocess): data: internal gzip read error: '<fd:4>: invalid block type'
dpkg-deb: error: subprocess <decompress> returned error exit status 2
dpkg: error processing /var/cache/apt/archives/wine1.6-amd64_1%3a1.6.1-0ubuntu1~ppa1~precise1_amd64.deb (--unpack):
 short read on buffer copy for backend dpkg-deb during `./usr/lib/x86_64-linux-gnu/wine/winhlp32.exe.so'
No apport report written because MaxReports is reached already
Unpacking wine1.6-i386:i386 (from .../wine1.6-i386_1%3a1.6.1-0ubuntu1~ppa1~precise1_i386.deb) ...
dpkg-deb (subprocess): data: internal gzip read error: '<fd:4>: invalid literal/lengths set'
dpkg-deb: error: subprocess <decompress> returned error exit status 2
dpkg: error processing /var/cache/apt/archives/wine1.6-i386_1%3a1.6.1-0ubuntu1~ppa1~precise1_i386.deb (--unpack):
 short read on buffer copy for backend dpkg-deb during `./usr/lib/i386-linux-gnu/wine/gdi32.dll.so'
No apport report written because MaxReports is reached already
Unpacking libnet-ssleay-perl (from .../libnet-ssleay-perl_1.42-1build1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libnet-ssleay-perl_1.42-1build1_amd64.deb (--unpack):
 corrupted filesystem tarfile - corrupted package archive
No apport report written because MaxReports is reached already
Unpacking libcups2:i386 (from .../libcups2_1.5.3-0ubuntu8_i386.deb) ...
dpkg-deb (subprocess): data: internal gzip read error: '<fd:4>: invalid block type'
dpkg-deb: error: subprocess <decompress> returned error exit status 2
dpkg: error processing /var/cache/apt/archives/libcups2_1.5.3-0ubuntu8_i386.deb (--unpack):
 short read on buffer copy for backend dpkg-deb during `./usr/lib/i386-linux-gnu/libcups.so.2'
No apport report written because MaxReports is reached already
Unpacking wine-gecko2.21:i386 (from .../wine-gecko2.21_2.21-0ubuntu1~ppa1~precise1_i386.deb) ...
dpkg-deb (subprocess): data: internal gzip read error: '<fd:4>: invalid stored block lengths'
dpkg-deb: error: subprocess <decompress> returned error exit status 2
dpkg: error processing /var/cache/apt/archives/wine-gecko2.21_2.21-0ubuntu1~ppa1~precise1_i386.deb (--unpack):
 short read on buffer copy for backend dpkg-deb during `./usr/share/wine/gecko/wine_gecko-2.21-x86.msi'
No apport report written because MaxReports is reached already
Unpacking wine-mono0.0.8 (from .../wine-mono0.0.8_0.0.8-0ubuntu1~ppa2_all.deb) ...
dpkg-deb (subprocess): data: internal gzip read error: '<fd:4>: invalid block type'
dpkg-deb: error: subprocess <decompress> returned error exit status 2
dpkg: error processing /var/cache/apt/archives/wine-mono0.0.8_0.0.8-0ubuntu1~ppa2_all.deb (--unpack):
 short read on buffer copy for backend dpkg-deb during `./usr/share/wine/mono/wine-mono-0.0.8.msi'
No apport report written because MaxReports is reached already
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/libgphoto2-2_2.4.13-1ubuntu1.2_i386.deb
 /var/cache/apt/archives/wine1.6-amd64_1%3a1.6.1-0ubuntu1~ppa1~precise1_amd64.deb
 /var/cache/apt/archives/wine1.6-i386_1%3a1.6.1-0ubuntu1~ppa1~precise1_i386.deb
 /var/cache/apt/archives/libnet-ssleay-perl_1.42-1build1_amd64.deb
 /var/cache/apt/archives/libcups2_1.5.3-0ubuntu8_i386.deb
 /var/cache/apt/archives/wine-gecko2.21_2.21-0ubuntu1~ppa1~precise1_i386.deb
 /var/cache/apt/archives/wine-mono0.0.8_0.0.8-0ubuntu1~ppa2_all.deb
Error in function: 
dpkg: dependency problems prevent configuration of libsane:i386:
 libsane:i386 depends on libgphoto2-2 (>= 2.4.10.1); however:
  Package libgphoto2-2:i386 is not installed.
dpkg: error processing libsane:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of wine1.6:
 wine1.6 depends on wine1.6-amd64 (= 1:1.6.1-0ubuntu1~ppa1~precise1); however:
  Package wine1.6-amd64 is not installed.
 wine1.6 depends on wine1.6-i386 (= 1:1.6.1-0ubuntu1~ppa1~precise1); however:
  Package wine1.6-i386 is not installed.
dpkg: error processing wine1.6 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libio-socket-ssl-perl:
 libio-socket-ssl-perl depends on libnet-ssleay-perl; however:
  Package libnet-ssleay-perl is not installed.
dpkg: error processing libio-socket-ssl-perl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of wine1.5:
 wine1.5 depends on wine1.6; however:
  Package wine1.6 is not configured yet.
dpkg: error processing wine1.5 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of liblwp-protocol-https-perl:
 liblwp-protocol-https-perl depends on libio-socket-ssl-perl; however:
  Package libio-socket-ssl-perl is not configured yet.
dpkg: error processing liblwp-protocol-https-perl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libwww-perl:
 libwww-perl depends on liblwp-protocol-https-perl; however:
  Package liblwp-protocol-https-perl is not configured yet.
dpkg: error processing libwww-perl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of icoutils:
 icoutils depends on libwww-perl; however:
  Package libwww-perl is not configured yet.
dpkg: error processing icoutils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-exe-thumbnailer:
 gnome-exe-thumbnailer depends on icoutils; however:
  Package icoutils is not configured yet.
dpkg: error processing gnome-exe-thumbnailer (--configure):
 dependency problems - leaving unconfigured

```

Anyone have any idea on how to fix the issues I am having?

---

### Post by ibjsb4 on 2014-03-05
Try cleaning out /var/cache/apt/archives.

```
sudo apt-get clean
sudo apt-get update
```

---

