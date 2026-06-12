---
title: "How do I update to flight?"
date: 2006-01-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by matthedane on 2006-01-21
Hi

I have spent quite some time googeling the web trying to find out how to update from breezy to Dapper flight 3. I have all my important data on a different partition running Mandrake, so even if something should go wrong on the Kubuntu-partition there will be no reason to panic...

Also I should mentions that I am running AMD64.

So far I have found several forums saying that the distro-upgrade is very easy, but non of them gave me the directions. I hope somebody can help... 

Matt

---

### Post by 23meg on 2006-01-21
If you're using any pre-Dapper release just upgrade it to Dapper as usual.

---

### Post by matthedane on 2006-01-25
Well... for me the "usual" approach is to download the CD, burn it and then install it. However I believe it is possible to install Dapper from an internet mirror. I just haven't been able to find any directions on that topic.

Matt

---

### Post by jnorth on 2006-01-25
Likewise for me... I'm used to Debian where I could change my apt sources to get the testing release.  Anyone?

---

### Post by chiisu on 2006-02-04
I assume you just edit your sources and change "breezy" to dapper", then do "apt-get update" and "apt-get dist-upgrade"

---

### Post by matthedane on 2006-02-05
Thanks. It works fine. I didn't expect it to be that easy... Downloading with 50 kb/sec it takes about 2 hours to do the upgrade.

Mathias

---

### Post by CyberAngel on 2006-02-16
[QUOTE=chiisu]I assume you just edit your sources and change "breezy" to dapper", then do "apt-get update" and "apt-get dist-upgrade"[/QUOTE]


I have done that but that`s what I`m getting....

```
......1182 upgraded, 134 newly installed, 250 to remove and 33 not upgraded.
Need to get 665MB of archives.
After unpacking 559MB disk space will be freed.

```

Why needs to remove 250 packages?????
Is everything going to work fine after this update??
I don`t think so....

I am pasting below the full list of packages that needs to be removed and installed..
As I can see it removes programs such as amarok,k3b,cinepaint but it doesn`t install them again...

```
The following packages will be REMOVED:
  adept akode akode-mpeg akregator amarok amarok-gstreamer ark artsbuilder base-config bug-buddy busybox-cvs-initramfs
  cinepaint cupsys-driver-gimpprint-data dbus dcgui digikam digikamimageplugins eog evince evolution-data-server
  file-roller gcalctool gconf-editor gedit gnome-about gnome-applets gnome-control-center gnome-games gnome-gv gnome-media
  gnome-netstatus-applet gnome-panel gnome-session gnome-system-monitor gnome-system-tools gnome-terminal gnome-utils
  gnome-volume-manager gnomebaker gnomemeeting gstreamer0.8-jack gtk2-engines-gtk-qt gtkhtml3.8 gucharmap gwenview hal
  hotplug hplip-base ivman k3b k3b-mp3 k3blibs kaddressbook kaddressbook-plugins kaffeine kaffeine-gstreamer kaffeine-xine
  kamera kappfinder karm katapult kate kaudiocreator kcontrol kcron kdat kde-guidance kde-i18n-el kde-style-lipstik
  kde-systemsettings kdeadmin kdeadmin-kfile-plugins kdeartwork kdeartwork-style kdeartwork-theme-window kdebase-bin
  kdebase-dev kdebase-kio-plugins kdebluetooth kdegraphics-kfile-plugins kdelibs kdelibs-bin kdelibs4-dev kdelibs4c2
  kdelirc kdemultimedia-kappfinder-data kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing
  kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint kdesktop kdm kfind
  kghostview khelpcenter kicker kid3 kio-apt kio-locate kipi-plugins klaptopdaemon klipper kmail kmenuedit kmilo kmix knemo
  knetworkconf knode knotes koffice-libs kolourpaint konq-plugins konqueror konqueror-nsplugins konserve konsole kontact
  konversation kooka kopete korganizer kpackage kpdf kpf kppp krdc krename krusader kscd kscreensaver kscreensaver-xsavers
  ksmserver ksnapshot ksplash kspread kstars kstreamripper ksvg ksysguard ksystemlog ksysv kthesaurus
  kubuntu-default-settings kubuntu-docs kubuntu-konqueror-shortcuts kuser kwalletmanager kwifimanager kwin kwin-baghira
  kword kxdocker kxdocker-data kynaptic libarts1-xine libarts1c2 libavifile-0.7 libbonoboui2-0 libbonoboui2-dev
  libcamel1.2-6 libebook1.2-5 libecal1.2-3 libedata-book1.2-2 libedata-cal1.2-1 libedataserver1.2-4 libedataserverui1.2-6
  libeel2-2 libegroupwise1.2-8 libenchant1c2 libgcj6-common libgdchart-gd1-noxpm libgksuui1.0-0 libglibmm-2.4-1c2
  libgnome-desktop-2 libgnome2-0 libgnome2-dev libgnome2-perl libgnomemm2.0-1c2 libgnomemm2.0-dev libgnomeui-0
  libgnomeui-dev libgnomeuimm2.0-1c2 libgnomeuimm2.0-dev libgtkhtml3.8-15 libgtkmm-2.4-1c2 libgucharmap4 libid3-3.8.3c2
  libjack0.80.0-0 libkcal2b libkcddb1 libkdeedu3 libkdepim1a libkexif1 libkipi0 libkleopatra1 libkmime2 libkonq4
  libkpimexchange1 libkpimidentities1 libkscan1 libksieve0 libktnef1 liblpint-bonobo0 libmimelib1c2 libmusicbrainz4c2
  libnids1 libnotify0 libopenexr2c2 libopenh323-1.15.3c2 libpanel-applet2-0 libpt-1.8.3c2 libqt4-dev libsigc++-2.0-0c2
  libtag1c2 libtunepimp2c2 mesa-doc mozilla-thunderbird-enigmail mozilla-thunderbird-offline nautilus nautilus-cd-burner
  nvidia-glx okle ontv python-gdchart python-gnome2 python-gnome2-extras python-kde3 python2.4-gnome2
  python2.4-gnome2-extras python2.4-kde3 sanekonsole secpolicy smb4k sound-juicer superkaramba totem totem-xine tsclient
  vino x-common xmkmf xorg-common xserver-common yakuake
The following NEW packages will be installed:
  amule-common busybox-initramfs ca-certificates cupsys-driver-gutenprint foomatic-db-gutenprint gconf2-common gdk-imlib11
  gettext-kde gstreamer0.10-alsa gstreamer0.10-plugins-base gstreamer0.10-plugins-good hplip ijsgutenprint irssi
  kdesdk-scripts laptop-mode-tools libarts1c2a libavifile-0.7c2 libbeecrypt6 libc6-i386 libcamel1.2-8 libcdio6
  libconvert-binhex-perl libcrypt-ssleay-perl libcupsys2 libcurl3-gnutls libdbus-1-2 libdbus-1-dev libdbus-glib-1-2 libdmx1
  libdns21 libdrm2 libdvbpsi4 libedataserver1.2-7 libegroupwise1.2-9 libenchant1c2a libfcgi-perl libgcj6-jar
  libgdchart-gd2-noxpm libgksuui1.0-1 libgmp3c2 libgnutls12 libgsf-1-113 libgsf-1-common libgstreamer-plugins-base0.10-0
  libgstreamer0.10-0 libgtk2-gladexml-perl libgtkextra-1.0-0 libgtop2-7 libgutenprint2 libid3-3.8.3c2a
  libio-socket-ssl-perl libisc11 libiso9660-4 libjack0.100.0-0 libkpathsea4 liblwres9 libmagick9 libmailtools-perl
  libmime-lite-perl libmime-perl libmono0 libmusicbrainz4c2a libnautilus-burn3 libneon25 libnet-ssleay-perl libnids1.20
  libnotify1 libopenexr2c2a libopenh323-1.15.6 libossp-uuid-perl libossp-uuid13 libparted1.6-13 libpcrecpp0 libpt-1.8.7
  libsepol1 libsgutils1 libsigc++-2.0-0c2a libsnmp9 libssl0.9.8 libsysfs2 libtag1c2a libtext-unaccent-perl libtimedate-perl
  libtunepimp2c2a libuniconf4.2 libwavpack0 libwvstreams4.2-base libwvstreams4.2-extras libxdmcp-dev libxine-extracodecs
  libxine-main1 libxp-dev libxplc0.3.13 linux-image-2.6.15-14-amd64-k8 mcpp mdetect mesa-common-dev mplayer-skins
  pcmciautils python-gobject-dev python-libxml2 python-twisted-conch python-twisted-core python-twisted-lore
  python-twisted-mail python-twisted-names python-twisted-news python-twisted-runner python-twisted-web
  python-twisted-words python2.3-crypto python2.3-twisted-conch python2.3-twisted-core python2.3-twisted-lore
  python2.3-twisted-mail python2.3-twisted-names python2.3-twisted-news python2.3-twisted-runner python2.3-twisted-web
  python2.3-twisted-words python2.4-gobject python2.4-twisted-conch python2.4-twisted-core python2.4-twisted-lore
  python2.4-twisted-mail python2.4-twisted-names python2.4-twisted-news python2.4-twisted-runner python2.4-twisted-web
  python2.4-twisted-words readline-common vbetool x11-common
The following packages have been kept back:
  amule gaim-meanwhile gdk-imlib1 gnome-menus gstreamer0.8-gnomevfs gstreamer0.8-gtk k3b-i18n libavahi-client-dev
  libavahi-common-dev libavahi-qt3-dev libgnome-menu2 libgnomevfs2-0 libgnomevfs2-common libgnomevfs2-dev libgtkmm2.0-dev
  libmysqlclient14 libmysqlclient14-dev libnautilus-extension1 libqt4-debug libqt4-qt3support libqt4-sql libxfcegui4-3
  mplayer python-netcdf python2.4-imaging-tk python2.4-pygame qdvdauthor xfce4 xfce4-mcs-manager xfce4-mcs-plugins
  xfce4-panel xfce4-session xfce4-utils
```

And 1182 will be upgraded..

---

