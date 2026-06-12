---
title: "Wine doesn't install on Ubuntu 14.04 amd64 - dependencies problem"
date: 2014-11-03
forum: Wine
---

### Post by temmokan on 2014-11-03
Short version: after upgrading Ubuntu 12.04 -> Ubuntu 14.04 Wine 1.6 disapeared. After deleting obsolete PPAs, removing i386 architecture, trying to locate and remove old Wine's dependencies and packages, I still can't install it.

Longer version (commands and output) below.

I would appreciate hints on how to handle it; I started with information from

[http://askubuntu.com/questions/140246/how-do-i-resolve-unmet-dependencies-after-adding-a-ppa](http://askubuntu.com/questions/140246/how-do-i-resolve-unmet-dependencies-after-adding-a-ppa)
and
[http://ubuntuforums.org/showthread.php?t=2188107&page=2](http://ubuntuforums.org/showthread.php?t=2188107&page=2)

for no avail. Thanks.

```
$ sudo add-apt-repository ppa:ubuntu-wine/ppa
(no errors reported)
$ sudo [COLOR=#000000][FONT=Ubuntu Mono]dpkg --add-architecture i386[/FONT][/COLOR]
$ sudo apt-get install wine1.6Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 wine1.6 : Depends: wine1.6-i386 (= 1:1.6.2-0ubuntu4)
E: Unable to correct problems, you have held broken packages.

$ sudo apt-get install wine1.6-i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 wine1.6-i386:i386 : Depends: liblcms2-2:i386 (>= 2.2+git20110628) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


$ sudo apt-get install liblcms2-2:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
accountsservice-ubuntu-schemas accountsservice-ubuntu-touch-schemas
cli-common digikam-data freeglut3 gir1.2-secret-1 gnome-video-effects
gsettings-ubuntu-touch-schemas gstreamer1.0-nice guile-2.0-libs hddtemp
hugin-data hugin-tools kipi-plugins-common liballegro4.4
liballegro4.4-plugin-alsa libandroid-properties1 libart2.0-cil
libboost-program-options1.54.0 libboost-serialization1.54.0 libcapnp-0.4.0
libcontent-hub0 libdbus-cpp2 libdee-qt5-3 libfarstream-0.2-2 libgc1c2
libgconf2.0-cil libgdiplus libgexiv2-2 libgflags2 libglade2.0-cil
libglade2.0-cil-dev libglib2.0-cil libglib2.0-cil-dev libgnome-vfs2.0-cil
libgnome2.24-cil libgoogle-glog0 libgsl0ldbl libgtk2.0-cil libgtk2.0-cil-dev
libgtkmm-2.4-1c2a libgtkspell0 libhardware2 libhud-client2 libhybris
libhybris-common1 libimage-exiftool-perl libjsoncpp0 libkdcraw-data
libkface-data libkface2 libkgeomap-data libkgeomap1 libkipi-data libkipi11
libksane-data libksane0 liblensfun-data liblensfun0 libmedia1
libmediascanner-2.0-0 libmirclient7 libmirclientplatform-mesa libmirplatform
libmirplatformgraphics-mesa libmirprotobuf0 libmirserver18 libmono-2.0-dev
libmono-accessibility2.0-cil libmono-accessibility4.0-cil
libmono-addins-gui0.2-cil libmono-addins0.2-cil libmono-c5-1.1-cil
libmono-cairo2.0-cil libmono-cairo4.0-cil libmono-cecil-private-cil
libmono-cil-dev libmono-codecontracts4.0-cil
libmono-compilerservices-symbolwriter4.0-cil libmono-corlib2.0-cil
libmono-corlib4.0-cil libmono-corlib4.5-cil libmono-cscompmgd8.0-cil
libmono-csharp4.0c-cil libmono-custommarshalers4.0-cil
libmono-data-tds2.0-cil libmono-data-tds4.0-cil libmono-db2-1.0-cil
libmono-debugger-soft2.0a-cil libmono-debugger-soft4.0a-cil
libmono-entityframework-sqlserver6.0-cil libmono-entityframework6.0-cil
libmono-http4.0-cil libmono-i18n-cjk4.0-cil libmono-i18n-mideast4.0-cil
libmono-i18n-other4.0-cil libmono-i18n-rare4.0-cil libmono-i18n-west2.0-cil
libmono-i18n-west4.0-cil libmono-i18n2.0-cil libmono-i18n4.0-all
libmono-i18n4.0-cil libmono-ldap2.0-cil libmono-ldap4.0-cil
libmono-management2.0-cil libmono-management4.0-cil
libmono-messaging-rabbitmq2.0-cil libmono-messaging-rabbitmq4.0-cil
libmono-messaging2.0-cil libmono-messaging4.0-cil
libmono-microsoft-build-engine4.0-cil
libmono-microsoft-build-framework4.0-cil
libmono-microsoft-build-tasks-v4.0-4.0-cil
libmono-microsoft-build-utilities-v4.0-4.0-cil
libmono-microsoft-build2.0-cil libmono-microsoft-build4.0-cil
libmono-microsoft-csharp4.0-cil libmono-microsoft-visualc10.0-cil
libmono-microsoft-web-infrastructure1.0-cil libmono-microsoft8.0-cil
libmono-npgsql2.0-cil libmono-npgsql4.0-cil libmono-opensystem-c4.0-cil
libmono-oracle2.0-cil libmono-oracle4.0-cil libmono-parallel4.0-cil
libmono-peapi2.0a-cil libmono-peapi4.0a-cil libmono-posix2.0-cil
libmono-posix4.0-cil libmono-rabbitmq2.0-cil libmono-rabbitmq4.0-cil
libmono-relaxng2.0-cil libmono-relaxng4.0-cil libmono-security2.0-cil
libmono-security4.0-cil libmono-sharpzip2.6-cil libmono-sharpzip2.84-cil
libmono-sharpzip4.84-cil libmono-simd2.0-cil libmono-simd4.0-cil
libmono-sqlite2.0-cil libmono-sqlite4.0-cil
libmono-system-componentmodel-composition4.0-cil
libmono-system-componentmodel-dataannotations4.0-cil
libmono-system-configuration-install4.0-cil
libmono-system-configuration4.0-cil libmono-system-core4.0-cil
libmono-system-data-datasetextensions4.0-cil libmono-system-data-linq2.0-cil
libmono-system-data-linq4.0-cil libmono-system-data-services-client4.0-cil
libmono-system-data-services2.0-cil libmono-system-data-services4.0-cil
libmono-system-data2.0-cil libmono-system-data4.0-cil
libmono-system-design4.0-cil libmono-system-drawing-design4.0-cil
libmono-system-drawing4.0-cil libmono-system-dynamic4.0-cil
libmono-system-enterpriseservices4.0-cil
libmono-system-identitymodel-selectors4.0-cil
libmono-system-identitymodel4.0-cil
libmono-system-io-compression-filesystem4.0-cil
libmono-system-io-compression4.0-cil libmono-system-json-microsoft4.0-cil
libmono-system-json2.0-cil libmono-system-json4.0-cil
libmono-system-ldap-protocols4.0-cil libmono-system-ldap2.0-cil
libmono-system-ldap4.0-cil libmono-system-management4.0-cil
libmono-system-messaging2.0-cil libmono-system-messaging4.0-cil
libmono-system-net-http-formatting4.0-cil
libmono-system-net-http-webrequest4.0-cil libmono-system-net-http4.0-cil
libmono-system-net2.0-cil libmono-system-net4.0-cil
libmono-system-numerics4.0-cil libmono-system-reactive-core2.2-cil
libmono-system-reactive-debugger2.2-cil
libmono-system-reactive-experimental2.2-cil
libmono-system-reactive-interfaces2.2-cil
libmono-system-reactive-linq2.2-cil
libmono-system-reactive-observable-aliases0.0-cil
libmono-system-reactive-platformservices2.2-cil
libmono-system-reactive-providers2.2-cil
libmono-system-reactive-runtime-remoting2.2-cil
libmono-system-reactive-windows-forms2.2-cil
libmono-system-reactive-windows-threading2.2-cil
libmono-system-runtime-caching4.0-cil
libmono-system-runtime-durableinstancing4.0-cil
libmono-system-runtime-serialization-formatters-soap4.0-cil
libmono-system-runtime-serialization4.0-cil libmono-system-runtime2.0-cil
libmono-system-runtime4.0-cil libmono-system-security4.0-cil
libmono-system-servicemodel-activation4.0-cil
libmono-system-servicemodel-discovery4.0-cil
libmono-system-servicemodel-routing4.0-cil
libmono-system-servicemodel-web4.0-cil libmono-system-servicemodel4.0a-cil
libmono-system-serviceprocess4.0-cil
libmono-system-threading-tasks-dataflow4.0-cil
libmono-system-transactions4.0-cil libmono-system-web-abstractions4.0-cil
libmono-system-web-applicationservices4.0-cil
libmono-system-web-dynamicdata4.0-cil
libmono-system-web-extensions-design4.0-cil
libmono-system-web-extensions4.0-cil libmono-system-web-http-selfhost4.0-cil
libmono-system-web-http-webhost4.0-cil libmono-system-web-http4.0-cil
libmono-system-web-mvc1.0-cil libmono-system-web-mvc2.0-cil
libmono-system-web-mvc3.0-cil libmono-system-web-razor2.0-cil
libmono-system-web-routing4.0-cil libmono-system-web-services4.0-cil
libmono-system-web-webpages-deployment2.0-cil
libmono-system-web-webpages-razor2.0-cil libmono-system-web-webpages2.0-cil
libmono-system-web2.0-cil libmono-system-web4.0-cil
libmono-system-windows-forms-datavisualization4.0a-cil
libmono-system-windows-forms4.0-cil libmono-system-windows4.0-cil
libmono-system-xaml4.0-cil libmono-system-xml-linq4.0-cil
libmono-system-xml-serialization4.0-cil libmono-system-xml4.0-cil
libmono-system2.0-cil libmono-system4.0-cil libmono-tasklets2.0-cil
libmono-tasklets4.0-cil libmono-wcf3.0a-cil libmono-web4.0-cil
libmono-webbrowser2.0-cil libmono-webbrowser4.0-cil
libmono-webmatrix-data4.0-cil libmono-windowsbase3.0-cil
libmono-windowsbase4.0-cil libmono-winforms2.0-cil
libmono-xbuild-tasks2.0-cil libmono-xbuild-tasks4.0-cil libmono2.0-cil
libmonoboehm-2.0-1 libmonoboehm-2.0-dev libnatpmp1 libnunit-cil-dev
libnunit2.6-cil libofono-qt1 libois-1.3.0 libonline-accounts-client1
liboxideqt-qmlplugin liboxideqtcore0 libpano13-2 libpano13-bin libpgf6
libpgm-5.1-0 libprocess-cpp1 libpyzy-1.0-0 libqdjango-db0 libqgsttools-p1
libqmenumodel0 libqt4-help libqt4-scripttools libqt4-test
libqt5multimedia5-plugins libqt5multimediaquick-p5 libqt5multimediawidgets5
libqt5systeminfo5 libqt5webkit5-qmlwebkitplugin libqt5xmlpatterns5
libqtassistantclient4 libsilly libsystemsettings1 libtelepathy-farstream3
libubuntu-application-api-mirserver1 libubuntu-application-api1
libubuntu-download-manager-client0 libubuntu-download-manager-common0
libubuntu-download-manager-priv0 libubuntu-location-service0
libubuntu-platform-hardware-api1 libubuntuoneauth-2.0-0 libufe-xidgetter0
libunity-api0 libunity-mir1 libunity-scopes1 libunwind8
libusermetricsoutput1 libvigraimpex5 libwebkit1.1-cil
libwhoopsie-preferences0 libzmq3 libzmqpp3 libzthread-2.3-2 libzzip-0-13
mediascanner2.0 mono-4.0-gac mono-csharp-shell mono-devel mono-gac mono-mcs
mono-runtime mono-runtime-common mono-runtime-sgen mono-xbuild monodoc-base
monodoc-browser monodoc-manual mplayerthumbs ofono oneconf-common
packagekit-tools powerd psensor-common python-lxml python-numpy
python-oneconf python-qt4 python-sip python3-brlapi python3-cairo
python3-gi-cairo python3-gnupg python3-louis python3-oneconf
python3-piston-mini-client python3-pyatspi python3-speechd python3-xdg
qmenumodel-qml qtdeclarative5-accounts-plugin qtdeclarative5-dee-plugin
qtdeclarative5-dialogs-plugin qtdeclarative5-folderlistmodel-plugin
qtdeclarative5-gsettings1.0 qtdeclarative5-privatewidgets-plugin
qtdeclarative5-qtmultimedia-plugin qtdeclarative5-systeminfo-plugin
qtdeclarative5-ubuntu-content0.1 qtdeclarative5-ubuntu-settings-components
qtdeclarative5-ubuntu-settings-components-assets
qtdeclarative5-ubuntu-thumbnailer0.1
qtdeclarative5-ubuntu-ui-extras-browser-plugin
qtdeclarative5-ubuntu-ui-extras-browser-plugin-assets
qtdeclarative5-ubuntuone1.0 qtdeclarative5-unity-notifications-plugin
qtdeclarative5-xmllistmodel-plugin shotwell-common signon-plugin-password
smc-data sqlite3 suru-icon-theme system-image-common system-image-dbus
thumbnailer-service ubuntu-download-manager ubuntu-keyboard-data
ubuntu-mobile-icons ubuntu-purchase-service ubuntu-touch-sounds
ubuntuone-client-data ubuntuone-credentials-common unity-plugin-scopes
unity-scope-mediascanner2 unity-scope-scopes unity-webapps-qml
usermetricsservice webapp-container webbrowser-app whoopsie-preferences
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  apparmor-easyprof apparmor-easyprof-ubuntu click click-apparmor
  foomatic-filters gir1.2-click-0.4 gir1.2-gee-0.8 gir1.2-json-1.0
  libclick-0.4-0 liblttng-ust-ctl2 liblttng-ust0 libupstart-app-launch2
  liburcu1 libwebkit1.1-cil monodoc-browser polkit-kde-1 python3-apparmor
  python3-apparmor-click python3-click python3-libapparmor upstart-app-launch
  upstart-app-launch-tools
Suggested packages:
  liblcms2-utils:i386 monodoc-webkit-manual
The following packages will be REMOVED:
  account-plugin-aim account-plugin-facebook account-plugin-flickr
  account-plugin-google account-plugin-identica account-plugin-jabber
  account-plugin-salut account-plugin-twitter account-plugin-windows-live
  account-plugin-yahoo activity-log-manager
  activity-log-manager-control-center aisleriot alacarte apport-gtk apturl
  bamfdaemon baobab bluez-cups brasero brasero-cdrkit cheese colord cups
  cups-core-drivers cups-filters cups-filters-core-drivers deja-dup
  deja-dup-backend-gvfs digikam dolphin empathy enblend enfuse eog evince
  evolution-data-server file-roller friends-facebook friends-identica
  friends-twitter gcalctool gcr gedit ghostscript ghostscript-x gimp
  gir1.2-appindicator3-0.1 gir1.2-gnomebluetooth-1.0 gir1.2-gtk-3.0
  gir1.2-gtksource-3.0 gir1.2-panelapplet-4.0 gir1.2-peas-1.0 gir1.2-rb-3.0
  gir1.2-totem-1.0 gir1.2-vte-2.90 gir1.2-webkit-3.0 gir1.2-wnck-3.0
  gkbd-capplet gnome-applets gnome-bluetooth gnome-calculator gnome-contacts
  gnome-control-center gnome-disk-utility gnome-font-viewer gnome-icon-theme
  gnome-icon-theme-symbolic gnome-keyring gnome-mahjongg gnome-media
  gnome-mines gnome-nettool gnome-online-accounts gnome-orca gnome-panel
  gnome-power-manager gnome-screensaver gnome-screenshot gnome-session
  gnome-session-bin gnome-session-canberra gnome-session-flashback
  gnome-settings-daemon gnome-sudoku gnome-system-log gnome-system-monitor
  gnome-terminal gnome-user-guide gnome-user-share gnomine
  gstreamer1.0-clutter gtk3-engines-unico gucharmap gvfs-backends
  gwibber-service-facebook gwibber-service-identica gwibber-service-twitter
  hplip hugin humanity-icon-theme ibus ibus-gtk3 ibus-pinyin ibus-table
  imagemagick indicator-applet-complete indicator-application
  indicator-appmenu indicator-bluetooth indicator-keyboard indicator-printers
  inkscape kipi-plugins landscape-client-ui-install language-selector-gnome
  libaccount-plugin-1.0-0 libaccount-plugin-generic-oauth
  libaccount-plugin-google libappindicator3-1 libavahi-ui-gtk3-0
  libbaloowidgets4 libbrasero-media3-1 libcanberra-gtk3-0
  libcanberra-gtk3-module libcdr-0.0-0 libcdr-0.1-1 libcegui-mk2-0.7.6
  libcheese-gtk23 libcheese7 libclutter-1.0-0 libclutter-gst-2.0-0
  libclutter-gtk-1.0-0 libcolord1 libcolorhug1 libdevil1c2 libevdocument3-4
  libevview3-3 libfolks-eds25 libfreeimage3 libgail-3-0 libgcr-3-1
  libgcr-ui-3-1 libgnome-bluetooth11 libgnome-control-center1
  libgnome-desktop-3-7 libgnome-media-profiles-3.0-0 libgnomekbd8
  libgoa-backend-1.0-1 libgrip0 libgs9 libgtk-3-0 libgtk-3-bin libgtkmm-3.0-1
  libgtksourceview-3.0-1 libgucharmap-2-90-7 libgweather-3-6 libgxps2
  libido3-0.1-0 libindicator3-7 libkdcraw23 libkfilemetadata4 liblcms2-2
  libmagick++5 libmagickcore5 libmagickcore5-extra libmagickwand5 libmng2
  libnautilus-extension1a libnm-gtk0 libogre-1.8.0 libpanel-applet-4-0
  libpeas-1.0-0 libpoppler-glib8 libpoppler-qt4-4 libpoppler19 libpoppler44
  libpstoedit0c2a libqtbamf1 libraw9 libreoffice
  libreoffice-avmedia-backend-gstreamer libreoffice-base libreoffice-base-core
  libreoffice-base-drivers libreoffice-calc libreoffice-core libreoffice-draw
  libreoffice-gnome libreoffice-gtk libreoffice-help-en-us libreoffice-help-ru
  libreoffice-impress libreoffice-math libreoffice-ogltrans
  libreoffice-pdfimport libreoffice-presentation-minimizer
  libreoffice-report-builder-bin libreoffice-sdbc-firebird libreoffice-writer
  librhythmbox-core8 libspectre1 libtimezonemap1 libtotem0 libunique-3.0-0
  libunity-2d-private0 libunity-control-center1 libunity-core-6.0-9
  libunity-gtk3-parser0 libunity-misc4 libunity-webapps0 libvte-2.90-9
  libwebkitgtk-3.0-0 libwnck-3-0 libyelp0 light-themes mahjongg
  mcp-account-manager-uoa metacity modemmanager monodevelop mousetweaks
  mythes-ru nautilus nautilus-sendto nautilus-sendto-empathy nautilus-share
  nepomuk-core-runtime network-manager-gnome network-manager-pptp-gnome
  notification-daemon notify-osd okular onboard onboard-data oneconf
  overlay-scrollbar overlay-scrollbar-gtk2 overlay-scrollbar-gtk3 perlmagick
  policykit-1-gnome poppler-utils printer-driver-gutenprint
  printer-driver-hpcups printer-driver-pnm2ppa printer-driver-postscript-hp
  printer-driver-ptouch printer-driver-pxljr printer-driver-sag-gdi
  printer-driver-splix psensor pstoedit python-aptdaemon.gtk3widgets
  python-imaging python-pil python-ubuntu-sso-client python-uniconvertor
  python3-aptdaemon.gtk3widgets python3-uno remmina remmina-plugin-rdp
  remmina-plugin-vnc rhythmbox rhythmbox-mozilla rhythmbox-plugin-cdrecorder
  rhythmbox-plugin-magnatune rhythmbox-plugin-zeitgeist rhythmbox-plugins
  seahorse sessioninstaller shotwell simple-scan smc smc-music software-center
  software-properties-gtk steam-launcher synaptic system-config-printer-gnome
  telepathy-indicator totem totem-mozilla totem-plugins transmission-gtk
  ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-mono
  ubuntu-release-upgrader-gtk ubuntu-session ubuntu-sso-client
  ubuntu-sso-client-qt unity unity-2d unity-2d-common unity-2d-panel
  unity-2d-shell unity-2d-spread unity-asset-pool unity-control-center
  unity-control-center-signon unity-greeter unity-gtk3-module
  unity-lens-applications unity-scope-calculator unity-scope-gdrive
  unity-scope-manpages unity-services unity-settings-daemon
  unity-webapps-common unity-webapps-service update-manager update-notifier
  usb-creator-gtk vino webaccounts-extension-common xdg-user-dirs-gtk
  xdiagnose xerox-phaser-6000-6010:i386 xul-ext-unity xul-ext-webaccounts
  xul-ext-websites-integration yelp zeitgeist zeitgeist-datahub zenity
The following NEW packages will be installed:
  apparmor-easyprof apparmor-easyprof-ubuntu click click-apparmor
  foomatic-filters gir1.2-click-0.4 gir1.2-gee-0.8 gir1.2-json-1.0
  libclick-0.4-0 liblcms2-2:i386 liblttng-ust-ctl2 liblttng-ust0
  libupstart-app-launch2 liburcu1 libwebkit1.1-cil monodoc-browser
  polkit-kde-1 python3-apparmor python3-apparmor-click python3-click
  python3-libapparmor upstart-app-launch upstart-app-launch-tools
0 upgraded, 23 newly installed, 326 to remove and 0 not upgraded.
Need to get 901 kB of archives.
After this operation, 936 MB disk space will be freed.
Do you want to continue? [Y/n]

At this point I responded with 'n', consequences of the above would be dire.
```

---

### Post by jhay2 on 2014-11-03
did you already install ia32-libs ?
after adding ubuntu-ppa/wine , you must  "sudo update" it before anything else


if nothing works .. you may consider installing the development version "sudo apt-get install wine1.7"

---

### Post by temmokan on 2014-11-04
> **jhay2 said:**
> did you already install ia32-libs ?
after adding ubuntu-ppa/wine , you must  "sudo update" it before anything else


if nothing works .. you may consider installing the development version "sudo apt-get install wine1.7"

ia32-libs is installed.

'dpkg --get-selections | grep hold' returns nothing (so, looks like there are NO broken/hold packages).

Attempts to install wine1.7 result in exactly the same weird report of unmet dependencies:

```
$ sudo apt-get install wine1.7(blah blah blah)
The following packages have unmet dependencies:
 wine1.7 : Depends: wine1.7-i386 (= 1:1.7.28-0ubuntu2~ppa1)
E: Unable to correct problems, you have held broken packages.

$ sudo apt-get install wine1.7-i386
(blah blah blah)The following packages have unmet dependencies:
 wine1.7-i386:i386 : Depends: liblcms2-2:i386 (>= 2.2+git20110628) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

and so on, see the rest in original post. 

I ceased to understand what's wrong with Ubuntu after 12.04 to 14.04 upgrade. The only remaining assumption is that Wine PPA is broken for 14.* series, with misconfigured dependencies.

Re-installing OS is last resort, I prefer to find and fix the issue.

---

### Post by jhay2 on 2014-11-15
try to install wine from git maybe it would work

---

