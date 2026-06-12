---
title: "[SOLVED] Huge Screw-up"
date: 2007-07-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by c6comp on 2007-07-30
Earlier today, i let one of my friends use my ubuntu amd 64 box, he wanted to install something, so i gave hime the root password (smacks self once). Then i left the room (smacks head twice). A few hours later, i came back from work and tried installing evolution (final smack of head), and this is what i got :( :
```
 omer@omer-deskubut:~$ sudo apt-get install evolution
Reading package lists... Done
Building dependency tree       
Reading state information... Done
evolution is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  cpp-4.1: Depends: gcc-4.1-base (= 4.1.2-0ubuntu4) but 4.1.2-14 is to be installed
  gcc-4.1: Depends: gcc-4.1-base (= 4.1.2-0ubuntu4) but 4.1.2-14 is to be installed
  libgcc1: Depends: gcc-4.1-base (= 4.1.2-0ubuntu4) but 4.1.2-14 is to be installed
  libstdc++6: Depends: gcc-4.1-base (= 4.1.2-0ubuntu4) but 4.1.2-14 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution). 
```

All i thought now was that this is VERY bad, and that when i ran sudo apt-get -f install, surely it would tell me to remove essential packages..and it did.:(

```
omer@omer-deskubut:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libaiksaurus-1.2-data java-common mplayer-skins gcc-3.3-base
  libgii1-target-x libgtk1.2-common linux-libc-dev kdelibs-data kdebase-data
  mysql-common
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  abiword abiword-common abiword-help abiword-plugins acpi acpi-support acpid
  adduser alacarte alien alsa-base alsa-utils amarok amarok-xine amsn anacron
  apport apport-gtk appres apt apt-utils aptitude aspell aspell-en at at-spi
  avahi-autoipd avahi-daemon base-files base-passwd bash bc beforelight
  belocs-locales-bin bind9-host binfmt-support binutils binutils-static bison
  bitmap bittorrent bluez-cups bluez-pin bluez-utils brasero brltty brltty-x11
  bsdmainutils bsdutils bsh bzip2 ca-certificates cabextract cairo-clock
  capplets-data cdparanoia cdrdao cdrecord cedega-small command-not-found
  compiz compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main
  compiz-fusion-plugins-unofficial compiz-gnome compiz-plugins
  compizconfig-settings-manager conky console-setup console-terminus
  console-tools contact-lookup-applet coreutils cpio cpp cpp-4.1 cron cupsys
  cupsys-bsd cupsys-client cupsys-driver-gutenprint dash dbus dbus-1-utils dc
  dcraw debconf debconf-i18n debhelper debianutils defoma deskbar-applet
  desktop-file-utils devede dhcdbd dhcp3-client dhcp3-common
  dictionaries-common diff diffstat diveintopython dmidecode dmsetup dnsutils
  doc-base docbook-xml docker dosbox dosfstools dpkg dpkg-dev dselect
  dvd+rw-tools dvdauthor e2fslibs e2fsprogs ed editres eject emerald enscript
  eog esound espeak etherape ethtool evince evolution evolution-data-server
  evolution-exchange evolution-plugins evolution-webcal fastjar fdutils fftw3
  file file-roller findutils finger firefox firefox-gnome-support flex
  fontconfig fontconfig-config fontforge foo2zjs foomatic-db-engine
  foomatic-db-hpijs foomatic-filters fortune-mod fortunes-min fping freeglut3
  fstobdf ftp gaim-data gamin gcalctool gcc gcc-4.1 gconf-editor gconf2
  gconf2-common gdb gdebi gdebi-core gdm gedit genisoimage gettext
  gettext-base gij gij-4.1 gimp-python gkrellm gksu gmpc gnome-about
  gnome-accessibility-themes gnome-app-install gnome-applets
  gnome-applets-data gnome-control-center gnome-cups-manager gnome-doc-utils
  gnome-games-data gnome-icon-theme gnome-keyring gnome-keyring-manager
  gnome-mag gnome-media gnome-media-common gnome-menus gnome-mount
  gnome-netstatus-applet gnome-nettool gnome-panel gnome-panel-data
  gnome-power-manager gnome-screensaver gnome-session gnome-spell
  gnome-system-monitor gnome-system-tools gnome-terminal gnome-terminal-data
  gnome-themes gnome-user-guide gnome-utils gnome-volume-manager gnupg gpgv
  gpm grep groff-base grub gs-common gs-esp gs-esp-x gsfonts
  gstreamer0.10-alsa gstreamer0.10-esd gstreamer0.10-gnomevfs
  gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps
  gstreamer0.10-plugins-good gstreamer0.10-plugins-ugly
  gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-tools gstreamer0.10-x
  gthumb gtk2-engines gtk2-engines-pixbuf gtk2-engines-ubuntulooks gtkhtml3.14
  guile-1.6-libs gzip hal hal-device-manager hdparm hostname hotkey-setup
  hpijs hplip html2text human-theme hwdb-client-common hwdb-client-gnome
  iceauth ico ifupdown imagemagick imlib-base imlib11 info initramfs-tools
  initscripts inputattach intltool-debian iproute iptables iputils-arping
  iputils-ping iputils-tracepath java-gcj-compat k3b kcontrol kdebase-bin
  kdebase-kio-plugins kdelibs4c2a kdesktop kfind kicker klogd konqueror
  konsole ktorrent kwin language-pack-en language-pack-en-base
  language-pack-gnome-en language-pack-gnome-en-base language-selector
  language-selector-common language-support-en laptop-detect laptop-mode-tools
  launchpad-integration less lftp liba52-0.7.4 libaa1 libacl1
  libaiksaurus-1.2-0c2a libaiksaurusgtk-1.2-0c2a libao2 libapm1 libapr1
  libaprutil1 libart-2.0-2 libarts1c2a libartsc0 libasound2 libaspell15
  libatk1.0-0 libatspi1.0-0 libattr1 libaudio2 libaudiofile0 libavahi-client3
  libavahi-common3 libavahi-core5 libavahi-glib1 libavahi-qt3-1 libavc1394-0
  libavcodec0d libavformat0d libbeagle0 libbeecrypt6 libbind9-0 libblkid1
  libbluetooth2 libbonobo2-0 libbonobo2-common libbonoboui2-0 libbrlapi1
  libbz2-1.0 libc6 libc6-dev libcaca0 libcairo-perl libcairo2 libcairomm-1.0-1
  libcamel1.2-10 libcap1 libcdio6 libcdparanoia0 libclass-accessor-perl
  libcomerr2 libcompizconfig-backend-gconf libcompizconfig0 libconsole
  libcroco3 libcucul0 libcupsimage2 libcupsys2 libcurl3 libcurl3-gnutls
  libdaemon0 libdatrie0 libdb4.2 libdb4.3 libdb4.4 libdbus-1-3
  libdbus-glib-1-2 libdbus-qt-1-1c2 libdc1394-13 libdecoration0
  libdevmapper1.02 libdirectfb-0.9-25 libdjvulibre15 libdmx1 libdns22 libdrm2
  libdv4 libdvbpsi4 libdvdnav4 libdvdread3 libebook1.2-9 libecal1.2-7
  libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-9
  libedataserverui1.2-8 libedit2 libeel2-2 libegroupwise1.2-13 libelfg0
  libemeraldengine0 libenchant1c2a libesd-alsa0 libespeak1
  libexchange-storage1.2-3 libexif12 libexo-0.3-0 libexpat1 libfaac0
  libflac++5c2 libflac7 libfontconfig1 libfontenc1 libfreetype6 libfribidi0
  libfs6 libfuse2 libgadu3 libgail-common libgail-gnome-module libgail18
  libgamin0 libgc1c2 libgcc1 libgcj-bc libgcj7-0 libgcj7-jar libgconf2-4
  libgconf2.0-cil libgcrypt11 libgda2-3 libgdbm3 libgdiplus libgdl-1-0
  libgdl-1-common libgdome2-0 libgdome2-cpp-smart0c2a libggi2 libgii1
  libgimp2.0 libgksu1.2-1 libgksu2-0 libgksuui1.0-1 libgl1-mesa-dri
  libgl1-mesa-glx libglade2-0 libglade2.0-cil libglademm-2.4-1c2a libglew1
  libglib-perl libglib1.2 libglib2.0-0 libglib2.0-cil libglibmm-2.4-1c2a
  libglu1-mesa libglut3 libgmime-2.0-2 libgmime2.2-cil libgmp3c2
  libgnome-desktop-2 libgnome-keyring0 libgnome-mag2 libgnome-media0
  libgnome-menu2 libgnome-pilot2 libgnome-speech3 libgnome-window-settings1
  libgnome2-0 libgnome2-canvas-perl libgnome2-common libgnome2-perl
  libgnome2-vfs-perl libgnome2.0-cil libgnomecanvas2-0 libgnomecups1.0-1
  libgnomecupsui1.0-1c2a libgnomekbd-common libgnomekbd1 libgnomekbdui1
  libgnomeprint2.2-0 libgnomeprintui2.2-0 libgnomeui-0 libgnomeui-common
  libgnomevfs2-0 libgnomevfs2-bin libgnomevfs2-common libgnomevfs2-extra
  libgnutls13 libgpg-error0 libgphoto2-2 libgphoto2-port0 libgpmg1 libgpod1
  libgs-esp8 libgsf-1-114 libgsm1 libgstreamer-plugins-base0.10-0
  libgstreamer0.10-0 libgtk1.2 libgtk2-perl libgtk2.0-0 libgtk2.0-bin
  libgtk2.0-cil libgtk2.0-common libgtkhtml2-0 libgtkhtml3.14-19
  libgtkmathview0c2a libgtkmm-2.4-1c2a libgtksourceview1.0-0 libgtkspell0
  libgtop2-7 libgucharmap6 libguile-ltdl-1 libgutenprint2 libgutenprintui2-1
  libhal-storage1 libhal1 libhsqldb-java libhtml-parser-perl
  libhtml-tagset-perl libhtml-tree-perl libhunspell-1.1-0 libice-dev libice6
  libicu36 libid3tag0 libidl0 libidn11 libiec61883-0 libieee1284-3 libifp4
  libio-string-perl libisc11 libisccc0 libisccfg1 libiso9660-4 libitl0 libiw28
  libjasper-1.701-1 libjaxp1.3-java libjline-java libjpeg62 libk3b2 libkonq4
  libkpathsea4 libkrb53 liblame0 liblaunchpad-integration0 liblcms1 libldap2
  liblircclient0 liblocale-gettext-perl liblpint-bonobo0 libltdl3 liblua50
  liblualib50 liblwres9 liblzo1 libmad0 libmagic1 libmagick9 libmdbtools
  libmetacity0 libmikmod2 libmng1 libmodplug0c2 libmono-cairo1.0-cil
  libmono-corlib1.0-cil libmono-corlib2.0-cil libmono-data-tds2.0-cil
  libmono-security2.0-cil libmono-sharpzip2.84-cil libmono-sqlite2.0-cil
  libmono-system-data2.0-cil libmono-system-web2.0-cil libmono-system1.0-cil
  libmono-system2.0-cil libmono0 libmono2.0-cil libmp4v2-0 libmpcdec3 libmpd0
  libmpeg2-4 libmtp5 libmusicbrainz4c2a libmysqlclient15off libnautilus-burn4
  libnautilus-extension1 libncurses5 libncursesw5 libndesk-dbus-glib1.0-cil
  libndesk-dbus1.0-cil libneon25 libneon26 libnet-dbus-perl libnewt0.52
  libnjb5 libnl1-pre6 libnm-glib0 libnm-util0 libnotify1 libnspr4 libnss-mdns
  libnss3 libofa0 libogg0 liboil0.3 liboobs-1-3 libopal-2.2.0 libopencdk8
  libopenexr2c2a liborbit2 libots0 libpam-foreground libpam-modules
  libpam-runtime libpam0g libpanel-applet2-0 libpango1.0-0 libpango1.0-common
  libpaper1 libparse-debianchangelog-perl libparted1.7-1 libpcap0.8 libpci2
  libpcre3 libperl5.8 libpisock9 libpisync0 libpng12-0 libpoppler1
  libpoppler1-glib libpopt0 libportaudio0 libpostproc0d libpq5 libpt-1.10.0
  libpt-plugins-alsa libpt-plugins-v4l libpt-plugins-v4l2 libpulse0
  libqt3-java libqt3-jni libqt3-mt libqt4-core libqt4-debug libqt4-gui
  libraw1394-8 libreadline5 librecode0 librpm4 librsvg2-2 librsvg2-common
  libruby1.8 libsane libsasl2-2 libsasl2-modules libscim8c2a libscrollkeeper0
  libsdl-image1.2 libsdl-net1.2 libsdl-sound1.2 libsdl1.2debian
  libsdl1.2debian-alsa libselinux1 libsensors3 libsepol1 libservlet2.3-java
  libsexy2 libshout3 libsidplay1 libsigc++-2.0-0c2a libslab0 libslang2 libslp1
  libsm-dev libsm6 libsmbclient libsmpeg0 libsndfile1 libsnmp9 libsoup2.2-8
  libspeex1 libsqlite3-0 libss2 libssl0.9.8 libstartup-notification0
  libstdc++5 libstdc++6 libstlport5.1 libsvga1 libsvn1 libsysfs2 libt1-5
  libtag1c2a libtar libtasn1-3 libtext-charwidth-perl libtext-iconv-perl
  libtext-wrapi18n-perl libthai0 libtheora0 libthunar-vfs-1-2 libtiff4
  libtimedate-perl libtotem-plparser1 libtunepimp5 libungif4g libuniconf4.2
  libuninameslist0 liburi-perl libusb-0.1-4 libusplash0 libuuid1 libvcdinfo0
  libvisual-0.4-0 libvlc0 libvolume-id0 libvorbis0a libvorbisenc2
  libvorbisfile3 libvte9 libwmf0.2-7 libwnck18 libwpd-stream8c2a libwpd8c2a
  libwps-0.1-1 libwrap0 libwvstreams4.2-base libwvstreams4.2-extras
  libwww-perl libwxbase2.6-0 libwxgtk2.6-0 libx11-6 libx11-data libx11-dev
  libx86-1 libxalan110 libxalan2-java libxau-dev libxau6 libxaw7
  libxcomposite1 libxcursor1 libxdamage1 libxdmcp-dev libxdmcp6
  libxerces2-java libxerces27 libxevie1 libxext-dev libxext6 libxext6-dbg
  libxfce4mcs-client3 libxfce4mcs-manager3 libxfce4util4 libxfcegui4-4
  libxfixes3 libxfont1 libxft2 libxi6 libxine-extracodecs libxine1
  libxine1-ffmpeg libxinerama1 libxkbfile1 libxklavier11 libxml-parser-perl
  libxml-twig-perl libxml2 libxml2-utils libxmu-dev libxmu-headers libxmu6
  libxmuu1 libxosd2 libxp6 libxplc0.3.13 libxpm4 libxrandr2 libxrender1
  libxres1 libxslt1.1 libxss1 libxt-dev libxt6 libxtrap6 libxtst6 libxv1
  libxvidcore4 libxvmc1 libxxf86dga1 libxxf86misc1 libxxf86vm1 links2 lintian
  linux-generic linux-headers-2.6.20-15 linux-headers-2.6.20-15-generic
  linux-headers-2.6.20-16 linux-headers-2.6.20-16-generic
  linux-headers-generic linux-image-2.6.20-15-generic
  linux-image-2.6.20-16-generic linux-image-generic
  linux-restricted-modules-2.6.20-15-generic
  linux-restricted-modules-2.6.20-16-generic linux-restricted-modules-common
  linux-restricted-modules-generic linux-sound-base linux32 listres lm-sensors
  locales login logrotate lsb-base lsb-release lshw lsof ltrace m4 make
  makedev man-db mawk mcpp mencoder mesa-utils metacity metacity-common
  mii-diag min12xxw mkisofs mktemp module-init-tools mono-common mono-gac
  mono-jit mono-runtime mount mozilla-firefox-locale-en-gb mpg123 mplayer
  mscompress msttcorefonts mtr-tiny myspell-en-gb myspell-en-us myspell-en-za
  nano nautilus nautilus-cd-burner nautilus-data ncurses-base ncurses-bin
  net-tools netbase netcat network-manager network-manager-gnome
  notification-daemon nspluginwrapper ntpdate nvidia-glx nvidia-kernel-common
  oclock odbcinst1debian1 openoffice.org openoffice.org-base
  openoffice.org-calc openoffice.org-common openoffice.org-core
  openoffice.org-draw openoffice.org-filter-mobiledev openoffice.org-gnome
  openoffice.org-gtk openoffice.org-help-en-us openoffice.org-hyphenation
  openoffice.org-impress openoffice.org-java-common openoffice.org-l10n-common
  openoffice.org-l10n-en-gb openoffice.org-l10n-en-za openoffice.org-math
  openoffice.org-style-human openoffice.org-thesaurus-en-us
  openoffice.org-writer openssh-client openssh-server openssl oss-compat
  p7zip-full parted passwd patch pciutils pcmciautils perl perl-base
  perl-modules pkg-config pnm2ppa po-debconf poppler-utils popularity-contest
  powermanagement-interface powermgmt-base powernowd ppp pppconfig pppoeconf
  preload procps psmisc putty putty-tools python python-apport python-apt
  python-at-spi python-bittorrent python-cairo python-central
  python-compizconfig python-dbus python-gconf python-gdbm python-glade2
  python-gmenu python-gnome2 python-gnome2-desktop python-gnome2-extras
  python-gnomecanvas python-gnupginterface python-gobject python-gst0.10
  python-gtk2 python-gtkhtml2 python-launchpad-bugs
  python-launchpad-integration python-libxml2 python-minimal python-notify
  python-numeric python-orca-brlapi python-problem-report python-pyorbit
  python-qt3 python-sip4 python-software-properties python-support python-uno
  python-virtkey python-vte python-xdg python-xml python2.5 python2.5-minimal
  qtparted rdesktop readahead reiserfsprogs restricted-manager rpm rss-glx
  rsync ruby ruby1.8 samba samba-common scim scim-gtk2-immodule
  scim-modules-socket screen screensaver-default-images scrollkeeper sed
  serpentine sessreg sgml-base sgml-data shared-mime-info slocate smbclient
  smproxy software-properties-gtk sound-juicer sox ssh-askpass-gnome ssl-cert
  startup-tasks startupmanager strace subversion sudo sun-java6-bin
  sun-java6-jre synaptic sysklogd system-services system-tools-backends
  sysvutils tangerine-icon-theme tango-icon-theme-common tar tasksel
  tasksel-data tcl8.4 tcltls tcpdump telnet thunar thunderbird-locale-en-gb
  time tk8.4 totem totem-gstreamer totem-mozilla tsclient ttf-arabeyes
  ttf-arphic-ukai ttf-arphic-uming ttf-baekmuk ttf-bengali-fonts
  ttf-bitstream-vera ttf-dejavu ttf-devanagari-fonts ttf-freefont ttf-gentium
  ttf-gujarati-fonts ttf-indic-fonts ttf-kannada-fonts ttf-kochi-gothic
  ttf-kochi-mincho ttf-lao ttf-malayalam-fonts ttf-mgopen ttf-oriya-fonts
  ttf-punjabi-fonts ttf-tamil-fonts ttf-telugu-fonts ttf-thai-tlwg tvtime
  tzdata ubuntu-artwork ubuntu-docs ubuntu-keyring ubuntu-minimal
  ubuntu-restricted-extras ubuntu-standard ucf udev unattended-upgrades
  unixodbc unrar unzip update-inetd update-manager update-manager-core
  update-notifier upstart upstart-compat-sysv upstart-logd usbutils usplash
  usplash-theme-ubuntu util-linux util-linux-locales vbaexpress vbetool
  vcdimager viewres vim-common vim-tiny vino virtualbox visualboyadvance vlc
  vlc-nox vnc-common volumeid w3m wamerican wbritish wget whiptail whois
  wireless-tools wodim wpasupplicant wvdial x-ttcidfont-conf x11-common
  x11perf x11proto-core-dev x11proto-input-dev x11proto-kb-dev
  x11proto-xext-dev xarchiver xauth xbase-clients xbiff xbindkeys
  xbindkeys-config xbitmaps xcalc xclipboard xclock xconsole xcursorgen
  xditview xdpyinfo xdriinfo xev xeyes xf86dga xfce4-panel xfd xfonts-100dpi
  xfonts-75dpi xfonts-base xfonts-encodings xfonts-scalable xfonts-utils
  xfontsel xgamma xgc xhost xinit xkbutils xkill xload xlogo xlsatoms
  xlsclients xlsfonts xmag xman xmessage xml-core xmodmap xmore xorg xpmutils
  xprop xrandr xrdb xrefresh xrgb xscreensaver-data xscreensaver-gl
  xserver-xorg xserver-xorg-core xserver-xorg-input-all
  xserver-xorg-input-evdev xserver-xorg-input-kbd xserver-xorg-input-mouse
  xserver-xorg-input-synaptics xserver-xorg-video-all xserver-xorg-video-apm
  xserver-xorg-video-ark xserver-xorg-video-ati xserver-xorg-video-chips
  xserver-xorg-video-cirrus xserver-xorg-video-cyrix xserver-xorg-video-dummy
  xserver-xorg-video-fbdev xserver-xorg-video-glint xserver-xorg-video-i128
  xserver-xorg-video-i810 xserver-xorg-video-mga xserver-xorg-video-neomagic
  xserver-xorg-video-nv xserver-xorg-video-rendition xserver-xorg-video-s3
  xserver-xorg-video-s3virge xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-tga
  xserver-xorg-video-trident xserver-xorg-video-tseng xserver-xorg-video-v4l
  xserver-xorg-video-vesa xserver-xorg-video-vga xserver-xorg-video-via
  xserver-xorg-video-vmware xserver-xorg-video-voodoo xset xsetmode
  xsetpointer xsetroot xsltproc xsm xstdcmap xterm xtrans-dev xtrap xutils
  xutils-dev xvidtune xvinfo xvncviewer xwd xwininfo xwud yelp zenity zip
  zlib1g
WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing!
  apt libc6 (due to apt) libgcc1 (due to apt) libstdc++6 (due to apt)
  base-files base-passwd (due to base-files) libpam-modules (due to
  base-files) bash debianutils (due to bash) libncurses5 (due to bash)
  bsdutils coreutils libacl1 (due to coreutils) libselinux1 (due to coreutils)
  mktemp (due to debianutils) diff dpkg e2fsprogs e2fslibs (due to e2fsprogs)
  libblkid1 (due to e2fsprogs) libcomerr2 (due to e2fsprogs) libss2 (due to
  e2fsprogs) libuuid1 (due to e2fsprogs) findutils grep gzip hostname login
  libpam0g (due to login) libpam-runtime (due to login) mount ncurses-base
  ncurses-bin perl-base python-minimal python2.5-minimal (due to
  python-minimal) sed sysvutils libsepol1 (due to sysvutils) tar util-linux
  lsb-base (due to util-linux) tzdata (due to util-linux) libslang2 (due to
  util-linux) zlib1g (due to util-linux)
0 upgraded, 0 newly installed, 1192 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 2907MB disk space will be freed.
You are about to do something potentially harmful.
To continue type in the phrase 'Yes, do as I say!'
 ?] n
Abort. 
```

Sigh.... i know that i will problably have to reinstall, because i cannot compile anything, nor can i use apt... So, i ask anyone with any suggestions to please come forth. I would like to avoid a reinstall...please???

](*,)

---

### Post by pranithkumar on 2007-07-30
i dont think u need to reinstall. just go to synaptic and select manually the above packages which have unmet dependencies, and try removing them. 
just give this a try...

---

### Post by c6comp on 2007-07-30
> **pranithkumar said:**
> i dont think u need to reinstall. just go to synaptic and select manually the above packages which have unmet dependencies, and try removing them. 
just give this a try...

Yes, i tried that, but the problem is that when i try to remove the broken packages, EVERYTHING gets removed:

[IMG]http://img227.imageshack.us/img227/5056/helpik2.png[/IMG]

Thanks anyway.

---

### Post by c6comp on 2007-07-30
[FONT="Arial Black"][SIZE="6"]I FOUND A SOLUTION!!![/SIZE][/FONT]


Linux Rocks! (Now i truly beleive the saying that in order to break windows, you have to work on it, in order to break linux, you have to work at it :))

I did the following command:
 sudo aptitude install gcc

then, it gave me:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  cpp-4.1 gcc-4.1 libgcc1 libstdc++6 
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
The following packages have unmet dependencies:
  libstdc++6: Depends: gcc-4.1-base (= 4.1.2-0ubuntu4) but 4.1.2-14 is installed.
  gcc-4.1: Depends: gcc-4.1-base (= 4.1.2-0ubuntu4) but 4.1.2-14 is installed.
  libgcc1: Depends: gcc-4.1-base (= 4.1.2-0ubuntu4) but 4.1.2-14 is installed.
  cpp-4.1: Depends: gcc-4.1-base (= 4.1.2-0ubuntu4) but 4.1.2-14 is installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Downgrade the following packages:
gcc-4.1-base [4.1.2-14 (now) -> 4.1.2-0ubuntu4 (feisty)]

Score is -40

Accept this solution? [Y/n/q/?] y
The following packages will be DOWNGRADED:
  gcc-4.1-base 
0 packages upgraded, 0 newly installed, 1 downgraded, 0 to remove and 0 not upgraded.
Need to get 201kB of archives. After unpacking 4096B will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main gcc-4.1-base 4.1.2-0ubuntu4 [201kB]
Fetched 201kB in 1s (149kB/s)       
dpkg - warning: downgrading gcc-4.1-base from 4.1.2-14 to 4.1.2-0ubuntu4.
(Reading database ... 124932 files and directories currently installed.)
Preparing to replace gcc-4.1-base 4.1.2-14 (using .../gcc-4.1-base_4.1.2-0ubuntu4_amd64.deb) ...
Unpacking replacement gcc-4.1-base ...
Setting up gcc-4.1-base (4.1.2-0ubuntu4) ...


Now, to check if it worked:

 sudo apt-get install evolution


And...(que drumroll):

Reading package lists... Done
Building dependency tree       
Reading state information... Done
evolution is already the newest version.
The following packages were automatically installed and are no longer required:
  libitl0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

HOLY CRAP!!! From now on, i will ALWAYS use aptitude...for two reasons. 1. It has smarter dependency management (Proof above). 2. It fixed what apt-get did not (Proof above)... Brilliant!!!

Thanks everyone!!!:D

---

### Post by bluenova on 2007-07-30
Aptitude rocks, I don't know why people still encourage the use of apt-get.

---

