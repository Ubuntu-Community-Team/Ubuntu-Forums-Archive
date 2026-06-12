---
title: "Installation Wine, Ubuntu center and other apps on Ubuntu (aarch64)"
date: 2019-01-03
forum: Wine
---

### Post by generalghest on 2019-01-03
Hello, Dear users. I am ask everyone to help. I have Galaxy Tab S4 and I have installed on it Linux on DEX (developed by Cannonical and Samsung). Now I have Ubuntu 18.04 with some preinstalled apps like a Intellige IDEA but I have a problems with installing new applications (like Wine or Skype). Please help with it. 
I can post links with screenshots of terminal.
Many thanks.

---

### Post by clementc on 2019-01-03
Hi [**[COLOR=#000000]generalghest[/COLOR]**]("https://ubuntuforums.org/member.php?u=2115439"),

You mentioned difficulties installing new applications, however, you did not provide us with any error message encountered when you try to do so.

We will need more information before we can help you troubleshoot the problem.

---

### Post by generalghest on 2019-01-04
Ok. Please look at [https://photos.app.goo.gl/KjtoKBEfnBeBUo4t8](https://photos.app.goo.gl/KjtoKBEfnBeBUo4t8) . 
Also I have terminal mode. I don't know what is it you could look please to [https://photos.app.goo.gl/8j7EB5SmP9MXyQhPA](https://photos.app.goo.gl/8j7EB5SmP9MXyQhPA) . Maybe should I try some commands in this terminal mode?

---

### Post by deadflowr on 2019-01-04
*Thread moved to **Wine***

---

### Post by clementc on 2019-01-04
Hi [**[COLOR=#000000]generalghest[/COLOR]**]("https://ubuntuforums.org/member.php?u=2115439"),

Can you please try running the following command in Terminal and let me know of the output:

sudo apt-get -f install

---

### Post by generalghest on 2019-01-04
Please look at text from command line below

---

### Post by howefield on 2019-01-04
generalghest, please copy/paste the terminal input/output and place between code tags instead of posting links to images. It makes it easier for others to help you.

---

### Post by generalghest on 2019-01-04
**```
dextop@localhost:~$ sudo apt-get -f install**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  apg appstream cups-pk-helper gkbd-capplet gnome-software-common
  libappstream3 libdbusmenu-gtk4 libfm-data libfm-extra4 libfm-gtk-data
  libfm-gtk4 libfm-modules libfm4 libgeonames0 libgnomekbd8 libgtkspell3-3-0
  libkeybinder0 libllvm5.0 libmenu-cache-bin libmenu-cache3 libqpdf17 libsbc1
  libsnapd-glib1 libtimezonemap-data libtimezonemap1 libwnck-common libwnck22
  linux-headers-4.4.0-119 linux-headers-4.4.0-119-generic
  linux-headers-4.4.0-131 linux-headers-4.4.0-131-generic
  linux-headers-4.4.0-135 linux-headers-4.4.0-135-generic
  linux-image-4.4.0-119-generic linux-image-4.4.0-131-generic
  linux-image-4.4.0-135-generic lxmenu-data lxpanel-data
  signon-keyring-extension snapd-login-service ubuntu-system-service
  unity-control-center-faces
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  openjdk-8-jre-headless
Suggested packages:
  fonts-ipafont-gothic fonts-ipafont-mincho fonts-wqy-microhei
  fonts-wqy-zenhei fonts-indic
The following packages will be upgraded:
  openjdk-8-jre-headless
1 upgraded, 0 newly installed, 0 to remove and 25 not upgraded.
110 not fully installed or removed.
Need to get 0 B/26.2 MB of archives.
After this operation, 834 kB of additional disk space will be used.
**Do you want to continue? [Y/n] y**
(Reading database ... 344364 files and directories currently installed.)
Preparing to unpack .../openjdk-8-jre-headless_8u191-b12-0ubuntu0.16.04.1_arm64.deb ...
Unpacking openjdk-8-jre-headless:arm64 (8u191-b12-0ubuntu0.16.04.1) over (8u181-b13-0ubuntu0.16.04.1) ...
Setting up libssl1.0.0:arm64 (1.0.2g-1ubuntu4.14) ...
Setting up libpython3.5-minimal:arm64 (3.5.2-2ubuntu0~16.04.5) ...
Setting up python3.5-minimal (3.5.2-2ubuntu0~16.04.5) ...
Setting up udev (229-4ubuntu21.10) ...
addgroup: The group `input' already exists as a system group. Exiting.
udev requires a mounted sysfs, not started.
insserv: warning: script 'int_container.sh' missing LSB tags and overrides
insserv: warning: script 'vnc.sh' missing LSB tags and overrides
insserv: warning: script 'init_container.sh' missing LSB tags and overrides
Setting up libcups2:arm64 (2.1.3-4ubuntu0.6) ...
Setting up chromium-codecs-ffmpeg-extra (71.0.3578.80-0ubuntu0.16.04.1) ...
Setting up chromium-browser (71.0.3578.80-0ubuntu0.16.04.1) ...
Setting up chromium-browser-l10n (71.0.3578.80-0ubuntu0.16.04.1) ...
Setting up libcupsmime1:arm64 (2.1.3-4ubuntu0.6) ...
Setting up cups-daemon (2.1.3-4ubuntu0.6) ...
insserv: warning: script 'int_container.sh' missing LSB tags and overrides
insserv: warning: script 'vnc.sh' missing LSB tags and overrides
insserv: warning: script 'init_container.sh' missing LSB tags and overrides
invoke-rc.d: could not determine current runlevel
Setting up libwbclient0:arm64 (2:4.3.11+dfsg-0ubuntu0.16.04.18) ...
Setting up perl-modules-5.22 (5.22.1-9ubuntu0.6) ...
Setting up libperl5.22:arm64 (5.22.1-9ubuntu0.6) ...
Setting up perl (5.22.1-9ubuntu0.6) ...
Setting up libpython2.7-minimal:arm64 (2.7.12-1ubuntu0~16.04.4) ...
Setting up python2.7-minimal (2.7.12-1ubuntu0~16.04.4) ...
Setting up libpython2.7-stdlib:arm64 (2.7.12-1ubuntu0~16.04.4) ...
Setting up libpython2.7:arm64 (2.7.12-1ubuntu0~16.04.4) ...
Setting up samba-libs:arm64 (2:4.3.11+dfsg-0ubuntu0.16.04.18) ...
Setting up libsmbclient:arm64 (2:4.3.11+dfsg-0ubuntu0.16.04.18) ...
Setting up distro-info-data (0.28ubuntu0.9) ...
Setting up libpython3.5-stdlib:arm64 (3.5.2-2ubuntu0~16.04.5) ...
Setting up python3.5 (3.5.2-2ubuntu0~16.04.5) ...
Setting up libasprintf0v5:arm64 (0.19.7-2ubuntu3.1) ...
Setting up gettext-base (0.19.7-2ubuntu3.1) ...
Setting up libcurl3-gnutls:arm64 (7.47.0-1ubuntu2.11) ...
Setting up libpam-systemd:arm64 (229-4ubuntu21.10) ...
Setting up openssh-client (1:7.2p2-4ubuntu2.6) ...
Setting up openssl (1.0.2g-1ubuntu4.14) ...
Setting up cups-core-drivers (2.1.3-4ubuntu0.6) ...
Setting up cups-server-common (2.1.3-4ubuntu0.6) ...
Setting up libcupsimage2:arm64 (2.1.3-4ubuntu0.6) ...
Setting up cups-common (2.1.3-4ubuntu0.6) ...
Setting up cups-client (2.1.3-4ubuntu0.6) ...
Setting up libcupscgi1:arm64 (2.1.3-4ubuntu0.6) ...
Setting up libcupsppdc1:arm64 (2.1.3-4ubuntu0.6) ...
Setting up libpoppler58:arm64 (0.41.0-0ubuntu1.10) ...
Setting up poppler-utils (0.41.0-0ubuntu1.10) ...
Setting up libgs9-common (9.26~dfsg+0-0ubuntu0.16.04.3) ...
update-alternatives: warning: alternative /usr/share/ghostscript/9.25 (part of link group ghostscript-current) doesn't exist; removing from list of alternatives
update-alternatives: warning: /etc/alternatives/ghostscript-current is dangling; it will be updated with best choice
update-alternatives: using /usr/share/ghostscript/9.26 to provide /usr/share/ghostscript/current (ghostscript-current) in auto mode
Setting up libgs9:arm64 (9.26~dfsg+0-0ubuntu0.16.04.3) ...
Setting up ghostscript (9.26~dfsg+0-0ubuntu0.16.04.3) ...
Setting up cups-ppdc (2.1.3-4ubuntu0.6) ...
Setting up cups (2.1.3-4ubuntu0.6) ...
Setting up curl (7.47.0-1ubuntu2.11) ...
Setting up firefox (64.0+build3-0ubuntu0.16.04.1) ...
Please restart all running instances of firefox, or you will experience problems.
Setting up libgettextpo0:arm64 (0.19.7-2ubuntu3.1) ...
Setting up libgettextpo-dev:arm64 (0.19.7-2ubuntu3.1) ...
Setting up libasprintf-dev:arm64 (0.19.7-2ubuntu3.1) ...
Setting up gettext (0.19.7-2ubuntu3.1) ...
Setting up ghostscript-x (9.26~dfsg+0-0ubuntu0.16.04.3) ...
Setting up git-man (1:2.7.4-0ubuntu1.6) ...
Setting up git (1:2.7.4-0ubuntu1.6) ...
Setting up libcurl3:arm64 (7.47.0-1ubuntu2.11) ...
Setting up libfreerdp-primitives1.1:arm64 (1.1.0~git20140921.1.440916e+dfsg1-5ubuntu1.3) ...
Setting up libwinpr-handle0.1:arm64 (1.1.0~git20140921.1.440916e+dfsg1-5ubuntu1.3) ...
Setting up libwinpr-interlocked0.1:arm64 (1.1.0~git20140921.1.440916e+dfsg1-5ubuntu1.3) ...
Setting up libwinpr-thread0.1:arm64 (1.1.0~git20140921.1.440916e+dfsg1-5ubuntu1.3) ...
Setting up libwinpr-synch0.1:arm64 (1.1.0~git20140921.1.440916e+dfsg1-5ubuntu1.3) ...
Setting up libwinpr-crt0.1:arm64 (1.1.0~git20140921.1.440916e+dfsg1-5ubuntu1.3) ...
Setting up libwinpr-sysinfo0.1:arm64 (1.1.0~git20140921.1.440916e+dfsg1-5ubuntu1.3) ...
Setting up libwinpr-utils0.1:arm64 (1.1.0~git20140921.1.440916e+dfsg1-5ubuntu1.3) ...
Setting up libwinpr-pool0.1:arm64 (1.1.0~git20140921.1.440916e+dfsg1-5ubuntu1.3) ...
Setting up libwinpr-registry0.1:arm64 (1.1.0~git20140921.1.440916e+dfsg1-5ubuntu1.3) ...
Setting up libfreerdp-codec1.1:arm64 (1.1.0~git20140921.1.440916e+dfsg1-5ubuntu1.3) ...
Setting up libwinpr-library0.1:arm64 (1.1.0~git20140921.1.440916e+dfsg1-5ubuntu1.3) ...
Setting up libwinpr-environment0.1:arm64 (1.1.0~git20140921.1.440916e+dfsg1-5ubuntu1.3) ...
Setting up libwinpr-heap0.1:arm64 (1.1.0~git20140921.1.440916e+dfsg1-5ubuntu1.3) ...
Setting up libwinpr-path0.1:arm64 (1.1.0~git20140921.1.440916e+dfsg1-5ubuntu1.3) ...
Setting up libfreerdp-common1.1.0:arm64 (1.1.0~git20140921.1.440916e+dfsg1-5ubuntu1.3) ...
Setting up libfreerdp-utils1.1:arm64 (1.1.0~git20140921.1.440916e+dfsg1-5ubuntu1.3) ...
Setting up libwinpr-file0.1:arm64 (1.1.0~git20140921.1.440916e+dfsg1-5ubuntu1.3) ...
Setting up libfreerdp-crypto1.1:arm64 (1.1.0~git20140921.1.440916e+dfsg1-5ubuntu1.3) ...
Setting up libwinpr-input0.1:arm64 (1.1.0~git20140921.1.440916e+dfsg1-5ubuntu1.3) ...
Setting up libfreerdp-locale1.1:arm64 (1.1.0~git20140921.1.440916e+dfsg1-5ubuntu1.3) ...
Setting up libwinpr-dsparse0.1:arm64 (1.1.0~git20140921.1.440916e+dfsg1-5ubuntu1.3) ...
Setting up libwinpr-rpc0.1:arm64 (1.1.0~git20140921.1.440916e+dfsg1-5ubuntu1.3) ...
Setting up libwinpr-sspi0.1:arm64 (1.1.0~git20140921.1.440916e+dfsg1-5ubuntu1.3) ...
Setting up libfreerdp-core1.1:arm64 (1.1.0~git20140921.1.440916e+dfsg1-5ubuntu1.3) ...
Setting up libfreerdp-cache1.1:arm64 (1.1.0~git20140921.1.440916e+dfsg1-5ubuntu1.3) ...
Setting up libfreerdp-client1.1:arm64 (1.1.0~git20140921.1.440916e+dfsg1-5ubuntu1.3) ...
Setting up libfreerdp-gdi1.1:arm64 (1.1.0~git20140921.1.440916e+dfsg1-5ubuntu1.3) ...
Setting up libfreerdp-plugins-standard:arm64 (1.1.0~git20140921.1.440916e+dfsg1-5ubuntu1.3) ...
Setting up libnm-util2:arm64 (1.2.6-0ubuntu0.16.04.3) ...
Setting up libnm-glib-vpn1:arm64 (1.2.6-0ubuntu0.16.04.3) ...
Setting up libnm-glib4:arm64 (1.2.6-0ubuntu0.16.04.3) ...
Setting up libnm0:arm64 (1.2.6-0ubuntu0.16.04.3) ...
Setting up libpoppler-glib8:arm64 (0.41.0-0ubuntu1.10) ...
Setting up libpython3.5:arm64 (3.5.2-2ubuntu0~16.04.5) ...
Setting up libraw15:arm64 (0.17.1-1ubuntu0.4) ...
Setting up libssh-4:arm64 (0.6.3-4.3ubuntu0.2) ...
Setting up libwavpack1:arm64 (4.75.2-2ubuntu0.2) ...
Setting up linux-firmware (1.157.21) ...
Setting up linux-image-4.4.0-139-generic (4.4.0-139.165) ...
Running depmod.
The link /boot/initrd.img is a dangling linkto /boot/initrd.img-4.4.0-138-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-139-generic /boot/vmlinuz-4.4.0-139-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-139-generic /boot/vmlinuz-4.4.0-139-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-139-generic /boot/vmlinuz-4.4.0-139-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-139-generic /boot/vmlinuz-4.4.0-139-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-139-generic /boot/vmlinuz-4.4.0-139-generic
run-parts: executing /etc/kernel/postinst.d/x-grub-legacy-ec2 4.4.0-139-generic /boot/vmlinuz-4.4.0-139-generic
Searching for GRUB installation directory ... found: /boot/grub
findfs: unable to resolve 'LABEL=cloudimg-rootfs'
Cannot determine root device.  Assuming /dev/hda1
This error is probably caused by an invalid /etc/fstab
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz
Found kernel: /boot/vmlinuz.old
Found kernel: /boot/vmlinuz-4.4.0-138-generic
Found kernel: /boot/vmlinuz-4.4.0-137-generic
Found kernel: /boot/vmlinuz-4.4.0-135-generic
Found kernel: /boot/vmlinuz-4.4.0-131-generic
Found kernel: /boot/vmlinuz-4.4.0-119-generic
Replacing config file /run/grub/menu.lst with new version
Found kernel: /boot/vmlinuz
Found kernel: /boot/vmlinuz.old
Found kernel: /boot/vmlinuz-4.4.0-139-generic
Found kernel: /boot/vmlinuz-4.4.0-138-generic
Found kernel: /boot/vmlinuz-4.4.0-137-generic
Found kernel: /boot/vmlinuz-4.4.0-135-generic
Found kernel: /boot/vmlinuz-4.4.0-131-generic
Found kernel: /boot/vmlinuz-4.4.0-119-generic
Replacing config file /run/grub/menu.lst with new version
Updating /boot/grub/menu.lst ... done


run-parts: executing /etc/kernel/postinst.d/zz-flash-kernel 4.4.0-139-generic /boot/vmlinuz-4.4.0-139-generic
flash-kernel: deferring update (trigger activated)
Setting up linux-image-generic (4.4.0.139.145) ...
Setting up linux-headers-4.4.0-139 (4.4.0-139.165) ...
Setting up linux-headers-4.4.0-139-generic (4.4.0-139.165) ...
Setting up linux-headers-generic (4.4.0.139.145) ...
Setting up linux-generic (4.4.0.139.145) ...
Setting up linux-libc-dev:arm64 (4.4.0-139.165) ...
Setting up network-manager (1.2.6-0ubuntu0.16.04.3) ...
insserv: warning: script 'int_container.sh' missing LSB tags and overrides
insserv: warning: script 'vnc.sh' missing LSB tags and overrides
insserv: warning: script 'init_container.sh' missing LSB tags and overrides
invoke-rc.d: could not determine current runlevel
 * Reloading system message bus config...                                                                                                    [ OK ] 
Setting up ppp (2.4.7-1+2ubuntu1.16.04.1) ...
insserv: warning: script 'int_container.sh' missing LSB tags and overrides
insserv: warning: script 'vnc.sh' missing LSB tags and overrides
insserv: warning: script 'init_container.sh' missing LSB tags and overrides
Setting up openjdk-8-jre-headless:arm64 (8u191-b12-0ubuntu0.16.04.1) ...
Installing new version of config file /etc/java-8-openjdk/security/java.security ...
Setting up openjdk-8-jre:arm64 (8u191-b12-0ubuntu0.16.04.1) ...
Setting up openjdk-8-jdk-headless:arm64 (8u191-b12-0ubuntu0.16.04.1) ...
Setting up openjdk-8-jdk:arm64 (8u191-b12-0ubuntu0.16.04.1) ...
Setting up openssh-sftp-server (1:7.2p2-4ubuntu2.6) ...
Setting up openssh-server (1:7.2p2-4ubuntu2.6) ...
insserv: warning: script 'int_container.sh' missing LSB tags and overrides
insserv: warning: script 'vnc.sh' missing LSB tags and overrides
insserv: warning: script 'init_container.sh' missing LSB tags and overrides
invoke-rc.d: could not determine current runlevel
Setting up python2.7 (2.7.12-1ubuntu0~16.04.4) ...
Setting up python3-cryptography (1.2.3-1ubuntu0.2) ...
Setting up python3-lxml (3.5.0-1ubuntu0.1) ...
Setting up cups-bsd (2.1.3-4ubuntu0.6) ...
Processing triggers for libc-bin (2.23-0ubuntu10) ...
Processing triggers for flash-kernel (3.0~rc.4ubuntu62.2) ...
Can't find /boot/vmlinuz-4.4.0-139-generic or /boot/initrd.img-4.4.0-139-generic
dpkg: error processing package flash-kernel (--configure):
 subprocess installed post-installation script returned error exit status 1
dmesg: read kernel buffer failed: Permission denied
                                                   Errors were encountered while processing:
 flash-kernel
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
**```
dextop@localhost:~$ sudo apt install software-center**
[sudo] password for dextop: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  apg appstream cups-pk-helper gkbd-capplet gnome-software-common libappstream3 libdbusmenu-gtk4 libfm-data libfm-extra4 libfm-gtk-data libfm-gtk4
  libfm-modules libfm4 libgeonames0 libgnomekbd8 libgtkspell3-3-0 libkeybinder0 libllvm5.0 libmenu-cache-bin libmenu-cache3 libqpdf17 libsbc1
  libsnapd-glib1 libtimezonemap-data libtimezonemap1 libwnck-common libwnck22 linux-headers-4.4.0-119 linux-headers-4.4.0-119-generic
  linux-headers-4.4.0-131 linux-headers-4.4.0-131-generic linux-headers-4.4.0-135 linux-headers-4.4.0-135-generic linux-headers-4.4.0-137
  linux-headers-4.4.0-137-generic linux-image-4.4.0-119-generic linux-image-4.4.0-131-generic linux-image-4.4.0-135-generic
  linux-image-4.4.0-137-generic lxmenu-data lxpanel-data signon-keyring-extension snapd-login-service ubuntu-system-service
  unity-control-center-faces
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  apt-xapian-index libxapian-1.3-5 oneconf oneconf-common python-apt python-aptdaemon python-aptdaemon.gtk3widgets python-attr python-blinker
  python-bs4 python-cairo python-cffi-backend python-chardet python-cryptography python-cups python-dbus python-debian python-debtagshw
  python-defer python-dirspec python-enum34 python-gi-cairo python-html5lib python-httplib2 python-idna python-ipaddress python-jwt python-lxml
  python-oauthlib python-oneconf python-openssl python-pam python-piston-mini-client python-pkg-resources python-pyasn1 python-pyasn1-modules
  python-serial python-service-identity python-six python-twisted-bin python-twisted-core python-twisted-web python-ubuntu-sso-client
  python-xapian python-xdg python-zope.interface python3-oneconf python3-piston-mini-client python3-xapian1.3 software-center-aptdaemon-plugins
  ubuntu-sso-client
Suggested packages:
  xapian-tools python-apt-dbg python-apt-doc python-blinker-doc python-cryptography-doc python-cryptography-vectors python-dbus-doc
  python-dbus-dbg python-enum34-doc python-genshi python-crypto python-lxml-dbg python-lxml-doc python-openssl-doc python-openssl-dbg
  python-pam-dbg python-setuptools python-wxgtk3.0 | python-wxgtk python-twisted-bin-dbg python-tk python-gtk2 python-glade2 python-qt3
  python-wxgtk3.0 xapian-doc ubuntu-sso-client-gui
The following NEW packages will be installed:
  apt-xapian-index libxapian-1.3-5 oneconf oneconf-common python-apt python-aptdaemon python-aptdaemon.gtk3widgets python-attr python-blinker
  python-bs4 python-cairo python-cffi-backend python-chardet python-cryptography python-cups python-dbus python-debian python-debtagshw
  python-defer python-dirspec python-enum34 python-gi-cairo python-html5lib python-httplib2 python-idna python-ipaddress python-jwt python-lxml
  python-oauthlib python-oneconf python-openssl python-pam python-piston-mini-client python-pkg-resources python-pyasn1 python-pyasn1-modules
  python-serial python-service-identity python-six python-twisted-bin python-twisted-core python-twisted-web python-ubuntu-sso-client
  python-xapian python-xdg python-zope.interface python3-oneconf python3-piston-mini-client python3-xapian1.3 software-center
  software-center-aptdaemon-plugins ubuntu-sso-client
0 upgraded, 52 newly installed, 0 to remove and 25 not upgraded.
1 not fully installed or removed.
Need to get 6,489 kB of archives.
After this operation, 39.8 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial/main arm64 python-dbus arm64 1.2.0-3 [76.4 kB]
Get:2 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial/universe arm64 python-dirspec all 13.10-1ubuntu1 [6,294 B]
Get:3 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial/main arm64 python-httplib2 all 0.9.1+dfsg-1 [34.2 kB]
Get:4 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial/main arm64 python-blinker all 1.3.dfsg2-1build1 [12.4 kB]
Get:5 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial/main arm64 python-cffi-backend arm64 1.5.2-1ubuntu1 [51.8 kB]
Get:6 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial/main arm64 python-enum34 all 1.1.2-1 [35.8 kB]
Get:7 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial/main arm64 python-idna all 2.0-3 [35.1 kB]
Get:8 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial/main arm64 python-ipaddress all 1.0.16-1 [18.0 kB]
Get:9 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial/main arm64 python-pkg-resources all 20.7.0-1 [108 kB]
Get:10 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial/main arm64 python-pyasn1 all 0.1.9-1 [45.1 kB]
Get:11 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial/main arm64 python-six all 1.10.0-3 [10.9 kB]
Get:12 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial-updates/main arm64 python-cryptography arm64 1.2.3-1ubuntu0.2 [151 kB]
Get:13 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial-updates/main arm64 python-jwt all 1.3.0-1ubuntu0.1 [20.5 kB]
Get:14 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial/main arm64 python-oauthlib all 1.0.3-1 [62.7 kB]
Get:15 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial-updates/main arm64 python-openssl all 0.15.1-2ubuntu0.2 [84.9 kB]
Get:16 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial-updates/main arm64 python-twisted-bin arm64 16.0.0-1ubuntu0.2 [11.9 kB]
Get:17 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial/main arm64 python-zope.interface arm64 4.1.3-1build1 [79.4 kB]
Get:18 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial/main arm64 python-attr all 15.2.0-1 [11.3 kB]
Get:19 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial/main arm64 python-pyasn1-modules all 0.0.7-0.1 [20.5 kB]
Get:20 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial/main arm64 python-service-identity all 16.0.0-2 [9,318 B]
Get:21 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial-updates/main arm64 python-twisted-core all 16.0.0-1ubuntu0.2 [1,941 kB]
Get:22 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial-updates/main arm64 python-twisted-web all 16.0.0-1ubuntu0.2 [75.0 kB]
Get:23 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial/universe arm64 python-ubuntu-sso-client all 13.10-0ubuntu11 [49.8 kB]
Get:24 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial/universe arm64 ubuntu-sso-client all 13.10-0ubuntu11 [2,780 B]
Get:25 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial/universe arm64 libxapian-1.3-5 arm64 1.3.4-0ubuntu6 [552 kB]
Get:26 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial/universe arm64 python3-xapian1.3 arm64 1.3.4-0ubuntu1 [338 kB]
Get:27 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial-updates/universe arm64 apt-xapian-index all 0.47ubuntu8.4 [56.9 kB]
Get:28 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial-updates/main arm64 python-apt arm64 1.1.0~beta1ubuntu0.16.04.2 [133 kB]
Get:29 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial/main arm64 python-bs4 all 4.4.1-1 [64.2 kB]
Get:30 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial/main arm64 python-cairo arm64 1.8.8-2 [36.4 kB]                                                 
Get:31 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial/main arm64 python-chardet all 2.3.0-2 [96.3 kB]                                                 
Get:32 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial/universe arm64 python-cups arm64 1.9.73-0ubuntu2 [49.7 kB]                                      
Get:33 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial/universe arm64 python-debian all 0.1.27ubuntu2 [64.2 kB]                                        
Get:34 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial/universe arm64 python-debtagshw all 2.0.1ubuntu6 [8,466 B]                                      
Get:35 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial/universe arm64 python-gi-cairo arm64 3.20.0-0ubuntu1 [5,942 B]                                  
Get:36 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial/main arm64 python-html5lib all 0.999-4 [83.1 kB]                                                
Get:37 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial-updates/main arm64 python-lxml arm64 3.5.0-1ubuntu0.1 [691 kB]                                  
Get:38 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial/main arm64 python-pam arm64 0.4.2-13.2ubuntu2 [9,342 B]                                         
Get:39 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial/main arm64 python-serial all 3.0.1-1 [69.9 kB]                                                  
Get:40 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial/main arm64 python-xapian arm64 1.2.22-2build1 [185 kB]                                          
Get:41 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial/universe arm64 python-xdg all 0.25-4 [31.4 kB]                                                  
Get:42 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial/universe arm64 python-piston-mini-client all 0.7.5-0ubuntu2 [18.6 kB]                           
Get:43 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial/universe arm64 software-center-aptdaemon-plugins all 0.1.6build1 [5,750 B]                      
Get:44 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial/universe arm64 python-defer all 1.0.6-2build1 [10.7 kB]                                         
Get:45 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial/universe arm64 python-aptdaemon all 1.1.1+bzr982-0ubuntu14 [76.4 kB]                            
Get:46 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial/universe arm64 python-aptdaemon.gtk3widgets all 1.1.1+bzr982-0ubuntu14 [13.8 kB]                
Get:47 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial/universe arm64 oneconf-common all 0.3.9 [5,992 B]                                               
Get:48 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial/universe arm64 python3-piston-mini-client all 0.7.5-0ubuntu2 [18.4 kB]                          
Get:49 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial/universe arm64 python3-oneconf all 0.3.9 [19.4 kB]                                              
Get:50 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial/universe arm64 oneconf all 0.3.9 [5,462 B]                                                      
Get:51 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial/universe arm64 python-oneconf all 0.3.9 [19.4 kB]                                               
Get:52 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial/universe arm64 software-center all 16.01+16.04.20160420 [867 kB]                                
Fetched 6,489 kB in 9s (715 kB/s)                                                                                                                  
Extracting templates from packages: 100%
Selecting previously unselected package python-dbus.
(Reading database ... 344364 files and directories currently installed.)
Preparing to unpack .../python-dbus_1.2.0-3_arm64.deb ...
Unpacking python-dbus (1.2.0-3) ...
Selecting previously unselected package python-dirspec.
Preparing to unpack .../python-dirspec_13.10-1ubuntu1_all.deb ...
Unpacking python-dirspec (13.10-1ubuntu1) ...
Selecting previously unselected package python-httplib2.
Preparing to unpack .../python-httplib2_0.9.1+dfsg-1_all.deb ...
Unpacking python-httplib2 (0.9.1+dfsg-1) ...
Selecting previously unselected package python-blinker.
Preparing to unpack .../python-blinker_1.3.dfsg2-1build1_all.deb ...
Unpacking python-blinker (1.3.dfsg2-1build1) ...
Selecting previously unselected package python-cffi-backend.
Preparing to unpack .../python-cffi-backend_1.5.2-1ubuntu1_arm64.deb ...
Unpacking python-cffi-backend (1.5.2-1ubuntu1) ...
Selecting previously unselected package python-enum34.
Preparing to unpack .../python-enum34_1.1.2-1_all.deb ...
Unpacking python-enum34 (1.1.2-1) ...
Selecting previously unselected package python-idna.
Preparing to unpack .../python-idna_2.0-3_all.deb ...
Unpacking python-idna (2.0-3) ...
Selecting previously unselected package python-ipaddress.
Preparing to unpack .../python-ipaddress_1.0.16-1_all.deb ...
Unpacking python-ipaddress (1.0.16-1) ...
Selecting previously unselected package python-pkg-resources.
Preparing to unpack .../python-pkg-resources_20.7.0-1_all.deb ...
Unpacking python-pkg-resources (20.7.0-1) ...
Selecting previously unselected package python-pyasn1.
Preparing to unpack .../python-pyasn1_0.1.9-1_all.deb ...
Unpacking python-pyasn1 (0.1.9-1) ...
Selecting previously unselected package python-six.
Preparing to unpack .../python-six_1.10.0-3_all.deb ...
Unpacking python-six (1.10.0-3) ...
Selecting previously unselected package python-cryptography.
Preparing to unpack .../python-cryptography_1.2.3-1ubuntu0.2_arm64.deb ...
Unpacking python-cryptography (1.2.3-1ubuntu0.2) ...
Selecting previously unselected package python-jwt.
Preparing to unpack .../python-jwt_1.3.0-1ubuntu0.1_all.deb ...
Unpacking python-jwt (1.3.0-1ubuntu0.1) ...
Selecting previously unselected package python-oauthlib.
Preparing to unpack .../python-oauthlib_1.0.3-1_all.deb ...
Unpacking python-oauthlib (1.0.3-1) ...
Selecting previously unselected package python-openssl.
Preparing to unpack .../python-openssl_0.15.1-2ubuntu0.2_all.deb ...
Unpacking python-openssl (0.15.1-2ubuntu0.2) ...
Selecting previously unselected package python-twisted-bin.
Preparing to unpack .../python-twisted-bin_16.0.0-1ubuntu0.2_arm64.deb ...
Unpacking python-twisted-bin (16.0.0-1ubuntu0.2) ...
Selecting previously unselected package python-zope.interface.
Preparing to unpack .../python-zope.interface_4.1.3-1build1_arm64.deb ...
Unpacking python-zope.interface (4.1.3-1build1) ...
Selecting previously unselected package python-attr.
Preparing to unpack .../python-attr_15.2.0-1_all.deb ...
Unpacking python-attr (15.2.0-1) ...
Selecting previously unselected package python-pyasn1-modules.
Preparing to unpack .../python-pyasn1-modules_0.0.7-0.1_all.deb ...
Unpacking python-pyasn1-modules (0.0.7-0.1) ...
Selecting previously unselected package python-service-identity.
Preparing to unpack .../python-service-identity_16.0.0-2_all.deb ...
Unpacking python-service-identity (16.0.0-2) ...
Selecting previously unselected package python-twisted-core.
Preparing to unpack .../python-twisted-core_16.0.0-1ubuntu0.2_all.deb ...
Unpacking python-twisted-core (16.0.0-1ubuntu0.2) ...
Selecting previously unselected package python-twisted-web.
Preparing to unpack .../python-twisted-web_16.0.0-1ubuntu0.2_all.deb ...
Unpacking python-twisted-web (16.0.0-1ubuntu0.2) ...
Selecting previously unselected package python-ubuntu-sso-client.
Preparing to unpack .../python-ubuntu-sso-client_13.10-0ubuntu11_all.deb ...
Unpacking python-ubuntu-sso-client (13.10-0ubuntu11) ...
Selecting previously unselected package ubuntu-sso-client.
Preparing to unpack .../ubuntu-sso-client_13.10-0ubuntu11_all.deb ...
Unpacking ubuntu-sso-client (13.10-0ubuntu11) ...
Selecting previously unselected package libxapian-1.3-5:arm64.
Preparing to unpack .../libxapian-1.3-5_1.3.4-0ubuntu6_arm64.deb ...
Unpacking libxapian-1.3-5:arm64 (1.3.4-0ubuntu6) ...
Selecting previously unselected package python3-xapian1.3.
Preparing to unpack .../python3-xapian1.3_1.3.4-0ubuntu1_arm64.deb ...
Unpacking python3-xapian1.3 (1.3.4-0ubuntu1) ...
Selecting previously unselected package apt-xapian-index.
Preparing to unpack .../apt-xapian-index_0.47ubuntu8.4_all.deb ...
Unpacking apt-xapian-index (0.47ubuntu8.4) ...
Selecting previously unselected package python-apt.
Preparing to unpack .../python-apt_1.1.0~beta1ubuntu0.16.04.2_arm64.deb ...
Unpacking python-apt (1.1.0~beta1ubuntu0.16.04.2) ...
Selecting previously unselected package python-bs4.
Preparing to unpack .../python-bs4_4.4.1-1_all.deb ...
Unpacking python-bs4 (4.4.1-1) ...
Selecting previously unselected package python-cairo.
Preparing to unpack .../python-cairo_1.8.8-2_arm64.deb ...
Unpacking python-cairo (1.8.8-2) ...
Selecting previously unselected package python-chardet.
Preparing to unpack .../python-chardet_2.3.0-2_all.deb ...
Unpacking python-chardet (2.3.0-2) ...
Selecting previously unselected package python-cups.
Preparing to unpack .../python-cups_1.9.73-0ubuntu2_arm64.deb ...
Unpacking python-cups (1.9.73-0ubuntu2) ...
Selecting previously unselected package python-debian.
Preparing to unpack .../python-debian_0.1.27ubuntu2_all.deb ...
Unpacking python-debian (0.1.27ubuntu2) ...
Selecting previously unselected package python-debtagshw.
Preparing to unpack .../python-debtagshw_2.0.1ubuntu6_all.deb ...
Unpacking python-debtagshw (2.0.1ubuntu6) ...
Selecting previously unselected package python-gi-cairo.
Preparing to unpack .../python-gi-cairo_3.20.0-0ubuntu1_arm64.deb ...
Unpacking python-gi-cairo (3.20.0-0ubuntu1) ...
Selecting previously unselected package python-html5lib.
Preparing to unpack .../python-html5lib_0.999-4_all.deb ...
Unpacking python-html5lib (0.999-4) ...
Selecting previously unselected package python-lxml.
Preparing to unpack .../python-lxml_3.5.0-1ubuntu0.1_arm64.deb ...
Unpacking python-lxml (3.5.0-1ubuntu0.1) ...
Selecting previously unselected package python-pam.
Preparing to unpack .../python-pam_0.4.2-13.2ubuntu2_arm64.deb ...
Unpacking python-pam (0.4.2-13.2ubuntu2) ...
Selecting previously unselected package python-serial.
Preparing to unpack .../python-serial_3.0.1-1_all.deb ...
Unpacking python-serial (3.0.1-1) ...
Selecting previously unselected package python-xapian.
Preparing to unpack .../python-xapian_1.2.22-2build1_arm64.deb ...
Unpacking python-xapian (1.2.22-2build1) ...
Selecting previously unselected package python-xdg.
Preparing to unpack .../python-xdg_0.25-4_all.deb ...
Unpacking python-xdg (0.25-4) ...
Selecting previously unselected package python-piston-mini-client.
Preparing to unpack .../python-piston-mini-client_0.7.5-0ubuntu2_all.deb ...
Unpacking python-piston-mini-client (0.7.5-0ubuntu2) ...
Selecting previously unselected package software-center-aptdaemon-plugins.
Preparing to unpack .../software-center-aptdaemon-plugins_0.1.6build1_all.deb ...
Unpacking software-center-aptdaemon-plugins (0.1.6build1) ...
Selecting previously unselected package python-defer.
Preparing to unpack .../python-defer_1.0.6-2build1_all.deb ...
Unpacking python-defer (1.0.6-2build1) ...
Selecting previously unselected package python-aptdaemon.
Preparing to unpack .../python-aptdaemon_1.1.1+bzr982-0ubuntu14_all.deb ...
Unpacking python-aptdaemon (1.1.1+bzr982-0ubuntu14) ...
Selecting previously unselected package python-aptdaemon.gtk3widgets.
Preparing to unpack .../python-aptdaemon.gtk3widgets_1.1.1+bzr982-0ubuntu14_all.deb ...
Unpacking python-aptdaemon.gtk3widgets (1.1.1+bzr982-0ubuntu14) ...
Selecting previously unselected package oneconf-common.
Preparing to unpack .../oneconf-common_0.3.9_all.deb ...
Unpacking oneconf-common (0.3.9) ...
Selecting previously unselected package python3-piston-mini-client.
Preparing to unpack .../python3-piston-mini-client_0.7.5-0ubuntu2_all.deb ...
Unpacking python3-piston-mini-client (0.7.5-0ubuntu2) ...
Selecting previously unselected package python3-oneconf.
Preparing to unpack .../python3-oneconf_0.3.9_all.deb ...
Unpacking python3-oneconf (0.3.9) ...
Selecting previously unselected package oneconf.
Preparing to unpack .../archives/oneconf_0.3.9_all.deb ...
Unpacking oneconf (0.3.9) ...
Selecting previously unselected package python-oneconf.
Preparing to unpack .../python-oneconf_0.3.9_all.deb ...
Unpacking python-oneconf (0.3.9) ...
Selecting previously unselected package software-center.
Preparing to unpack .../software-center_16.01+16.04.20160420_all.deb ...
Unpacking software-center (16.01+16.04.20160420) ...
Processing triggers for doc-base (0.10.7) ...
Processing 3 added doc-base files...
Error in `/usr/share/doc-base/xapian-python3-docs', line 9: all `Format' sections are invalid.
Note: `install-docs --verbose --check file_name' may give more details about the above error.
Registering documents with scrollkeeper...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for libc-bin (2.23-0ubuntu10) ...
Processing triggers for dbus (1.10.6-1ubuntu3.3) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5.2) ...
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20180209-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Processing triggers for hicolor-icon-theme (0.15-0ubuntu1.1) ...
Setting up flash-kernel (3.0~rc.4ubuntu62.2) ...
Setting up python-dbus (1.2.0-3) ...
Remove stale byte-compiled files...
Setting up python-dirspec (13.10-1ubuntu1) ...
Setting up python-httplib2 (0.9.1+dfsg-1) ...
Setting up python-blinker (1.3.dfsg2-1build1) ...
Setting up python-cffi-backend (1.5.2-1ubuntu1) ...
Setting up python-enum34 (1.1.2-1) ...
Setting up python-idna (2.0-3) ...
Setting up python-ipaddress (1.0.16-1) ...
Setting up python-pkg-resources (20.7.0-1) ...
Setting up python-pyasn1 (0.1.9-1) ...
Setting up python-six (1.10.0-3) ...
Setting up python-cryptography (1.2.3-1ubuntu0.2) ...
Setting up python-jwt (1.3.0-1ubuntu0.1) ...
Setting up python-oauthlib (1.0.3-1) ...
Setting up python-openssl (0.15.1-2ubuntu0.2) ...
Setting up python-twisted-bin (16.0.0-1ubuntu0.2) ...
Setting up python-zope.interface (4.1.3-1build1) ...
Setting up python-attr (15.2.0-1) ...
Setting up python-pyasn1-modules (0.0.7-0.1) ...
Setting up python-service-identity (16.0.0-2) ...
Setting up python-twisted-core (16.0.0-1ubuntu0.2) ...
Setting up python-twisted-web (16.0.0-1ubuntu0.2) ...
Setting up python-ubuntu-sso-client (13.10-0ubuntu11) ...
Setting up ubuntu-sso-client (13.10-0ubuntu11) ...
Setting up libxapian-1.3-5:arm64 (1.3.4-0ubuntu6) ...
Setting up python3-xapian1.3 (1.3.4-0ubuntu1) ...
Setting up apt-xapian-index (0.47ubuntu8.4) ...
apt-xapian-index: Building new index in background...
Setting up python-apt (1.1.0~beta1ubuntu0.16.04.2) ...
Setting up python-bs4 (4.4.1-1) ...
Setting up python-cairo (1.8.8-2) ...
Setting up python-chardet (2.3.0-2) ...
Setting up python-cups (1.9.73-0ubuntu2) ...
Setting up python-debian (0.1.27ubuntu2) ...
Setting up python-debtagshw (2.0.1ubuntu6) ...
Setting up python-gi-cairo (3.20.0-0ubuntu1) ...
Setting up python-html5lib (0.999-4) ...
Setting up python-lxml (3.5.0-1ubuntu0.1) ...
Setting up python-pam (0.4.2-13.2ubuntu2) ...
Setting up python-serial (3.0.1-1) ...
Setting up python-xapian (1.2.22-2build1) ...
Setting up python-xdg (0.25-4) ...
Setting up python-piston-mini-client (0.7.5-0ubuntu2) ...
Setting up software-center-aptdaemon-plugins (0.1.6build1) ...
Setting up python-defer (1.0.6-2build1) ...
Setting up python-aptdaemon (1.1.1+bzr982-0ubuntu14) ...
Setting up python-aptdaemon.gtk3widgets (1.1.1+bzr982-0ubuntu14) ...
Setting up oneconf-common (0.3.9) ...
Setting up python3-piston-mini-client (0.7.5-0ubuntu2) ...
Setting up python3-oneconf (0.3.9) ...
Setting up oneconf (0.3.9) ...
Setting up python-oneconf (0.3.9) ...
Setting up software-center (16.01+16.04.20160420) ...
Updating software catalog...this may take a moment.
INFO:softwarecenter.db.pkginfo_impl.aptcache:aptcache.open()
Traceback (most recent call last):
  File "/usr/sbin/update-apt-xapian-index", line 111, in <module>
    indexer.rebuild(opts.pkgfile)
  File "/usr/lib/python3/dist-packages/axi/indexer.py", line 761, in rebuild
    self.buildIndex(dbdir, generator)
  File "/usr/lib/python3/dist-packages/axi/indexer.py", line 737, in buildIndex
    db.add_document(doc)
xapian.DatabaseError: Error writing block 143 (No space left on device)
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/apport_python_hook.py", line 146, in apport_excepthook
    pr.write(f)
  File "/usr/lib/python3/dist-packages/problem_report.py", line 402, in write
    file.write(v.replace(b'\n', b'\n '))
OSError: [Errno 28] No space left on device


During handling of the above exception, another exception occurred:


Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/apport_python_hook.py", line 146, in apport_excepthook
    pr.write(f)
OSError: [Errno 28] No space left on device


Original exception was:
Traceback (most recent call last):
  File "/usr/sbin/update-apt-xapian-index", line 111, in <module>
    indexer.rebuild(opts.pkgfile)
  File "/usr/lib/python3/dist-packages/axi/indexer.py", line 761, in rebuild
    self.buildIndex(dbdir, generator)
  File "/usr/lib/python3/dist-packages/axi/indexer.py", line 737, in buildIndex
    db.add_document(doc)
xapian.DatabaseError: Error writing block 143 (No space left on device)
Traceback (most recent call last):
  File "/usr/sbin/update-software-center", line 176, in <module>
    pathname, appinfo_dir=options.app_install_desktop_dir)
  File "/usr/share/software-center/softwarecenter/db/update.py", line 1200, in rebuild_database
    db.flush()
xapian.DatabaseError: Modifications failed (DatabaseError: Error writing block: No space left on device), and cannot set consistent table revision numbers: Error writing to file
dpkg: unrecoverable fatal error, aborting:
 unable to flush /var/lib/dpkg/updates/tmp.i after padding: No space left on device
E: Sub-process /usr/bin/dpkg returned an error code (2)
dextop@localhost:~$ software-center
/usr/bin/software-center:25: PyGIWarning: Gtk was imported without specifying a version first. Use gi.require_version('Gtk', '3.0') before import to ensure that the right version gets loaded.
  from gi.repository import Gtk, GObject
2019-01-04 15:04:04,141 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/share/software-center/softwarecenter/netstatus.py', 122, '__init_network_state')'
2019-01-04 15:04:04,140 - root - WARNING - failed to init network state watcher 'org.freedesktop.DBus.Error.AccessDenied: Failed to connect to socket /var/run/dbus/system_bus_socket: Permission denied'
/usr/share/software-center/softwarecenter/ui/gtk3/views/purchaseview.py:29: PyGIWarning: WebKit2 was imported without specifying a version first. Use gi.require_version('WebKit2', '4.0') before import to ensure that the right version gets loaded.
  from gi.repository import WebKit2 as webkit
2019-01-04 15:04:05,044 - softwarecenter.backend.zeitgeist_logger - WARNING - Support for Zeitgeist disabled
/usr/share/software-center/softwarecenter/ui/gtk3/widgets/symbolic_icons.py:23: PyGIWarning: PangoCairo was imported without specifying a version first. Use gi.require_version('PangoCairo', '1.0') before import to ensure that the right version gets loaded.
  from gi.repository import Gtk, Gdk, GLib, PangoCairo
2019-01-04 15:04:05,068 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/share/software-center/softwarecenter/netstatus.py', 144, 'test_ping')'
2019-01-04 15:04:05,068 - root - INFO - Attempting one time ping of screenshots.ubuntu.com to test if internet connectivity exists.
2019-01-04 15:04:05,285 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/share/software-center/softwarecenter/netstatus.py', 160, 'test_ping')'
2019-01-04 15:04:05,284 - root - INFO - ping output: 'Could not detect an internet connection
ping: icmp open socket: Operation not permitted
'
2019-01-04 15:04:05,288 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2019-01-04 15:04:05,311 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py', 151, '__init__')'
2019-01-04 15:04:05,310 - root - ERROR - Can not get aptdaemon client: 'org.freedesktop.DBus.Error.AccessDenied: Failed to connect to socket /var/run/dbus/system_bus_socket: Permission denied', no size information will be available 
2019-01-04 15:04:05,325 - softwarecenter.ui.gtk3.app - INFO - building local database
2019-01-04 15:04:05,326 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
2019-01-04 15:04:05,843 - softwarecenter.db.update - WARNING - Cannot write to '/var/cache/software-center/xapian'.
2019-01-04 15:04:05,844 - softwarecenter.db.update - WARNING - Please check you have the relevant permissions.
Traceback (most recent call last):
  File "/usr/bin/software-center", line 130, in <module>
    app = SoftwareCenterAppGtk3(options, args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 329, in __init__
    self.backend = get_install_backend()
  File "/usr/share/software-center/softwarecenter/backend/installbackend.py", line 88, in get_install_backend
    install_backend = AptdaemonBackend()
  File "/usr/share/software-center/softwarecenter/backend/installbackend_impl/aptd.py", line 226, in __init__
    bus = get_dbus_bus()
  File "/usr/share/software-center/softwarecenter/backend/installbackend_impl/aptd.py", line 77, in get_dbus_bus
    bus = dbus.SystemBus()
  File "/usr/lib/python2.7/dist-packages/dbus/_dbus.py", line 194, in __new__
    private=private)
  File "/usr/lib/python2.7/dist-packages/dbus/_dbus.py", line 100, in __new__
    bus = BusConnection.__new__(subclass, bus_type, mainloop=mainloop)
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 122, in __new__
    bus = cls._new_for_bus(address_or_type, mainloop=mainloop)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.AccessDenied: Failed to connect to socket /var/run/dbus/system_bus_socket: Permission denied
```

---

### Post by kc1di on 2019-01-04
It looks like your running out of disk space and thus the install can not be completed.  How big is the Partition you are installing to?
please list the output of ```
sudo fdisk -l
```

---

### Post by generalghest on 2019-01-04
**```
dextop@localhost:~$ sudo fdisk -l 
```** ```

[sudo] password for dextop: 
```
```
  
```
[B]```
dextop@localhost:~$ sudo fdisk -l 
``` 
[/B] ```
  
```[B]
```
dextop@localhost:~$ sudo fdisk /dev/sdaX
```[/B] ```

Welcome to fdisk (util-linux 2.27.1)
Changes wiill remain in memory only, until you decide to write them.
Be careful before using the write command.

fdisk: cannot open /dev/sdaX: No such file or directory 
```

---

### Post by clementc on 2019-01-04
Hi [**[COLOR=#000000]generalghest[/COLOR]**]("https://ubuntuforums.org/member.php?u=2115439"),

Can you please run the following command and provide its output:

df -H

---

### Post by generalghest on 2019-01-04
```
 dextop@localhost:~$ df -H
Filesystem               Size  Used Avail Use% Mounted on
/dev/block/loop7          11G   11G   30M 100% /
/data/media/0/LoD_Share   57G   21G   36G  37% /int_sd
tmpfs                    1.8G     0  1.8G   0% /devro
tmpfs                    1.8G     0  1.8G   0% /devro/shm
tmpfs                    1.8G     0  1.8G   0% /ext_sd
tmpfs                    1.8G     0  1.8G   0% /dev
tmpfs                    1.8G  4.1k  1.8G   1% /tmp
tmpfs                    1.8G   33k  1.8G   1% /run
/dev/block/dm-3           57G   21G   36G  37% /share/run 
```

Please pay attention that when I enter [COLOR=#000000][FONT=&amp]sudo fdisk -l and enter the password nothing happens and I get empty output
[/FONT][/COLOR]
Oh, I see that memory is full. I will increase it and I'll try again.
**upd: After increasing memory **
```
dextop@localhost:~$ df -H
Filesystem               Size  Used Avail Use% Mounted on
/dev/block/loop7          22G   11G   12G  48% /
/data/media/0/LoD_Share   57G   33G   24G  58% /int_sd
tmpfs                    1.8G     0  1.8G   0% /devro
tmpfs                    1.8G   25M  1.8G   2% /devro/shm
tmpfs                    1.8G     0  1.8G   0% /ext_sd
tmpfs                    1.8G     0  1.8G   0% /dev
tmpfs                    1.8G  4.1k  1.8G   1% /tmp
tmpfs                    1.8G   25k  1.8G   1% /run
/dev/block/dm-3           57G   33G   24G  58% /share/run

```

---

### Post by generalghest on 2019-01-05
i have increased memory and I was get it:
```
dextop@localhost:~$ sudo apt install software-center 
```
```
[sudo] password for dextop: 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.  
```
```
dextop@localhost:~$ sudo dpkg --configure -a 
```
```
Processing triggers for libc-bin (2.23-0ubuntu10) ...
Processing triggers for dbus (1.10.6-1ubuntu3.3) ...
dextop@localhost:~$ sudo apt install software-center
Reading package lists... Done
Building dependency tree       
Reading state information... Done
software-center is already the newest version (16.01+16.04.20160420).
The following packages were automatically installed and are no longer required:
  apg appstream cups-pk-helper gkbd-capplet gnome-software-common
  libappstream3 libdbusmenu-gtk4 libfm-data libfm-extra4 libfm-gtk-data
  libfm-gtk4 libfm-modules libfm4 libgeonames0 libgnomekbd8 libgtkspell3-3-0
  libkeybinder0 libllvm5.0 libmenu-cache-bin libmenu-cache3 libqpdf17 libsbc1
  libsnapd-glib1 libtimezonemap-data libtimezonemap1 libwnck-common libwnck22
  linux-headers-4.4.0-119 linux-headers-4.4.0-119-generic
  linux-headers-4.4.0-131 linux-headers-4.4.0-131-generic
  linux-headers-4.4.0-135 linux-headers-4.4.0-135-generic
  linux-headers-4.4.0-137 linux-headers-4.4.0-137-generic
  linux-image-4.4.0-119-generic linux-image-4.4.0-131-generic
  linux-image-4.4.0-135-generic linux-image-4.4.0-137-generic lxmenu-data
  lxpanel-data signon-keyring-extension snapd-login-service
  ubuntu-system-service unity-control-center-faces
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 25 not upgraded. 
```
```
dextop@localhost:~$ software-center 
```
```
/usr/bin/software-center:25: PyGIWarning: Gtk was imported without specifying a version first. Use gi.require_version('Gtk', '3.0') before import to ensure that the right version gets loaded.
  from gi.repository import Gtk, GObject
2019-01-05 11:57:04,244 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/share/software-center/softwarecenter/netstatus.py', 122, '__init_network_state')'
2019-01-05 11:57:04,244 - root - WARNING - failed to init network state watcher 'org.freedesktop.DBus.Error.AccessDenied: Failed to connect to socket /var/run/dbus/system_bus_socket: Permission denied'
/usr/share/software-center/softwarecenter/ui/gtk3/views/purchaseview.py:29: PyGIWarning: WebKit2 was imported without specifying a version first. Use gi.require_version('WebKit2', '4.0') before import to ensure that the right version gets loaded.
  from gi.repository import WebKit2 as webkit
2019-01-05 11:57:05,163 - softwarecenter.backend.zeitgeist_logger - WARNING - Support for Zeitgeist disabled
/usr/share/software-center/softwarecenter/ui/gtk3/widgets/symbolic_icons.py:23: PyGIWarning: PangoCairo was imported without specifying a version first. Use gi.require_version('PangoCairo', '1.0') before import to ensure that the right version gets loaded.
  from gi.repository import Gtk, Gdk, GLib, PangoCairo
2019-01-05 11:57:05,197 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/share/software-center/softwarecenter/netstatus.py', 144, 'test_ping')'
2019-01-05 11:57:05,196 - root - INFO - Attempting one time ping of screenshots.ubuntu.com to test if internet connectivity exists.
2019-01-05 11:57:05,319 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/share/software-center/softwarecenter/netstatus.py', 160, 'test_ping')'
2019-01-05 11:57:05,319 - root - INFO - ping output: 'Could not detect an internet connection
ping: icmp open socket: Operation not permitted
'
2019-01-05 11:57:05,346 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2019-01-05 11:57:05,367 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py', 151, '__init__')'
2019-01-05 11:57:05,367 - root - ERROR - Can not get aptdaemon client: 'org.freedesktop.DBus.Error.AccessDenied: Failed to connect to socket /var/run/dbus/system_bus_socket: Permission denied', no size information will be available 
2019-01-05 11:57:05,386 - softwarecenter.ui.gtk3.app - INFO - building local database
2019-01-05 11:57:05,386 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
2019-01-05 11:57:06,005 - softwarecenter.db.update - WARNING - Cannot write to '/var/cache/software-center/xapian'.
2019-01-05 11:57:06,007 - softwarecenter.db.update - WARNING - Please check you have the relevant permissions.
Traceback (most recent call last):
  File "/usr/bin/software-center", line 130, in <module>
    app = SoftwareCenterAppGtk3(options, args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 329, in __init__
    self.backend = get_install_backend()
  File "/usr/share/software-center/softwarecenter/backend/installbackend.py", line 88, in get_install_backend
    install_backend = AptdaemonBackend()
  File "/usr/share/software-center/softwarecenter/backend/installbackend_impl/aptd.py", line 226, in __init__
    bus = get_dbus_bus()
  File "/usr/share/software-center/softwarecenter/backend/installbackend_impl/aptd.py", line 77, in get_dbus_bus
    bus = dbus.SystemBus()
  File "/usr/lib/python2.7/dist-packages/dbus/_dbus.py", line 194, in __new__
    private=private)
  File "/usr/lib/python2.7/dist-packages/dbus/_dbus.py", line 100, in __new__
    bus = BusConnection.__new__(subclass, bus_type, mainloop=mainloop)
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 122, in __new__
    bus = cls._new_for_bus(address_or_type, mainloop=mainloop)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.AccessDenied: Failed to connect to socket /var/run/dbus/system_bus_socket: Permission denied


dextop@localhost:~$   from gi.repository import Gtk, GObject
 from: can't read /var/mail/gi.repository
dextop@localhost:~$ 2019-01-05 11:57:04,244 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/share/software-center/softwarecenter/netstatus.py', 122, '__init_network_state')'
 root 2019-01-05: command not found
dextop@localhost:~$ 2019-01-05 11:57:04,244 - root - WARNING - failed to init network state watcher 'org.freedesktop.DBus.Error.AccessDenied: Failed to connect to socket /var/run/dbus/system_bus_socket: Permission denied'
net conn2019-01-05: command not found
dextop@localhost:~$ /usr/share/software-center/softwarecenter/ui/gtk3/views/purchaseview.py:29: PyGIWarning: WebKit2 was imported without specifying a version first. Use gi.require_version('WebKit2', '4.0') before import to ensure that the right version gets loaded.
bash: syntax error near unexpected token `('
dextop@localhost:~$   from gi.repository import WebKit2 as webkit
ect an internet connection
ping: icmp open socfrom: can't read /var/mail/gi.repository
dextop@localhost:~$ 2019-01-05 11:57:05,163 - softwarecenter.backend.zeitgeist_logger - WARNING - Support for Zeitgeist disabled
 proxy2019-01-05: command not found
dextop@localhost:~$ /usr/share/software-center/softwarecenter/ui/gtk3/widgets/symbolic_icons.py:23: PyGIWarning: PangoCairo was imported without specifying a version first. Use gi.require_version('PangoCairo', '1.0') before import to ensure that the right version gets loaded.
bash: syntax error near unexpected token `('
dextop@localhost:~$   from gi.repository import Gtk, Gdk, GLib, PangoCairo
nfrom: can't read /var/mail/gi.repository
dextop@localhost:~$ 2019-01-05 11:57:05,197 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/share/software-center/softwarecenter/netstatus.py', 144, 'test_ping')'
N2019-01-05: command not found
dextop@localhost:~$ 2019-01-05 11:57:05,196 - root - INFO - Attempting one time ping of screenshots.ubuntu.com to test if internet connectivity exists.
05 12019-01-05: command not found
dextop@localhost:~$ 2019-01-05 11:57:05,319 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/share/software-center/softwarecenter/netstatus.py', 160, 'test_ping')'
1:57:06,007 - softwarecenter.db.update - WARNIN2019-01-05: command not found
dextop@localhost:~$ 2019-01-05 11:57:05,319 - root - INFO - ping output: 'Could not detect an internet connection
 last):
  File > ping: icmp open socket: Operation not permitted
> '
2019-01-05: command not found
dextop@localhost:~$ 2019-01-05 11:57:05,346 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
args)
  File "/usr/share/software-center/soft2019-01-05: command not found
dextop@localhost:~$ 2019-01-05 11:57:05,367 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py', 151, '__init__')'
2019-01-05: command not found
dextop@localhost:~$ 2019-01-05 11:57:05,367 - root - ERROR - Can not get aptdaemon client: 'org.freedesktop.DBus.Error.AccessDenied: Failed to connect to socket /var/run/dbus/system_bus_socket: Permission denied', no size information will be available 
2019-01-05: command not found
dextop@localhost:~$ 2019-01-05 11:57:05,386 - softwarecenter.ui.gtk3.app - INFO - building local database
2019-01-05: command not found
dextop@localhost:~$ 2019-01-05 11:57:05,386 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
bash: syntax error near unexpected token `('
dextop@localhost:~$ 2019-01-05 11:57:06,005 - softwarecenter.db.update - WARNING - Cannot write to '/var/cache/software-center/xapian'.
2019-01-05: command not found
dextop@localhost:~$ 2019-01-05 11:57:06,007 - softwarecenter.db.update - WARNING - Please check you have the relevant permissions.
2019-01-05: command not found
dextop@localhost:~$ Traceback (most recent call last):
bash: syntax error near unexpected token `most'
dextop@localhost:~$   File "/usr/bin/software-center", line 130, in <module>
bash: syntax error near unexpected token `newline'
dextop@localhost:~$     app = SoftwareCenterAppGtk3(options, args)
bash: syntax error near unexpected token `('
dextop@localhost:~$   File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 329, in __init__
No command 'File' found, did you mean:
 Command 'kile' from package 'kile' (universe)
 Command 'file' from package 'file' (main)
 Command 'vile' from package 'vile' (universe)
 Command 'zile' from package 'zile' (universe)
File: command not found
dextop@localhost:~$     self.backend = get_install_backend()
bash: syntax error near unexpected token `('
dextop@localhost:~$   File "/usr/share/software-center/softwarecenter/backend/installbackend.py", line 88, in get_install_backend
No command 'File' found, did you mean:
 Command 'zile' from package 'zile' (universe)
 Command 'kile' from package 'kile' (universe)
 Command 'vile' from package 'vile' (universe)
 Command 'file' from package 'file' (main)
File: command not found
dextop@localhost:~$     install_backend = AptdaemonBackend()
bash: syntax error near unexpected token `('
dextop@localhost:~$   File "/usr/ that the right version gets loaded.
>   from gi.repository import Gtk, GObject
> 2019-01-05 11:57:04,244 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/share/software-center/softwarecenter/netstatus.py', 122, '__init_network_state')'
> 2019-01-05 11:57:04,244 - root - WARNING - failed to init network state watcher 'org.freedesktop.DBus.Error.AccessDenied: Failed to connect to socket /var/run/dbus/system_bus_socket: Permission denied'
> /usr/share/software-center/softwarecenter/ui/gtk3/views/purchaseview.py:29: PyGIWarning: WebKit2 was imported without specifying a version first. Use gi.require_version('WebKit2', '4.0') before import to ensure that the right version gets loaded.
>   from gi.repository import WebKit2 as webkit
> 2019-01-05 11:57:05,163 - softwarecenter.backend.zeitgeist_logger - WARNING - Support for Zeitgeist disabled
> /usr/share/software-center/softwarecenter/ui/gtk3/widgets/symbolic_icons.py:23: PyGIWarning: PangoCairo was imported without specifying a version first. Use gi.require_version('PangoCairo', '1.0') before import to ensure that the right version gets loaded.
>   from gi.repository import Gtk, Gdk, GLib, PangoCairo
> 2019-01-05 11:57:05,197 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/share/software-center/softwarecenter/netstatus.py', 144, 'test_ping')'
> 2019-01-05 11:57:05,196 - root - INFO - Attempting one time ping of screenshots.ubuntu.com to test if internet connectivity exists.
> 2019-01-05 11:57:05,319 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/share/software-center/softwarecenter/netstatus.py', 160, 'test_ping')'
> 2019-01-05 11:57:05,319 - root - INFO - ping output: 'Could not detect an internet connection
> ping: icmp open socket: Operation not permitted
> '
> 2019-01-05 11:57:05,346 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
> 2019-01-05 11:57:05,367 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py', 151, '__init__')'
> 2019-01-05 11:57:05,367 - root - ERROR - Can not get aptdaemon client: 'org.freedesktop.DBus.Error.AccessDenied: Failed to connect to socket /var/run/dbus/system_bus_socket: Permission denied', no size information will be available 
> 2019-01-05 11:57:05,386 - softwarecenter.ui.gtk3.app - INFO - building local database
> 2019-01-05 11:57:05,386 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
> 2019-01-05 11:57:06,005 - softwarecenter.db.update - WARNING - Cannot write to '/var/cache/software-center/xapian'.
> 2019-01-05 11:57:06,007 - softwarecenter.db.update - WARNING - Please check you have the relevant permissions.
> Traceback (most recent call last):
>   File "/usr/bin/software-center", line 130, in <module>
>     app = SoftwareCenterAppGtk3(options, args)
>   File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 329, in __init__
>     self.backend = get_install_backend()
>   File "/usr/share/software-center/softwarecenter/backend/installbackend.py", line 88, in get_install_backend
>     install_backend = AptdaemonBackend()
> ilil  File "/usr//usr/share/software-center/softwarecenter/ui/gtk3/views/purchaseview.py/usr/share/software-center/softwarecenter/ui/gtk3/views/purchaseview.py
No command 'File' found, did you mean:
 Command 'file' from package 'file' (main)
 Command 'vile' from package 'vile' (universe)
 Command 'zile' from package 'zile' (universe)
 Command 'kile' from package 'kile' (universe)
File: command not found

```
I see icon of program software-center but when I clicked on it program is launch but I see nothing on display

---

### Post by generalghest on 2019-01-05
When I try to install wine I get it:
```
dextop@localhost:~$ sudo dpkg --add-architecture i386 
```
```
[sudo] password for dextop: 
```
```
dextop@localhost:~$ sudo add-apt-repository ppa:wine/wine-builds && sudo apt-get update 
```
```
 !!! PLEASE NOTE THAT THIS REPOSITORY IS DEPRECATED !!!


For more information, please see:


    https://www.winehq.org/pipermail/wine-devel/2017-March/117104.html


The following commands can be used to add the new repository:


    wget https://dl.winehq.org/wine-builds/Release.key
    sudo apt-key add Release.key
    sudo apt-add-repository 'https://dl.winehq.org/wine-builds/ubuntu/'


 More info: https://launchpad.net/~wine/+archive/ubuntu/wine-builds
Press [ENTER] to continue or ctrl-c to cancel adding it


gpg: keyring `/tmp/tmpunhj8iou/secring.gpg' created
gpg: keyring `/tmp/tmpunhj8iou/pubring.gpg' created
gpg: requesting key 77C899CB from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpunhj8iou/trustdb.gpg: trustdb created
gpg: key 77C899CB: public key "Launchpad PPA for Wine" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
Hit:1 http://ports.ubuntu.com/ubuntu-ports xenial InRelease
Get:2 http://ports.ubuntu.com/ubuntu-ports xenial-updates InRelease [109 kB]
Hit:5 https://deb.nodesource.com/node_8.x xenial InRelease       
Get:3 http://ports.ubuntu.com/ubuntu-ports xenial-backports InRelease [107 kB]
Get:4 http://ports.ubuntu.com/ubuntu-ports xenial-security InRelease [107 kB]
Ign:7 http://ports.ubuntu.com/ubuntu-ports xenial/main i386 Packages
Hit:8 http://ppa.launchpad.net/alexlarsson/flatpak/ubuntu xenial InRelease
Ign:9 http://ports.ubuntu.com/ubuntu-ports xenial/restricted i386 Packages
Ign:10 http://ports.ubuntu.com/ubuntu-ports xenial/universe i386 Packages
Hit:11 http://ppa.launchpad.net/wine/wine-builds/ubuntu xenial InRelease
Ign:12 http://ports.ubuntu.com/ubuntu-ports xenial/multiverse i386 Packages
Ign:7 http://ports.ubuntu.com/ubuntu-ports xenial/main i386 Packages
Get:13 http://ports.ubuntu.com/ubuntu-ports xenial-updates/main arm64 Packages [683 kB]
Ign:14 http://ports.ubuntu.com/ubuntu-ports xenial-updates/main i386 Packages
Get:15 http://ports.ubuntu.com/ubuntu-ports xenial-updates/main Translation-en [363 kB]
Get:16 http://ports.ubuntu.com/ubuntu-ports xenial-updates/main arm64 DEP-11 Metadata [320 kB]
Err:6 https://dl.winehq.org/wine-builds/ubuntu xenial InRelease  
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 76F1A20FF987672F
Get:17 http://ports.ubuntu.com/ubuntu-ports xenial-updates/main DEP-11 64x64 Icons [227 kB]
Ign:18 http://ports.ubuntu.com/ubuntu-ports xenial-updates/restricted i386 Packages
Get:19 http://ports.ubuntu.com/ubuntu-ports xenial-updates/universe arm64 Packages [640 kB]
Ign:20 http://ports.ubuntu.com/ubuntu-ports xenial-updates/universe i386 Packages
Get:21 http://ports.ubuntu.com/ubuntu-ports xenial-updates/universe Translation-en [294 kB]
Get:22 http://ports.ubuntu.com/ubuntu-ports xenial-updates/universe arm64 DEP-11 Metadata [251 kB]
Get:23 http://ports.ubuntu.com/ubuntu-ports xenial-updates/universe DEP-11 64x64 Icons [343 kB]
Ign:24 http://ports.ubuntu.com/ubuntu-ports xenial-updates/multiverse i386 Packages
Get:25 http://ports.ubuntu.com/ubuntu-ports xenial-updates/multiverse arm64 DEP-11 Metadata [4,068 B]
Get:26 http://ports.ubuntu.com/ubuntu-ports xenial-updates/multiverse DEP-11 64x64 Icons [14.3 kB]
Ign:9 http://ports.ubuntu.com/ubuntu-ports xenial/restricted i386 Packages
Ign:10 http://ports.ubuntu.com/ubuntu-ports xenial/universe i386 Packages
Ign:12 http://ports.ubuntu.com/ubuntu-ports xenial/multiverse i386 Packages
Ign:7 http://ports.ubuntu.com/ubuntu-ports xenial/main i386 Packages
Ign:14 http://ports.ubuntu.com/ubuntu-ports xenial-updates/main i386 Packages
Ign:18 http://ports.ubuntu.com/ubuntu-ports xenial-updates/restricted i386 Packages
Get:27 http://ports.ubuntu.com/ubuntu-ports xenial-backports/main arm64 Packages [7,272 B]
Ign:28 http://ports.ubuntu.com/ubuntu-ports xenial-backports/main i386 Packages
Get:29 http://ports.ubuntu.com/ubuntu-ports xenial-backports/main arm64 DEP-11 Metadata [3,324 B]
Ign:30 http://ports.ubuntu.com/ubuntu-ports xenial-backports/universe i386 Packages
Get:31 http://ports.ubuntu.com/ubuntu-ports xenial-backports/universe arm64 DEP-11 Metadata [5,104 B]
Ign:20 http://ports.ubuntu.com/ubuntu-ports xenial-updates/universe i386 Packages
Get:32 http://ports.ubuntu.com/ubuntu-ports xenial-security/main arm64 Packages [410 kB]
Ign:33 http://ports.ubuntu.com/ubuntu-ports xenial-security/main i386 Packages
Get:34 http://ports.ubuntu.com/ubuntu-ports xenial-security/main Translation-en [248 kB]
Get:35 http://ports.ubuntu.com/ubuntu-ports xenial-security/main arm64 DEP-11 Metadata [67.7 kB]
Get:36 http://ports.ubuntu.com/ubuntu-ports xenial-security/main DEP-11 64x64 Icons [68.0 kB]
Ign:37 http://ports.ubuntu.com/ubuntu-ports xenial-security/restricted i386 Packages
Get:38 http://ports.ubuntu.com/ubuntu-ports xenial-security/universe arm64 Packages [357 kB]
Ign:39 http://ports.ubuntu.com/ubuntu-ports xenial-security/universe i386 Packages
Get:40 http://ports.ubuntu.com/ubuntu-ports xenial-security/universe Translation-en [161 kB]
Get:41 http://ports.ubuntu.com/ubuntu-ports xenial-security/universe arm64 DEP-11 Metadata [109 kB]
Get:42 http://ports.ubuntu.com/ubuntu-ports xenial-security/universe DEP-11 64x64 Icons [158 kB]
Ign:43 http://ports.ubuntu.com/ubuntu-ports xenial-security/multiverse i386 Packages
Ign:24 http://ports.ubuntu.com/ubuntu-ports xenial-updates/multiverse i386 Packages
Ign:9 http://ports.ubuntu.com/ubuntu-ports xenial/restricted i386 Packages
Ign:10 http://ports.ubuntu.com/ubuntu-ports xenial/universe i386 Packages
Ign:12 http://ports.ubuntu.com/ubuntu-ports xenial/multiverse i386 Packages
Err:7 http://ports.ubuntu.com/ubuntu-ports xenial/main i386 Packages
  404  Not Found [IP: 91.189.88.150 80]
Ign:14 http://ports.ubuntu.com/ubuntu-ports xenial-updates/main i386 Packages
Ign:18 http://ports.ubuntu.com/ubuntu-ports xenial-updates/restricted i386 Packages
Ign:28 http://ports.ubuntu.com/ubuntu-ports xenial-backports/main i386 Packages
Ign:30 http://ports.ubuntu.com/ubuntu-ports xenial-backports/universe i386 Packages
Ign:20 http://ports.ubuntu.com/ubuntu-ports xenial-updates/universe i386 Packages
Ign:33 http://ports.ubuntu.com/ubuntu-ports xenial-security/main i386 Packages
Ign:37 http://ports.ubuntu.com/ubuntu-ports xenial-security/restricted i386 Packages
Ign:39 http://ports.ubuntu.com/ubuntu-ports xenial-security/universe i386 Packages
Ign:43 http://ports.ubuntu.com/ubuntu-ports xenial-security/multiverse i386 Packages
Ign:24 http://ports.ubuntu.com/ubuntu-ports xenial-updates/multiverse i386 Packages
Err:14 http://ports.ubuntu.com/ubuntu-ports xenial-updates/main i386 Packages
  404  Not Found [IP: 91.189.88.150 80]
Ign:18 http://ports.ubuntu.com/ubuntu-ports xenial-updates/restricted i386 Packages
Ign:28 http://ports.ubuntu.com/ubuntu-ports xenial-backports/main i386 Packages
Ign:30 http://ports.ubuntu.com/ubuntu-ports xenial-backports/universe i386 Packages
Ign:20 http://ports.ubuntu.com/ubuntu-ports xenial-updates/universe i386 Packages
Ign:33 http://ports.ubuntu.com/ubuntu-ports xenial-security/main i386 Packages
Ign:37 http://ports.ubuntu.com/ubuntu-ports xenial-security/restricted i386 Packages
Ign:39 http://ports.ubuntu.com/ubuntu-ports xenial-security/universe i386 Packages
Ign:43 http://ports.ubuntu.com/ubuntu-ports xenial-security/multiverse i386 Packages
Ign:24 http://ports.ubuntu.com/ubuntu-ports xenial-updates/multiverse i386 Packages
Err:28 http://ports.ubuntu.com/ubuntu-ports xenial-backports/main i386 Packages
  404  Not Found [IP: 91.189.88.150 80]
Ign:30 http://ports.ubuntu.com/ubuntu-ports xenial-backports/universe i386 Packages
Err:33 http://ports.ubuntu.com/ubuntu-ports xenial-security/main i386 Packages
  404  Not Found [IP: 91.189.88.150 80]
Ign:37 http://ports.ubuntu.com/ubuntu-ports xenial-security/restricted i386 Packages
Ign:39 http://ports.ubuntu.com/ubuntu-ports xenial-security/universe i386 Packages
Ign:43 http://ports.ubuntu.com/ubuntu-ports xenial-security/multiverse i386 Packages
Fetched 323 kB in 9s (34.2 kB/s)                                 
Reading package lists... Done
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: https://dl.winehq.org/wine-builds/ubuntu xenial InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 76F1A20FF987672F
W: Failed to fetch https://dl.winehq.org/wine-builds/ubuntu/dists/xenial/InRelease  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 76F1A20FF987672F
E: Failed to fetch http://ports.ubuntu.com/ubuntu-ports/dists/xenial/main/binary-i386/Packages  404  Not Found [IP: 91.189.88.150 80]
E: Failed to fetch http://ports.ubuntu.com/ubuntu-ports/dists/xenial-updates/main/binary-i386/Packages  404  Not Found [IP: 91.189.88.150 80]
E: Failed to fetch http://ports.ubuntu.com/ubuntu-ports/dists/xenial-backports/main/binary-i386/Packages  404  Not Found [IP: 91.189.88.150 80]
E: Failed to fetch http://ports.ubuntu.com/ubuntu-ports/dists/xenial-security/main/binary-i386/Packages  404  Not Found [IP: 91.189.88.150 80]
W: Some index files failed to download. They have been ignored, or old ones used instead.
[code]dextop@localhost:~$ sudo apt-get install --install-recommends winehq-devel 
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 winehq-devel:i386 : Depends: wine-devel:i386 (= 4.0~rc2~xenial) but it is not going to be installed
E: Unable to correct problems, you have held broken packages. [/code]
```
dextop@localhost:~$ winecfg
```
```
winecfg: command not found
```

---

### Post by kc1di on 2019-01-05
drop the X in the command should look like fdisk /dev/sda or fdisk /dev/sdb  ETC.

At this point you may want to try Playonlinux it's in the repository and will allow you to install multiple versions of wine.

---

### Post by generalghest on 2019-01-05
Also today I have tried to install Netbeans. Installing is successful but program does not launch. 
```
dextop@localhost:~$ netbeans
```
```
Unrecognized option: -client
Error: Could not create the Java Virtual Machine.
Error: A fatal exception has occurred. Program will exit.
```

---

