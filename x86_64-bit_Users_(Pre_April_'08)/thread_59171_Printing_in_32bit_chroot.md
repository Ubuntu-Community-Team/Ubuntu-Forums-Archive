---
title: "Printing in 32bit chroot"
date: 2005-08-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by nosatalian on 2005-08-23
I finally have Firefox setup with all the 32bit plugins in my chroot, but I can only print in my 64bit version.  Is there an easy way to print from within my chroot so I don't have to switch browsers to print?

---

### Post by encinado on 2005-09-05
in your fstab add 
/var on /chroot/var  none bind 0 0

---

### Post by negatory on 2005-09-05
Wich packages should I install in the chroot?I've installed lpr and it didn't work.
If I try to install cupsys and cupsys-client through apt it gives me (in the chroot) these TONS of packages to install first:
```
The following NEW packages will be installed:
  alsa-utils apt apt-utils aspell-bin aspell-en base-files base-passwd bash bc binutils blt bsdutils
  cabextract capplets console-tools coreutils cpio cpp cpp-3.3 cramfsprogs cron cupsys
  cupsys-driver-gimpprint dash dbus-1 dbus-glib-1 debianutils devscripts dmidecode dpkg dselect
  e2fslibs e2fsprogs fakeroot file fontconfig foomatic-db-engine fortune-mod fping freeglut3 gamin
  gawk gcc-3.3-base gconf2 gdm gedit gettext gettext-base gftp-common gftp-gtk gftp-text gksu
  gnome-applets gnome-control-center gnome-keyring gnome-menus gnome-panel gnome-session gnupg grep
  gs-esp gs-gpl gstreamer0.8-gnomevfs gstreamer0.8-misc gstreamer0.8-oss gstreamer0.8-vorbis
  gstreamer0.8-x gtk2-engines-clearlooks gtk2-engines-pixbuf gtk2-engines-redmond95
  gtk2-engines-smooth gtk2-engines-thinice gzip hal hpijs html2text ifupdown ijsgimpprint initscripts
  installwatch iputils-ping kdelibs-bin kdelibs4 laptop-detect lesstif2 libacl1 libadns1 libapm1
  libapt-pkg-perl libart-2.0-2 libarts1 libartsc0 libasound2 libaspell15 libatk1.0-0 libattr1
  libaudio2 libaudiofile0 libauthen-pam-perl libbit-vector-perl libblkid1 libbonobo2-0
  libbonobo2-common libbonoboui2-0 libbz2-1.0 libc6 libc6-dev libcap1 libcarp-clan-perl
  libcdparanoia0 libcomerr2 libconsole libcroco3 libcupsimage2 libcupsys2-gnutls10 libcurl3
  libdate-calc-perl libdb1-compat libdb3 libdb4.2 libdb4.2++ libdmx1 libdps1 libecal1.2-2
  libedataserver1.2-4 libeel2-2 libesd0 libexif10 libexpat1 libfontconfig1 libfreetype6 libfs6
  libgail-common libgail17 libgamin0 libgcc1 libgconf2-4 libgcrypt11 libgd2-noxpm libgdbm3 libgeoip1
  libgimpprint1 libgksu1.2-0 libgksuui1.0-0 libglade2-0 libglib-perl libglib2.0-0 libgnome-desktop-2
  libgnome-keyring0 libgnome-menu0 libgnome2-0 libgnome2-canvas-perl libgnome2-perl
  libgnome2-vfs-perl libgnomecanvas2-0 libgnomecups1.0-1 libgnomeprint2.2-0 libgnomeprintui2.2-0
  libgnomeui-0 libgnomevfs2-0 libgnomevfs2-common libgnutls11 libgpg-error0 libgphoto2-2
  libgphoto2-port0 libgpmg1 libgsf-1 libgstreamer-gconf0.8-0 libgstreamer-plugins0.8-0
  libgstreamer0.8-0 libgtk2-perl libgtk2.0-0 libgtk2.0-bin libgtkhtml2-0 libgtksourceview1.0-0
  libgtkspell0 libgtop2-5 libgucharmap4 libhal-storage0 libhal0 libhtml-parser-perl libice-dev
  libice6 libid3-3.8.3 libidl0 libidn11 libieee1284-3 libijs-0.35 libjasper-1.701-1 libjpeg62
  libkrb53 liblcms1 libldap2 liblircclient0 liblocale-gettext-perl liblzo1 libmagic1 libmetacity0
  libmng1 libmodplug0 libmyspell3 libmysqlclient10 libnautilus-burn1 libnautilus-extension1
  libncurses5 libneon23 libnet-ssleay-perl libnetpbm10 libnewt0.51 libnspr4 libogg0 liboil0.2
  libopencdk8 libopenexr2 liborbit2 libosp4 libostyle1 libpam-modules libpam0g libpanel-applet2-0
  libpango1.0-0 libpango1.0-common libpaper1 libpcap0.8 libpcre3 libperl5.8 libpng12-0 libpopt0
  libpq3 libqt3c102-mt libreadline4 librecode0 librpm4 librsvg2-2 librsvg2-common libsane libsasl2
  libsasl2-modules libscrollkeeper0 libselinux1 libshout3 libslp1 libsm-dev libsm6 libsmbclient
  libsqlite0 libss2 libssl0.9.7 libstartup-notification0 libstdc++5 libstlport4.6 libt1-5 libtasn1-2
  libtext-charwidth-perl libtext-iconv-perl libtiff4 libunicode-string-perl libusb-0.1-4 libuuid1
  libvorbis0a libvorbisenc2 libvorbisfile3 libvte4 libwnck16 libwrap0 libx11-6 libx11-dev libxau-dev
  libxau6 libxaw7 libxaw8 libxcursor1 libxdmcp6 libxext-dev libxext6 libxft2 libxi-dev libxi6
  libxinerama1 libxkbfile-dev libxkbfile1 libxkbui1 libxklavier10 libxml2 libxml2-utils libxmu-dev
  libxmu6 libxmuu-dev libxmuu1 libxosd2 libxp-dev libxp6 libxpm-dev libxpm4 libxrandr-dev libxrandr2
  libxrender-dev libxrender1 libxslt1.1 libxss1 libxt-dev libxt6 libxtrap-dev libxtrap6 libxtst-dev
  libxtst6 libxv-dev libxv1 libxxf86dga1 libxxf86misc1 libxxf86vm1 linux-kernel-headers login
  logrotate lsof m4 make modutils mount ncurses-bin net-tools netkit-inetd netpbm openjade
  openoffice.org-bin openssh-client openssh-server openssl passwd patch pciutils perl perl-base
  powermgmt-base ppp procps pwgen python-apt python-orbit python2.4 python2.4-adns python2.4-dbus
  python2.4-dev python2.4-egenix-mxdatetime python2.4-egenix-mxproxy python2.4-egenix-mxstack
  python2.4-egenix-mxtexttools python2.4-egenix-mxtools python2.4-eunuchs python2.4-gd python2.4-gdbm
  python2.4-geoip python2.4-glade2 python2.4-gnome2 python2.4-gnome2-extras python2.4-gtk2
  python2.4-id3lib python2.4-imaging python2.4-imaging-sane python2.4-kjbuckets python2.4-ldap
  python2.4-libxml2 python2.4-minimal python2.4-mysqldb python2.4-numeric python2.4-opengl
  python2.4-osd python2.4-pam python2.4-pgsql python2.4-pylibacl python2.4-pyopenssl
  python2.4-pyorbit python2.4-pyxattr python2.4-reportlab python2.4-sqlite python2.4-tk
  python2.4-twisted-bin python2.4-xml rpm samba samba-common sane-utils scrollkeeper sed
  shared-mime-info slang1a-utf8 sudo synaptic sysvinit tcl8.4 tcpd tk8.4 totem-gstreamer udev
  usbutils util-linux vim wget whiptail xbase-clients xchat xlibmesa-dri xlibmesa-gl xlibmesa-glu
  xlibmesa3 xlibs-static-dev xpdf-reader xpdf-utils xsltproc xutils zlib1g zlib1g-dev
```
...wich most of them I don't need in the chroot
Thanks
Pedro Carrico

---

### Post by negatory on 2005-09-05
WARNING!
Putting "/var /chroot/var none bind 0 0" on fstab will completely mess up your apt repository in your base system!I really don't recommend doing that...
But maybe experimenting with the spool directory in there I can print using the chroot...I'll try and report here...
If anyone has found the solution please post here
Thanks
Pedro Carrico

---

### Post by encinado on 2005-09-06
I'm very sorry but it if you mount /var in /choot you can print but your apt repository will completely mess . Nothing with :
/var/spool /chroot/var/spool none bind 0 0
/var/run /chroot/var/run none bind 0 0
/var/lib/cups /chroot/var/lib/cups none bind 0 0
/var/log/cups /chroot/var/log/cups none bind 0 0

---

### Post by encinado on 2005-09-06
You don't need mount anything else, just aptitude install cupsys-client and gnome-cups-manager in 32bit chroot and print
 df -h
S.ficheros          Tamaño Usado  Disp Uso% Montado en
/dev/hdb1             144G   31G  107G  23% /
tmpfs                 500M     0  500M   0% /dev/shm
/home                 144G   31G  107G  23% /chroot/home
/tmp                  144G   31G  107G  23% /chroot/tmp
/dev                  5,0M  2,8M  2,3M  55% /chroot/dev
/media/cdrom0         144G   31G  107G  23% /chroot/media/cdrom0
/usr/share/fonts      144G   31G  107G  23% /chroot/usr/share/fonts
/dev                  144G   31G  107G  23% /.dev
none                  5,0M  2,8M  2,3M  55% /dev

---

### Post by negatory on 2005-09-06
Can't get it to work,I've installed everything you said and mounted those directories but when I try to print like I do in the base system It complains "lpr: cannot open /var/spool/lpd/lp/.seq: No such file or directory".The command I use to print in the base system is "/usr/bin/lpr" it should be the same in the chroot right?But that file doesn't even exist in the base system (hence the "No such file or directory" in the "mounted binded" /var/spool).
What is the command you use?
Thanks
Pedro Carrico

---

### Post by rhaurison on 2005-12-01
Install in chrooted: cupsys-client and cupsys-bsd, the cupsys-bsd have the "lpr" for cups. this may be your problem, you are using "lpr" from lpr package. apt will remove lpr.deb when install cupsys-bsd.

---

