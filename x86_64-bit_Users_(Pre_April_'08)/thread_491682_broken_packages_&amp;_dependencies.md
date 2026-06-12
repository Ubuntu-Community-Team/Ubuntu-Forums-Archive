---
title: "broken packages &amp; dependencies"
date: 2007-07-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by darwinmach on 2007-07-03
i need help with a very broken package system...

when i try to install any packages via apt-get, i receive the following:

```

Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  libdbus-1-3: Depends: libc6 (>= 2.5-5) but 2.5-0ubuntu14 is installed
  libdbus-1-dev: Depends: libdbus-1-3 (= 1.0.2-1ubuntu3) but 1.0.2-5ubuntu1 is installed
  libqt4-core: Depends: libc6 (>= 2.5-5) but 2.5-0ubuntu14 is installed
               Depends: libgcc1 (>= 1:4.2-20070516) but 1:4.1.2-0ubuntu4 is installed
               Depends: libglib2.0-0 (>= 2.13.2) but 2.12.11-0ubuntu1 is installed
  libqt4-dev: Depends: libqt4-core (= 4.2.3-0ubuntu3) but 4.3.0-0ubuntu1 is installed
  libstdc++6: Depends: gcc-4.2-base (= 4.2-20070627-1ubuntu1) but it is not installable
              Depends: libc6 (>= 2.5-5) but 2.5-0ubuntu14 is installed
              Depends: libgcc1 (>= 1:4.2-20070516) but 1:4.1.2-0ubuntu4 is installed
  python-dbus: Depends: libc6 (>= 2.5-5) but 2.5-0ubuntu14 is installed
               Depends: libglib2.0-0 (>= 2.13.5) but 2.12.11-0ubuntu1 is installed
  python-qt4-dbus: Depends: libc6 (>= 2.5-5) but 2.5-0ubuntu14 is installed
                   Depends: libgcc1 (>= 1:4.2-20070516) but 1:4.1.2-0ubuntu4 is installed
  python-qt4-dbus-dbg: Depends: python-dbg but it is not installed
                       Depends: python-qt4-dbg but it is not installed
                       Depends: python-dbus-dbg but it is not installed
                       Depends: libc6 (>= 2.5-5) but 2.5-0ubuntu14 is installed
                       Depends: libgcc1 (>= 1:4.2-20070516) but 1:4.1.2-0ubuntu4 is installed
E: Unmet dependencies. Try using -f.
```

then, when i try the suggested "-f" flag, i get the following:

```

Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  kalzium-data gnome-media-common imlib11 libgmime-2.0-2 libfaad2-0
  libeel2-data libgnomeprintui2.2-common python-pyorbit libgail18 libpth20
  liblua50-dev libjasper-1.701-dev gamin libnss3 libgconf2-dev
  libgnomecanvas2-0 dirmngr libkpathsea4 libaudiofile-dev latex-xft-fonts
  libavc1394-0 libbonobo2-common gnome-mime-data libmpeg3hv libgpg-error-dev
  libxslt1-dev libxml2-utils clamav libartsc0-dev comerr-dev
  libedataserver1.2-9 python-reportlab libqt3-headers libquicktime0
  libgl1-mesa-dev libasound2-dev ttf-dustin libavahi-glib-dev python-imaging
  libsepol1-dev libbonobo2-0 libvte-common libgnomeprintui2.2-0
  libgnomevfs2-common docbook-xml libvorbis-dev libestools1.2 xlibmesa-gl-dev
  libselinux1-dev libpisock9 refblas3 python2.5-dbg libsuperlu3 python-dbg
  libiso9660-4 python-gnomecanvas libhsqldb-java kdeedu-data clamav-base
  libavahi-glib1 liborbit2-dev evolution-common libkrb5-dev libclamav2
  liblcms1-dev libogg-dev libgda2-common shared-mime-info libdvbpsi4
  libmdbtools libavcodec0d libcdio6 python-ipy libxosd2 mesa-common-dev
  libgamin0 libcupsys2-dev librsvg2-common libiec61883-0 libgnomeprint2.2-0
  tidy libsdl-image1.2 arj blt lua50 ttf-sjfonts libijs-0.35 libacl1-dev
  libgnome2-common libggi2 libgtksourceview1.0-0 hspell libgii1 gpp
  libglade2-dev libssl-dev python-vte libxt-dev libvte9 libksba8 libxmu-dev
  python-xml libscrollkeeper0 libgnomecups1.0-1 libegroupwise1.2-13
  libidn11-dev libgtop2-common libtasn1-3-dev gnupg-agent python-foomatic
  libgts-0.7-5 tcltls libgnomeprint2.2-data liba52-0.7.4 kstars-data edict
  libpostproc0d system-config-printer libidl-dev module-assistant
  kdegames-card-data libesd0-dev libgksuui1.0-1 libgail-common libattr1-dev
  docker libnspr4 libgnome-media0 libgsm1 libdv4 libdvdnav4 libservlet2.3-java
  libgii1-target-x kdeartwork-theme-icon libopencdk8-dev kdeartwork-misc
  libdvdread3 sox liblzo-dev libdc1394-13 atlas3-base tcl8.4 python-gtkhtml2
  libgcrypt11-dev libgksu1.2-1 libavformat0d kanjidic libgtop2-7 imlib-base
  libaudio-dev liblualib50-dev liblircclient0 libgnomeui-common libpq-dev
  tango-icon-theme libxvidcore4 tango-icon-theme-common libkadm55 python-cups
  clamav-freshclam tk8.4 libgda2-3 libxmu-headers sgml-data libmad0
  kdesdk-scripts libgfortran1 libmal1 evolution-data-server-common
  liblaunchpad-integration0 hal-info libtar libtiff-tools libgnutls-dev
  scrollkeeper kdewallpapers libg2c0 libmng-dev libgtksourceview-common
  klettres-data kdeartwork-emoticons libavahi-common-dev libsqlite0-dev
  libbonoboui2-common libjpeg62-dev libvcdinfo0 libgnomecanvas2-dev liblame0
  libgnome-pilot2 gnome-icon-theme dpatch python-gconf gpgsm gnupg2 libcucul0
  gettext-kde libtidy-0.99-0 libmpeg2-4 libsasl2-dev libsoup2.2-8
  python-libxml2 libgnomecanvas2-common quanta-data texinfo libpisync0
  libbonobo2-dev libgtkhtml2-0 gcc-3.4-base
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  blt python-dbg python2.5-dbg
Suggested packages:
  blt-demo
The following packages will be REMOVED:
  adept adept-batch adept-common adept-installer adept-manager adept-notifier
  adept-updater akregator alien alsa-source alsa-tools alsa-tools-gui
  alsamixergui amarok amarok-xine amor amsn apport apport-qt apt apt-utils
  aptitude ark arts artsbuilder aspell aspell-en atlantik atlantikdesigner
  automatix2 avahi-daemon blender blinken bluez-pin bluez-utils bug-buddy
  build-essential cdrdao cinelerra cupsys cupsys-driver-gutenprint dbus
  dchroot dcoprss debhelper debtags dh-make dhcdbd digikam dselect
  dvd+rw-tools eggcups envy evince evolution evolution-data-server eyesapplet
  festival festlex-cmu festlex-poslex festvox-kallpc16k fftw2 fifteenapplet
  filelight firefox foomatic-db-gutenprint foomatic-db-hpijs freeglut3 g++
  g++-4.1 gdesklets gdesklets-data gksu gnome-cups-manager gnome-keyring
  groff-base gs-common gs-esp gs-esp-x gtk-qt-engine gtkhtml3.14 gwenview hal
  hal-cups-utils hpijs hpijs-ppds hplip html2text hwdb-client-common
  hwdb-client-kde ijsgutenprint indi juk k3b k3d kaboodle kaddressbook
  kaddressbook-plugins kaffeine kaffeine-xine kalarm kalzium kamera kanagram
  kandy kappfinder karm kasteroids katapult kate kate-plugins katomic
  kaudiocreator kbackgammon kbattleship kblackbox kbounce kbruch kbstate kcalc
  kcharselect kcoloredit kcontrol kcron kdat kde kde-amusements kde-core
  kde-guidance kde-guidance-powermanager kde-style-polyester
  kde-systemsettings kdeaccessibility kdeaddons kdeaddons-kfile-plugins
  kdeadmin kdeadmin-kfile-plugins kdeartwork kdeartwork-style
  kdeartwork-theme-window kdebase kdebase-bin kdebase-dev kdebase-kio-plugins
  kdebluetooth kdeedu kdegames kdegraphics kdegraphics-kfile-plugins kdelibs
  kdelibs4-dev kdelibs4c2a kdelirc kdemultimedia kdemultimedia-kappfinder-data
  kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork
  kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim
  kdepim-kfile-plugins kdepim-kio-plugins kdepim-kresources kdepim-wizards
  kdeprint kdesktop kdessh kdetoys kdeutils kdewebdev kdf kdict kdm kdnssd
  kdvi kedit keduca keep kenolaba kexi kfax kfaxview kfilereplace kfind
  kfloppy kfouleggs kgamma kget kghostview kgoldrunner kgpg khangman
  khelpcenter khexedit kicker kicker-applets kiconedit kig kimagemapeditor
  kio-apt kio-locate kipi-plugins kitchensync kiten kjots kjumpingcube klamav
  klaptopdaemon klatin kleopatra klettres klickety klines klinkstatus klipper
  kmag kmahjongg kmail kmailcvt kmenuedit kmid kmilo kmines kmix kmoon
  kmousetool kmouth kmplayer-base kmplayer-konq-plugins kmplot kmrml knemo
  knetwalk knetworkconf knetworkmanager knewsticker knode knotes kodo
  koffice-libs kolf kolourpaint komba2 kommander konq-plugins konqueror
  konqueror-nsplugins konquest konsole konsolekalendar kontact konversation
  kooka kopete korganizer korn kpackage kpager kpat kpdf kpercentage
  kpersonalizer kpf kpilot kpoker kpovmodeler kppp krdc krec kregexpeditor
  kreversi krfb kruler ksame ksayit kscd kscreensaver kscreensaver-xsavers
  kshisen ksig ksim ksirc ksirtet ksmiletris ksmserver ksnake ksnapshot
  ksokoban kspaceduel ksplash ksplash-engine-moodin kstars ksvg ksync
  ksysguard ksysguardd ksystemlog ksysv kteatime ktimer ktip ktnef ktorrent
  ktouch ktron kttsd ktuberling kturtle ktux kubuntu-default-settings
  kubuntu-docs kubuntu-konqueror-shortcuts kuser kverbos kview kviewshell
  kvoctrain kwalletmanager kweather kwifimanager kwin kwin-style-crystal kwin4
  kwordquiz kworldclock kxsldbg language-selector-qt language-support-en
  libakode2 libarts1-akode libarts1-audiofile libarts1-dev libarts1-mpeglib
  libarts1-xine libarts1c2a libaspell-dev libaspell15 libavahi-client-dev
  libavahi-client3 libavahi-compat-libdnssd1 libavahi-qt3-1 libavahi-qt3-dev
  libbeecrypt6 libbonoboui2-0 libbonoboui2-dev libboost-date-time1.33.1
  libboost-filesystem1.33.1 libboost-program-options1.33.1
  libboost-python1.33.1 libboost-regex1.33.1 libcaca0 libcairomm-1.0-1
  libcamel1.2-10 libcvsservice0 libdb4.3++c2 libdbus-1-3 libdbus-1-dev
  libdbus-glib-1-2 libdbus-glib-1-dev libdbus-qt-1-1c2 libdbus-qt-1-dev
  libdjvulibre15 libebook1.2-9 libecal1.2-7 libedata-book1.2-2
  libedata-cal1.2-6 libedataserverui1.2-8 libeel2-2 libenchant1c2a
  libexchange-storage1.2-3 libexiv2-0.12 libfaac0 libflac++5c2 libfltk1.1
  libfox1.4 libfreebob0 libgc1c2 libgdl-1-0 libgdl-1-common libgksu2-0
  libglibmm-2.4-1c2a libglu1-mesa libglu1-mesa-dev libglu1-xorg-dev libglut3
  libgnome-desktop-2 libgnome-desktop-dev libgnome-keyring-dev
  libgnome-keyring0 libgnome-menu2 libgnome-window-settings-dev
  libgnome-window-settings1 libgnome2-0 libgnome2-dev libgnomecupsui1.0-1c2a
  libgnomeui-0 libgnomeui-dev libgnomevfs2-0 libgnomevfs2-dev libgphoto2-2
  libgphoto2-port0 libgs-esp8 libgtkglext1 libgtkhtml3.14-19 libgtkmm-2.4-1c2a
  libgtkspell0 libguicast libhal-storage1 libhal1 libhdf5-serial-1.6.5-0
  libhunspell-1.1-0 libicu36 libindex0 libjack0.100.0-0 libjasper-runtime
  libk3b2 libkcal2b libkcddb1 libkdeedu3 libkdegames1 libkdepim1a libkexiv2-0
  libkgantt0 libkipi0 libkiten1 libkleopatra1 libkmime2 libkonq4
  libkpimexchange1 libkpimidentities1 libkscan1 libksieve0 libktnef1
  liblpint-bonobo0 libmagick++9c2a libmimelib1c2a libmjpegtools0c2a
  libmodplug0c2 libmp4v2-0 libmpich1.0c2 libmusicbrainz4c2a libnautilus-burn4
  libnautilus-extension1 libnm-glib0 libnm-util0 libnotify1 libnss-mdns
  libofa0 libopenexr-dev libopenexr2c2a libpanel-applet2-0 libpcre3-dev
  libpcrecpp0 libpoppler1 libpoppler1-glib libpoppler1-qt libpythonize0
  libqt-perl libqt3-mt libqt3-mt-dev libqt4-core libqt4-debug libqt4-dev
  libqt4-gui libqt4-qt3support libqt4-sql libquicktimehv librpm4 librss1
  libsane libscim8c2a libsexy2 libsigc++-2.0-0c2a libskim0 libsmokeqt1
  libsoundtouch1c2 libstdc++6 libstdc++6-4.1-dev libtag1c2a libtiff4-dev
  libtiffxx0c2 libtotem-plparser1 libtunepimp5 libuniconf4.2 libvlc0
  libwpd8c2a libwps-0.1-1 libwvstreams4.2-base libwvstreams4.2-extras
  libwxbase2.6-0 libwxgtk2.6-0 libxine1 libxplc0.3.13 lshw lskat
  mail-notification man-db mencoder mozilla-firefox-locale-en-gb
  mozilla-mplayer mozilla-thunderbird mpeglib mplayer mplayer-fonts nerolinux
  network-manager networkstatus noatun noatun-plugins notification-daemon
  nvclock-qt octave octave2.1 openoffice.org openoffice.org-base
  openoffice.org-calc openoffice.org-common openoffice.org-core
  openoffice.org-draw openoffice.org-filter-mobiledev
  openoffice.org-help-en-us openoffice.org-impress openoffice.org-java-common
  openoffice.org-kde openoffice.org-l10n-en-gb openoffice.org-l10n-en-za
  openoffice.org-math openoffice.org-style-crystal openoffice.org-style-human
  openoffice.org-thesaurus-en-us openoffice.org-writer p7zip-full pdfedit
  pdftk pinentry-qt pmount pnm2ppa poppler-utils printconf python-apport
  python-apt python-dbus python-gnome2 python-gnome2-desktop
  python-gnome2-extras python-kde3 python-launchpad-bugs python-notify
  python-qt3 python-qt4 python-qt4-dbus python-qt4-dbus-dbg python-sip4
  python-software-properties python-uno qca-tls qobex qt3-dev-tools
  qt3-qtconfig qt4-designer qt4-dev-tools qt4-qtconfig quanta
  restricted-manager rezound rpm schroot scim-qtimm secpolicy skim
  software-properties-kde speedcrunch superkaramba synaptic tasksel
  tasksel-data telnet thunderbird-locale-en-gb ubuntu-standard
  unattended-upgrades unrar update-manager-core vlc vlc-nox w3m wine
  wpasupplicant wvdial xorg xscreensaver-gl zenity
The following NEW packages will be installed:
  blt python-dbg python2.5-dbg
WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing!
  apt libstdc++6 (due to apt)
0 upgraded, 3 newly installed, 593 to remove and 0 not upgraded.
6 not fully installed or removed.
Need to get 9709kB of archives.
After unpacking 1897MB disk space will be freed.
You are about to do something potentially harmful.
To continue type in the phrase 'Yes, do as I say!'
 ?]  
```

obviously, this is basically saying: "everything's broken, have to remove everything"

can anyone help me fix this without reformatting? thanks.

---

### Post by darwinmach on 2007-07-03
ok, i think i fixed it

ran the following:

```
$ sudo aptitude
```

then pressed 'g' to fix the broken packages... worked like a charm, although aptitude's GUI wasn't friendly

---

