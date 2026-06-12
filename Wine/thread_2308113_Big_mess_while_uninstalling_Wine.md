---
title: "Big mess while uninstalling Wine"
date: 2015-12-31
forum: Wine
---

### Post by White_Wind on 2015-12-31
I am in panic right now, I think I've messed things up big time.
I wanted to reinstall Wine, so to uninstall it first I typed:

```
sudo apt-get remove --purge wine*
```

and a whole bunch of things got uninstalled. Here is what I got:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'kmfl-keyboards-mywin' for regex 'wine*'
Note, selecting 'kwin-style-qtcurve' for regex 'wine*'
Note, selecting 'windows-el' for regex 'wine*'
Note, selecting 'avifile-win32-plugin' for regex 'wine*'
Note, selecting 'libswingworker-java-doc' for regex 'wine*'
Note, selecting 'libunwind8' for regex 'wine*'
Note, selecting 'navit-graphics-gtk-drawing-area' for regex 'wine*'
Note, selecting 'golang-go-darwin-amd64' for regex 'wine*'
Note, selecting 'python2.7-windowmocker' for regex 'wine*'
Note, selecting 'hwinfo' for regex 'wine*'
Note, selecting 'libchewing2-dev' for regex 'wine*'
Note, selecting 'winff-gtk2' for regex 'wine*'
Note, selecting 'winefish' for regex 'wine*'
Note, selecting 'wine64-bin' for regex 'wine*'
Note, selecting 'winff-qt' for regex 'wine*'
Note, selecting 'scim-chewing' for regex 'wine*'
Note, selecting 'openwince-jtag' for regex 'wine*'
Note, selecting 'petitboot-twin' for regex 'wine*'
Note, selecting 'libswing-layout-java' for regex 'wine*'
Note, selecting 'libswing-layout-java-doc' for regex 'wine*'
Note, selecting 'plplot12-driver-xwin' for regex 'wine*'
Note, selecting 'libswingx-java' for regex 'wine*'
Note, selecting 'libfreehep-swing-java' for regex 'wine*'
Note, selecting 'libchewing3-dbg' for regex 'wine*'
Note, selecting 'kdeartwork-theme-window' for regex 'wine*'
Note, selecting 'libx11-windowhierarchy-perl' for regex 'wine*'
Note, selecting 'libwine-gecko-dbg-2.21' for regex 'wine*'
Note, selecting 'golang-go-windows-amd64' for regex 'wine*'
Note, selecting 'winbind' for regex 'wine*'
Note, selecting 'libtwin0' for regex 'wine*'
Note, selecting 'kde-window-manager-active-gles' for regex 'wine*'
Note, selecting 'winff-doc' for regex 'wine*'
Note, selecting 'q4wine-unstable' for regex 'wine*'
Note, selecting 'win32-loader' for regex 'wine*'
Note, selecting 'libchewing' for regex 'wine*'
Note, selecting 'gnome-window-applets' for regex 'wine*'
Note, selecting 'wine1.4:any' for regex 'wine*'
Note, selecting 'wininfo' for regex 'wine*'
Note, selecting 'libkwineffects1abi4' for regex 'wine*'
Note, selecting 'wine-i386' for regex 'wine*'
Note, selecting 'freepwing' for regex 'wine*'
Note, selecting 'libchewing3-dev' for regex 'wine*'
Note, selecting 'winpdb' for regex 'wine*'
Note, selecting 'libkwinglesutils1' for regex 'wine*'
Note, selecting 'wine1.6-dbg' for regex 'wine*'
Note, selecting 'libwind0-heimdal' for regex 'wine*'
Note, selecting 'phylowin' for regex 'wine*'
Note, selecting 'wine1.4-amd64' for regex 'wine*'
Note, selecting 'matchbox-window-manager' for regex 'wine*'
Note, selecting 'wine1.6-i386' for regex 'wine*'
Note, selecting 'wine1.6-dev' for regex 'wine*'
Note, selecting 'windowlab' for regex 'wine*'
Note, selecting 'wine64-bin-unstable' for regex 'wine*'
Note, selecting 'libworldwind-java' for regex 'wine*'
Note, selecting 'ibus-chewing' for regex 'wine*'
Note, selecting 'libwings-dev' for regex 'wine*'
Note, selecting 'account-plugin-windows-live' for regex 'wine*'
Note, selecting 'winswitch' for regex 'wine*'
Note, selecting 'libwin-hivex-perl' for regex 'wine*'
Note, selecting 'wine' for regex 'wine*'
Note, selecting 'wing' for regex 'wine*'
Note, selecting 'kde-window-manager-gles' for regex 'wine*'
Note, selecting 'wink' for regex 'wine*'
Note, selecting 'worldwind' for regex 'wine*'
Note, selecting 'wine1.5-amd64' for regex 'wine*'
Note, selecting 'libmono-system-windows-forms-datavisualization4.0a-cil' for regex 'wine*'
Note, selecting 'wine1.5-i386' for regex 'wine*'
Note, selecting 'q4wine' for regex 'wine*'
Note, selecting 'winetricks' for regex 'wine*'
Note, selecting 'winkeydaemon' for regex 'wine*'
Note, selecting 'kwin-style-skulpture' for regex 'wine*'
Note, selecting 'mate-window-manager' for regex 'wine*'
Note, selecting 'python3-windowmocker' for regex 'wine*'
Note, selecting 'libkwinactiveeffects1abi4' for regex 'wine*'
Note, selecting 'libtwin-dev' for regex 'wine*'
Note, selecting 'shiki-wine-theme' for regex 'wine*'
Note, selecting 'libcsfml-window2' for regex 'wine*'
Note, selecting 'libkwinglutils1abi3' for regex 'wine*'
Note, selecting 'libmate-window-settings-dbg' for regex 'wine*'
Note, selecting 'libunwind-setjmp0-dbg' for regex 'wine*'
Note, selecting 'wings3d' for regex 'wine*'
Note, selecting 'libnss-winbind' for regex 'wine*'
Note, selecting 'libmate-window-settings1' for regex 'wine*'
Note, selecting 'kde-window-manager' for regex 'wine*'
Note, selecting 'libunwind1-dev' for regex 'wine*'
Note, selecting 'libmono-system-drawing4.0-cil' for regex 'wine*'
Note, selecting 'libswingx1-java-doc' for regex 'wine*'
Note, selecting 'libunwind7-dev' for regex 'wine*'
Note, selecting 'libparse-win32registry-perl' for regex 'wine*'
Note, selecting 'libswingx1-java' for regex 'wine*'
Note, selecting 'wine1.4-i386' for regex 'wine*'
Note, selecting 'wine-mono0.0.8' for regex 'wine*'
Note, selecting 'wine1.6-amd64' for regex 'wine*'
Note, selecting 'wine-dev' for regex 'wine*'
Note, selecting 'python-windowmocker' for regex 'wine*'
Note, selecting 'libmate-window-settings-dev' for regex 'wine*'
Note, selecting 'avant-window-navigator' for regex 'wine*'
Note, selecting 'libmono-system-reactive-windows-threading2.1-cil' for regex 'wine*'
Note, selecting 'avant-window-navigator-trunk' for regex 'wine*'
Note, selecting 'libmono-system-drawing-design4.0-cil' for regex 'wine*'
Note, selecting 'libsfml-window2' for regex 'wine*'
Note, selecting 'libunwind-setjmp0-dev' for regex 'wine*'
Note, selecting 'ibus-chewing-dbg' for regex 'wine*'
Note, selecting 'openwince-include' for regex 'wine*'
Note, selecting 'wine-amd64' for regex 'wine*'
Note, selecting 'wine1.6:any' for regex 'wine*'
Note, selecting 'qtdeclarative5-window-plugin' for regex 'wine*'
Note, selecting 'fcitx-chewing' for regex 'wine*'
Note, selecting 'libunwind8-dbg' for regex 'wine*'
Note, selecting 'libchewing-dev' for regex 'wine*'
Note, selecting 'wine-gecko2.21' for regex 'wine*'
Note, selecting 'kwin-style-dekorator' for regex 'wine*'
Note, selecting 'libchewing-data' for regex 'wine*'
Note, selecting 'libapache2-mod-auth-ntlm-winbind' for regex 'wine*'
Note, selecting 'golang-go-windows-386' for regex 'wine*'
Note, selecting 'libmono-system-reactive-windows-forms2.1-cil' for regex 'wine*'
Note, selecting 'libwings2' for regex 'wine*'
Note, selecting 'wine1.0' for regex 'wine*'
Note, selecting 'wine1.2' for regex 'wine*'
Note, selecting 'wine1.3' for regex 'wine*'
Note, selecting 'wine-unstable' for regex 'wine*'
Note, selecting 'wine1.4' for regex 'wine*'
Note, selecting 'wine1.5' for regex 'wine*'
Note, selecting 'wine1.6' for regex 'wine*'
Note, selecting 'x-window-system-core' for regex 'wine*'
Note, selecting 'libchewing3-data' for regex 'wine*'
Note, selecting 'kde-window-manager-common' for regex 'wine*'
Note, selecting 'libunwind8-dev' for regex 'wine*'
Note, selecting 'libkwinactiveglutils1abi3' for regex 'wine*'
Note, selecting 'libmono-windowsbase3.0-cil' for regex 'wine*'
Note, selecting 'winwrangler' for regex 'wine*'
Note, selecting 'plplot11-driver-xwin' for regex 'wine*'
Note, selecting 'libmono-system-windows-forms4.0-cil' for regex 'wine*'
Note, selecting 'libmono-system-reactive-windows-threading2.2-cil' for regex 'wine*'
Note, selecting 'golang-go-darwin-386' for regex 'wine*'
Note, selecting 'wing-data' for regex 'wine*'
Note, selecting 'libmono-winforms2.0-cil' for regex 'wine*'
Note, selecting 'libkwinactiveglesutils1' for regex 'wine*'
Note, selecting 'arc-wine' for regex 'wine*'
Note, selecting 'x-window-manager' for regex 'wine*'
Note, selecting 'libjenkins-winstone-java-doc' for regex 'wine*'
Note, selecting 'fte-xwindow' for regex 'wine*'
Note, selecting 'libmono-system-windows-forms-datavisualization4.0-cil' for regex 'wine*'
Note, selecting 'hime-chewing' for regex 'wine*'
Note, selecting 'libswingworker-java' for regex 'wine*'
Note, selecting 'wine-gecko' for regex 'wine*'
Note, selecting 'libjenkins-winstone-java' for regex 'wine*'
Note, selecting 'pd-windowing' for regex 'wine*'
Note, selecting 'libmono-windowsbase4.0-cil' for regex 'wine*'
Note, selecting 'libmate-window-settings1-dbg' for regex 'wine*'
Note, selecting 'libswingx-java-doc' for regex 'wine*'
Note, selecting 'libmono-system-reactive-windows-forms2.2-cil' for regex 'wine*'
Note, selecting 'libpam-winbind' for regex 'wine*'
Note, selecting 'kwin4-style-bespin' for regex 'wine*'
Note, selecting 'ucimf-chewing' for regex 'wine*'
Note, selecting 'kwin-style-crystal' for regex 'wine*'
Note, selecting 'gextractwinicons' for regex 'wine*'
Note, selecting 'uim-chewing' for regex 'wine*'
Note, selecting 'twinkle' for regex 'wine*'
Note, selecting 'emacs-window-layout' for regex 'wine*'
Note, selecting 'libchewing3' for regex 'wine*'
Note, selecting 'gnome-wine-icon-theme' for regex 'wine*'
Note, selecting 'x-window-system' for regex 'wine*'
Note, selecting 'gcin-chewing' for regex 'wine*'
Note, selecting 'libchewing1-dev' for regex 'wine*'
Note, selecting 'winbind4' for regex 'wine*'
Note, selecting 'science-viewing' for regex 'wine*'
Note, selecting 'libjswingreader-java' for regex 'wine*'
Note, selecting 'plplot9-driver-xwin' for regex 'wine*'
Note, selecting 'libmono-system-windows4.0-cil' for regex 'wine*'
Note, selecting 'wine1.4-dbg' for regex 'wine*'
Note, selecting 'twine' for regex 'wine*'
Note, selecting 'libunwind-setjmp0' for regex 'wine*'
Note, selecting 'kde-window-manager-active' for regex 'wine*'
Note, selecting 'winbindd' for regex 'wine*'
Note, selecting 'winff' for regex 'wine*'
Note, selecting 'python-strongwind' for regex 'wine*'
Note, selecting 'winff-dbg' for regex 'wine*'
Note, selecting 'wine-mono' for regex 'wine*'
Note, selecting 'libwine-gecko-2.21' for regex 'wine*'
Note, selecting 'all-knowing-dns' for regex 'wine*'
Note, selecting 'wine1.4-dev' for regex 'wine*'
Note, selecting 'libchewing3' instead of 'libchewing'
Note, selecting 'libchewing3-data' instead of 'libchewing-data'
Package 'libchewing-dev' is not installed, so not removed
Package 'libchewing1-dev' is not installed, so not removed
Package 'libchewing2-dev' is not installed, so not removed
Package 'wink' is not installed, so not removed
Package 'libmono-system-reactive-windows-forms2.1-cil' is not installed, so not removed
Package 'libmono-system-reactive-windows-threading2.1-cil' is not installed, so not removed
Package 'libmono-system-windows-forms-datavisualization4.0-cil' is not installed, so not removed
Package 'libunwind1-dev' is not installed, so not removed
Package 'libunwind7-dev' is not installed, so not removed
Package 'win32-loader' is not installed, so not removed
Package 'winbindd' is not installed, so not removed
Package 'winbind4' is not installed, so not removed
Note, selecting 'xorg' instead of 'x-window-system'
Note, selecting 'xorg' instead of 'x-window-system-core'
Package 'hwinfo' is not installed, so not removed
Package 'winkeydaemon' is not installed, so not removed
Package 'kwin4-style-bespin' is not installed, so not removed
Package 'kde-window-manager-gles' is not installed, so not removed
Package 'kde-window-manager-active-gles' is not installed, so not removed
Package 'avifile-win32-plugin' is not installed, so not removed
Package 'phylowin' is not installed, so not removed
Package 'wings3d' is not installed, so not removed
Package 'plplot11-driver-xwin' is not installed, so not removed
Package 'plplot9-driver-xwin' is not installed, so not removed
Note, selecting 'python-windowmocker' instead of 'python2.7-windowmocker'
Package 'wine64-bin' is not installed, so not removed
Package 'wine64-bin-unstable' is not installed, so not removed
Package 'wine1.2' is not installed, so not removed
Package 'wine1.3' is not installed, so not removed
Package 'wine1.5' is not installed, so not removed
Package 'q4wine-unstable' is not installed, so not removed
Package 'worldwind' is not installed, so not removed
Package 'libworldwind-java' is not installed, so not removed
Package 'arc-wine' is not installed, so not removed
Note, selecting 'wine1.4' instead of 'wine1.4:any'
Note, selecting 'wine1.6-i386:i386' instead of 'wine1.6-i386'
Package 'wine1.0' is not installed, so not removed
Note, selecting 'wine1.6' instead of 'wine1.6:any'
Note, selecting 'wine1.6-amd64' instead of 'wine-amd64'
Note, selecting 'wine1.6-amd64' instead of 'wine1.5-amd64'
Note, selecting 'wine1.6-dev' instead of 'wine-dev'
Package 'wine-unstable' is not installed, so not removed
Note, selecting 'wine-gecko2.21' instead of 'wine-gecko'
Note, selecting 'wine-mono0.0.8' instead of 'wine-mono'
Note, selecting 'wine1.6-i386:i386' instead of 'wine-i386'
Note, selecting 'wine1.6-i386:i386' instead of 'wine1.5-i386'
Package 'mate-window-manager' is not installed, so not removed
Note, selecting 'libmate-window-settings1-dbg' instead of 'libmate-window-settings-dbg'
Package 'avant-window-navigator' is not installed, so not removed
Package 'avant-window-navigator-trunk' is not installed, so not removed
Package 'ibus-chewing' is not installed, so not removed
Package 'ibus-chewing-dbg' is not installed, so not removed
Package 'libchewing3' is not installed, so not removed
Package 'libchewing3-data' is not installed, so not removed
Package 'libchewing3-dbg' is not installed, so not removed
Package 'libchewing3-dev' is not installed, so not removed
Package 'libunwind-setjmp0' is not installed, so not removed
Package 'libunwind-setjmp0-dbg' is not installed, so not removed
Package 'libunwind-setjmp0-dev' is not installed, so not removed
Package 'libunwind8' is not installed, so not removed
Package 'libunwind8-dbg' is not installed, so not removed
Package 'libunwind8-dev' is not installed, so not removed
Package 'all-knowing-dns' is not installed, so not removed
Package 'emacs-window-layout' is not installed, so not removed
Package 'fcitx-chewing' is not installed, so not removed
Package 'freepwing' is not installed, so not removed
Package 'fte-xwindow' is not installed, so not removed
Package 'gcin-chewing' is not installed, so not removed
Package 'gextractwinicons' is not installed, so not removed
Package 'gnome-wine-icon-theme' is not installed, so not removed
Package 'hime-chewing' is not installed, so not removed
Package 'kmfl-keyboards-mywin' is not installed, so not removed
Package 'kwin-style-crystal' is not installed, so not removed
Package 'kwin-style-dekorator' is not installed, so not removed
Package 'kwin-style-qtcurve' is not installed, so not removed
Package 'kwin-style-skulpture' is not installed, so not removed
Package 'libapache2-mod-auth-ntlm-winbind' is not installed, so not removed
Package 'libcsfml-window2' is not installed, so not removed
Package 'libfreehep-swing-java' is not installed, so not removed
Package 'libjenkins-winstone-java' is not installed, so not removed
Package 'libjenkins-winstone-java-doc' is not installed, so not removed
Package 'libjswingreader-java' is not installed, so not removed
Package 'libparse-win32registry-perl' is not installed, so not removed
Package 'libsfml-window2' is not installed, so not removed
Package 'libswing-layout-java' is not installed, so not removed
Package 'libswing-layout-java-doc' is not installed, so not removed
Package 'libswingworker-java' is not installed, so not removed
Package 'libswingworker-java-doc' is not installed, so not removed
Package 'libswingx-java' is not installed, so not removed
Package 'libswingx-java-doc' is not installed, so not removed
Package 'libswingx1-java' is not installed, so not removed
Package 'libswingx1-java-doc' is not installed, so not removed
Package 'libtwin-dev' is not installed, so not removed
Package 'libtwin0' is not installed, so not removed
Package 'libwin-hivex-perl' is not installed, so not removed
Package 'libwine-gecko-2.21' is not installed, so not removed
Package 'libwine-gecko-dbg-2.21' is not installed, so not removed
Package 'libwings-dev' is not installed, so not removed
Package 'libwings2' is not installed, so not removed
Package 'libx11-windowhierarchy-perl' is not installed, so not removed
Package 'matchbox-window-manager' is not installed, so not removed
Package 'navit-graphics-gtk-drawing-area' is not installed, so not removed
Package 'openwince-include' is not installed, so not removed
Package 'openwince-jtag' is not installed, so not removed
Package 'pd-windowing' is not installed, so not removed
Package 'petitboot-twin' is not installed, so not removed
Package 'plplot12-driver-xwin' is not installed, so not removed
Package 'python-strongwind' is not installed, so not removed
Package 'python-windowmocker' is not installed, so not removed
Package 'python3-windowmocker' is not installed, so not removed
Package 'q4wine' is not installed, so not removed
Package 'science-viewing' is not installed, so not removed
Package 'scim-chewing' is not installed, so not removed
Package 'shiki-wine-theme' is not installed, so not removed
Package 'twinkle' is not installed, so not removed
Package 'ucimf-chewing' is not installed, so not removed
Package 'uim-chewing' is not installed, so not removed
Package 'windowlab' is not installed, so not removed
Package 'windows-el' is not installed, so not removed
Package 'wine1.4' is not installed, so not removed
Package 'wine1.4-amd64' is not installed, so not removed
Package 'wine1.4-dbg' is not installed, so not removed
Package 'wine1.4-dev' is not installed, so not removed
Package 'wine1.6-dbg' is not installed, so not removed
Package 'wine1.6-dev' is not installed, so not removed
Package 'winefish' is not installed, so not removed
Package 'winff' is not installed, so not removed
Package 'winff-dbg' is not installed, so not removed
Package 'winff-doc' is not installed, so not removed
Package 'winff-gtk2' is not installed, so not removed
Package 'winff-qt' is not installed, so not removed
Package 'wing' is not installed, so not removed
Package 'wing-data' is not installed, so not removed
Package 'wininfo' is not installed, so not removed
Package 'winpdb' is not installed, so not removed
Package 'winswitch' is not installed, so not removed
Package 'winwrangler' is not installed, so not removed
Package 'account-plugin-windows-live' is not installed, so not removed
Package 'libmono-system-drawing-design4.0-cil' is not installed, so not removed
Package 'libmono-system-drawing4.0-cil' is not installed, so not removed
Package 'libmono-system-reactive-windows-forms2.2-cil' is not installed, so not removed
Package 'libmono-system-reactive-windows-threading2.2-cil' is not installed, so not removed
Package 'libmono-system-windows-forms-datavisualization4.0a-cil' is not installed, so not removed
Package 'libmono-system-windows-forms4.0-cil' is not installed, so not removed
Package 'libmono-system-windows4.0-cil' is not installed, so not removed
Package 'libmono-windowsbase3.0-cil' is not installed, so not removed
Package 'libmono-windowsbase4.0-cil' is not installed, so not removed
Package 'libmono-winforms2.0-cil' is not installed, so not removed
Package 'qtdeclarative5-window-plugin' is not installed, so not removed
Package 'kde-window-manager' is not installed, so not removed
Package 'kde-window-manager-active' is not installed, so not removed
Package 'kde-window-manager-common' is not installed, so not removed
Package 'kdeartwork-theme-window' is not installed, so not removed
Package 'libkwinactiveeffects1abi4' is not installed, so not removed
Package 'libkwinactiveglesutils1' is not installed, so not removed
Package 'libkwinactiveglutils1abi3' is not installed, so not removed
Package 'libkwineffects1abi4' is not installed, so not removed
Package 'libkwinglesutils1' is not installed, so not removed
Package 'libkwinglutils1abi3' is not installed, so not removed
Package 'golang-go-darwin-386' is not installed, so not removed
Package 'golang-go-darwin-amd64' is not installed, so not removed
Package 'golang-go-windows-386' is not installed, so not removed
Package 'golang-go-windows-amd64' is not installed, so not removed
Package 'twine' is not installed, so not removed
Package 'libmate-window-settings-dev' is not installed, so not removed
Package 'libmate-window-settings1-dbg' is not installed, so not removed
Package 'gnome-window-applets' is not installed, so not removed
The following packages were automatically installed and are no longer required:
  apturl-common attr brasero-common dvd+rw-tools fonts-horai-umefont
  gdebi-core gir1.2-notify-0.7 gir1.2-packagekitglib-1.0 gnome-exe-thumbnailer
  growisofs icoutils libaio1 libasn1-8-heimdal:i386 libasound2:i386
  libasound2-plugins:i386 libassuan0 libasyncns0:i386 libatk-bridge2.0-0:i386
  libatk1.0-0:i386 libatspi2.0-0:i386 libavahi-client3:i386
  libavahi-common-data:i386 libavahi-common3:i386 libboost-system1.54.0
  libburn4 libcairo2:i386 libcapi20-3 libcapi20-3:i386 libcdr-0.0-0
  libcups2:i386 libdatrie1:i386 libevent-2.0-5 libexif12:i386 libflac8:i386
  libfontconfig1:i386 libfreetype6:i386 libgail18:i386 libgcrypt11:i386
  libgcrypt20 libgd3:i386 libgdk-pixbuf2.0-0:i386 libgif4:i386
  libglib2.0-0:i386 libglu1-mesa:i386 libgmime-2.6-0 libgnutls26:i386
  libgpg-error0:i386 libgpgme11 libgphoto2-6:i386 libgphoto2-port10:i386
  libgraphite2-3:i386 libgssapi-krb5-2:i386 libgssapi3-heimdal:i386
  libgstreamer-plugins-base0.10-0:i386 libgstreamer0.10-0:i386
  libgtk2.0-0:i386 libguess1 libharfbuzz0b:i386 libhcrypto4-heimdal:i386
  libheimbase1-heimdal:i386 libheimntlm0-heimdal:i386 libhx509-5-heimdal:i386
  libice6:i386 libieee1284-3:i386 libisofs6 libjack-jackd2-0:i386
  libjasper1:i386 libjbig0:i386 libjpeg-turbo8:i386 libjpeg8:i386 libjte1
  libk5crypto3:i386 libkeyutils1:i386 libkrb5-26-heimdal:i386 libkrb5-3:i386
  libkrb5support0:i386 liblcms2-2:i386 libldap-2.4-2:i386 libltdl7:i386
  libminiupnpc8 libmpg123-0:i386 libmspub-0.0-0 libnatpmp1 libodbc1
  libogg0:i386 libopenal1:i386 liborc-0.4-0:i386 liborcus-0.6-0 libosmesa6
  libosmesa6:i386 libp11-kit-gnome-keyring:i386 libp11-kit0:i386
  libpackagekit-glib2-16 libpango-1.0-0:i386 libpangocairo-1.0-0:i386
  libpangoft2-1.0-0:i386 libpixman-1-0:i386 libpulse0:i386
  libroken18-heimdal:i386 librubberband2 libsamplerate0:i386 libsane:i386
  libsasl2-2:i386 libsasl2-modules:i386 libsasl2-modules-db:i386
  libsdl-ttf2.0-0 libsm6:i386 libsndfile1:i386 libsoxr0 libspeexdsp1:i386
  libsqlite3-0:i386 libssh-4 libssl1.0.0:i386 libtasn1-6:i386 libthai0:i386
  libtiff5:i386 libuchardet0 libusb-1.0-0:i386 libv4l-0:i386
  libv4lconvert0:i386 libva-x11-1 libvisio-0.0-0 libvorbis0a:i386
  libvorbisenc2:i386 libvpx1:i386 libwind0-heimdal:i386 libwrap0:i386
  libxcb-render0:i386 libxcb-shm0:i386 libxcomposite1:i386 libxcursor1:i386
  libxi6:i386 libxinerama1:i386 libxml2:i386 libxpm4:i386 libxrandr2:i386
  libxrender1:i386 libxslt1.1:i386 libxt6:i386 linux-headers-3.13.0-39
  linux-headers-3.13.0-39-generic linux-headers-3.13.0-44
  linux-headers-3.13.0-44-generic ocl-icd-libopencl1:i386 odbcinst
  odbcinst1debian2 p11-kit-modules:i386 packagekit packagekit-backend-aptcc
  python-dnspython python-gnomekeyring python3-packagekit tdb-tools
  transmission-common ttf-mscorefonts-installer unixodbc wine-gecko2.21:i386
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  apt-transport-https* apturl* brasero* brasero-cdrkit* caja-gksu* compiz*
  compiz-gnome* compiz-mate* curl* deja-dup-backend-gvfs* gconf-service*
  gconf-service-backend* gconf2* gksu* gstreamer0.10-plugins-bad*
  gstreamer1.0-plugins-bad* gvfs-backends* kerneloops-daemon*
  libbrasero-media3-1* libcmis-0.4-4* libcurl3* libcurl3-gnutls* libgconf2-4*
  libgksu2-0* libgnome2-0* libgnome2-bin* libgnome2-common* libgnomevfs2-0*
  libgnomevfs2-common* libgssapi3-heimdal* libhdb9-heimdal*
  libheimntlm0-heimdal* libhx509-5-heimdal* libkdc2-heimdal*
  libkrb5-26-heimdal* libldap-2.4-2* libldb1* libmate-window-settings1*
  libnss-winbind* libpam-winbind* libquvi7* libraptor2-0* librasqal3* librdf0*
  libreoffice-avmedia-backend-gstreamer* libreoffice-base-core*
  libreoffice-calc* libreoffice-core* libreoffice-draw* libreoffice-gnome*
  libreoffice-gtk* libreoffice-help-en-gb* libreoffice-help-en-us*
  libreoffice-impress* libreoffice-math* libreoffice-ogltrans*
  libreoffice-pdfimport* libreoffice-presentation-minimizer*
  libreoffice-writer* libslv2-9* libsmbclient* libtotem-plparser18*
  libwind0-heimdal* mate-control-center* mate-desktop-environment-core*
  mplayer2* mpv* mythes-en-us* network-manager-gnome* python-gconf*
  python-ldb* python-samba* python-smbc* python3-pycurl*
  python3-software-properties* samba* samba-common-bin* samba-dsdb-modules*
  samba-libs* samba-vfs-modules* seahorse* smbclient* software-center*
  software-properties-common* software-properties-gtk* steam-launcher*
  system-config-printer-common* system-config-printer-gnome* transmission-gtk*
  virtualbox-5.0* whoopsie* winbind* wine* wine-gecko2.21* wine-mono0.0.8*
  wine1.6* wine1.6-amd64* wine1.6-i386:i386* winetricks*
0 upgraded, 0 newly installed, 99 to remove and 0 not upgraded.
After this operation, 854 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 871859 files and directories currently installed.)
Removing apt-transport-https (1.0.1ubuntu2.10) ...
Removing apturl (0.5.2ubuntu4) ...
Removing brasero (3.10.0-0ubuntu1) ...
Purging configuration files for brasero (3.10.0-0ubuntu1) ...
Removing brasero-cdrkit (3.10.0-0ubuntu1) ...
Removing caja-gksu (1.8.0-3~trusty1) ...
Purging configuration files for caja-gksu (1.8.0-3~trusty1) ...
Removing compiz (1:0.9.11.3+14.04.20150313-0ubuntu1.1) ...
Purging configuration files for compiz (1:0.9.11.3+14.04.20150313-0ubuntu1.1) ...
Removing compiz-mate (1:0.9.11.3+14.04.20150313-0ubuntu1.1) ...
Purging configuration files for compiz-mate (1:0.9.11.3+14.04.20150313-0ubuntu1.1) ...
Removing compiz-gnome (1:0.9.11.3+14.04.20150313-0ubuntu1.1) ...
Purging configuration files for compiz-gnome (1:0.9.11.3+14.04.20150313-0ubuntu1.1) ...
Removing steam-launcher (1.0.0.51) ...
Purging configuration files for steam-launcher (1.0.0.51) ...
Removing curl (7.35.0-1ubuntu2.5) ...
Removing deja-dup-backend-gvfs (32.0-0ubuntu2.2~trusty1) ...
Removing network-manager-gnome (0.9.8.8-0ubuntu4.4) ...
Purging configuration files for network-manager-gnome (0.9.8.8-0ubuntu4.4) ...
Removing libreoffice-gnome (1:4.2.8-0ubuntu3) ...
Removing transmission-gtk (2.82-1.1ubuntu3.1) ...
Purging configuration files for transmission-gtk (2.82-1.1ubuntu3.1) ...
Removing gksu (2.0.2-6ubuntu2) ...
Purging configuration files for gksu (2.0.2-6ubuntu2) ...
Removing libgksu2-0 (2.0.13~pre1-6ubuntu4) ...
update-alternatives: removing manually selected alternative - switching libgksu-gconf-defaults to auto mode
Purging configuration files for libgksu2-0 (2.0.13~pre1-6ubuntu4) ...
Removing gstreamer0.10-plugins-bad:amd64 (0.10.23-7.2ubuntu1.1) ...
Removing gstreamer1.0-plugins-bad:amd64 (1.2.4-1~ubuntu1) ...
Removing mate-desktop-environment-core (1.8.0+9~trusty1) ...
Removing software-center (13.10-0ubuntu4.1) ...
Purging configuration files for software-center (13.10-0ubuntu4.1) ...
Removing gvfs-backends (1.20.3-0ubuntu1.2) ...
Removing kerneloops-daemon (0.12+git20090217-3ubuntu8) ...
Purging configuration files for kerneloops-daemon (0.12+git20090217-3ubuntu8) ...
Removing libbrasero-media3-1 (3.10.0-0ubuntu1) ...
Purging configuration files for libbrasero-media3-1 (3.10.0-0ubuntu1) ...
Removing mythes-en-us (1:4.2.1-0ubuntu1.1) ...
Purging configuration files for mythes-en-us (1:4.2.1-0ubuntu1.1) ...
Removing libreoffice-help-en-us (1:4.2.8-0ubuntu1) ...
Removing virtualbox-5.0 (5.0.12-104815~Ubuntu~trusty) ...
Purging configuration files for virtualbox-5.0 (5.0.12-104815~Ubuntu~trusty) ...
Removing whoopsie (0.2.24.6ubuntu2) ...
Purging configuration files for whoopsie (0.2.24.6ubuntu2) ...
Removing libcurl3:amd64 (7.35.0-1ubuntu2.5) ...
Purging configuration files for libcurl3:amd64 (7.35.0-1ubuntu2.5) ...
Removing libtotem-plparser18 (3.10.3-1~trusty) ...
Purging configuration files for libtotem-plparser18 (3.10.3-1~trusty) ...
Removing mpv (2:0.14.0~trusty) ...
Purging configuration files for mpv (2:0.14.0~trusty) ...
Removing software-properties-gtk (0.92.37.6) ...
Removing libgconf2-4:amd64 (3.2.6-0ubuntu2) ...
Removing libpam-winbind:amd64 (2:4.1.6+dfsg-1ubuntu2.14.04.9) ...
Removing libnss-winbind:amd64 (2:4.1.6+dfsg-1ubuntu2.14.04.9) ...
Removing winbind (2:4.1.6+dfsg-1ubuntu2.14.04.9) ...
winbind stop/waiting
Purging configuration files for winbind (2:4.1.6+dfsg-1ubuntu2.14.04.9) ...
Removing samba (2:4.1.6+dfsg-1ubuntu2.14.04.9) ...
nmbd stop/waiting
smbd stop/waiting
Purging configuration files for samba (2:4.1.6+dfsg-1ubuntu2.14.04.9) ...
Removing samba-common-bin (2:4.1.6+dfsg-1ubuntu2.14.04.9) ...
Removing libkdc2-heimdal:amd64 (1.6~git20131207+dfsg-1ubuntu1.1) ...
Purging configuration files for libkdc2-heimdal:amd64 (1.6~git20131207+dfsg-1ubuntu1.1) ...
Removing libhdb9-heimdal:amd64 (1.6~git20131207+dfsg-1ubuntu1.1) ...
Purging configuration files for libhdb9-heimdal:amd64 (1.6~git20131207+dfsg-1ubuntu1.1) ...
Removing samba-dsdb-modules (2:4.1.6+dfsg-1ubuntu2.14.04.9) ...
Purging configuration files for samba-dsdb-modules (2:4.1.6+dfsg-1ubuntu2.14.04.9) ...
Removing wine (1:1.6.2-0ubuntu4) ...
Removing python-samba (2:4.1.6+dfsg-1ubuntu2.14.04.9) ...
Removing python-ldb (1:1.1.16-1) ...
Purging configuration files for python-ldb (1:1.1.16-1) ...
Removing mate-control-center (1.8.3+dfsg1-2~trusty1) ...
Purging configuration files for mate-control-center (1.8.3+dfsg1-2~trusty1) ...
Removing libmate-window-settings1:amd64 (1.8.3+dfsg1-2~trusty1) ...
Purging configuration files for libmate-window-settings1:amd64 (1.8.3+dfsg1-2~trusty1) ...
Removing libslv2-9 (0.6.6+dfsg1-2) ...
Purging configuration files for libslv2-9 (0.6.6+dfsg1-2) ...
Removing libreoffice-avmedia-backend-gstreamer (1:4.2.8-0ubuntu3) ...
Removing libreoffice-calc (1:4.2.8-0ubuntu3) ...
Purging configuration files for libreoffice-calc (1:4.2.8-0ubuntu3) ...
Removing libreoffice-presentation-minimizer (1:4.2.8-0ubuntu3) ...
Removing libreoffice-ogltrans (1:4.2.8-0ubuntu3) ...
Removing libreoffice-impress (1:4.2.8-0ubuntu3) ...
Purging configuration files for libreoffice-impress (1:4.2.8-0ubuntu3) ...
Removing libreoffice-draw (1:4.2.8-0ubuntu3) ...
Purging configuration files for libreoffice-draw (1:4.2.8-0ubuntu3) ...
Removing libreoffice-gtk (1:4.2.8-0ubuntu3) ...
Removing libreoffice-help-en-gb (1:4.2.8-0ubuntu1) ...
Removing libreoffice-math (1:4.2.8-0ubuntu3) ...
Purging configuration files for libreoffice-math (1:4.2.8-0ubuntu3) ...
Removing libreoffice-pdfimport (1:4.2.8-0ubuntu3) ...
Removing smbclient (2:4.1.6+dfsg-1ubuntu2.14.04.9) ...
Removing mplayer2 (2.0-701-gd4c5b7f-2ubuntu2) ...
Removing python-gconf (2.28.1+dfsg-1ubuntu2) ...
Removing system-config-printer-gnome (1.4.3+20140219-0ubuntu2.6) ...
Purging configuration files for system-config-printer-gnome (1.4.3+20140219-0ubuntu2.6) ...
Removing system-config-printer-common (1.4.3+20140219-0ubuntu2.6) ...
Purging configuration files for system-config-printer-common (1.4.3+20140219-0ubuntu2.6) ...
Removing python-smbc (1.0.14.1-0ubuntu2) ...
Removing samba-vfs-modules (2:4.1.6+dfsg-1ubuntu2.14.04.9) ...
Removing seahorse (3.10.2-0ubuntu1) ...
Purging configuration files for seahorse (3.10.2-0ubuntu1) ...
Removing software-properties-common (0.92.37.6) ...
Purging configuration files for software-properties-common (0.92.37.6) ...
Removing wine-gecko2.21:amd64 (2.21-0ubuntu1) ...
Removing wine-mono0.0.8 (0.0.8-0ubuntu1) ...
Removing winetricks (0.0+20140302-0ubuntu2) ...
Removing libreoffice-writer (1:4.2.8-0ubuntu3) ...
Purging configuration files for libreoffice-writer (1:4.2.8-0ubuntu3) ...
Removing libquvi7:amd64 (0.4.1-1ubuntu3) ...
Purging configuration files for libquvi7:amd64 (0.4.1-1ubuntu3) ...
Removing python3-software-properties (0.92.37.6) ...
Removing python3-pycurl (7.19.3-0ubuntu3) ...
Removing libreoffice-base-core (1:4.2.8-0ubuntu3) ...
Removing libsmbclient:amd64 (2:4.1.6+dfsg-1ubuntu2.14.04.9) ...
Purging configuration files for libsmbclient:amd64 (2:4.1.6+dfsg-1ubuntu2.14.04.9) ...
Removing libreoffice-core (1:4.2.8-0ubuntu3) ...
Purging configuration files for libreoffice-core (1:4.2.8-0ubuntu3) ...
Removing libcmis-0.4-4 (0.4.1-3ubuntu4) ...
Purging configuration files for libcmis-0.4-4 (0.4.1-3ubuntu4) ...
Removing samba-libs:amd64 (2:4.1.6+dfsg-1ubuntu2.14.04.9) ...
Purging configuration files for samba-libs:amd64 (2:4.1.6+dfsg-1ubuntu2.14.04.9) ...
Removing libldb1:amd64 (1:1.1.16-1) ...
Purging configuration files for libldb1:amd64 (1:1.1.16-1) ...
Removing librdf0:amd64 (1.0.17-1) ...
Purging configuration files for librdf0:amd64 (1.0.17-1) ...
Removing librasqal3:amd64 (0.9.32-1) ...
Purging configuration files for librasqal3:amd64 (0.9.32-1) ...
Removing libraptor2-0:amd64 (2.0.13-1) ...
Purging configuration files for libraptor2-0:amd64 (2.0.13-1) ...
Removing libcurl3-gnutls:amd64 (7.35.0-1ubuntu2.5) ...
Purging configuration files for libcurl3-gnutls:amd64 (7.35.0-1ubuntu2.5) ...
Removing wine1.6-amd64 (1:1.6.2-0ubuntu4) ...
Purging configuration files for wine1.6-amd64 (1:1.6.2-0ubuntu4) ...
Removing libgnome2-0:amd64 (2.32.1-4ubuntu1) ...
Purging configuration files for libgnome2-0:amd64 (2.32.1-4ubuntu1) ...
Removing libgnome2-bin (2.32.1-4ubuntu1) ...
Removing libgnome2-common (2.32.1-4ubuntu1) ...
Purging configuration files for libgnome2-common (2.32.1-4ubuntu1) ...
Removing libgnomevfs2-0:amd64 (1:2.24.4-1ubuntu6) ...
Purging configuration files for libgnomevfs2-0:amd64 (1:2.24.4-1ubuntu6) ...
Removing libgnomevfs2-common (1:2.24.4-1ubuntu6) ...
Purging configuration files for libgnomevfs2-common (1:2.24.4-1ubuntu6) ...
Removing wine1.6-i386 (1:1.6.2-0ubuntu4) ...
Purging configuration files for wine1.6-i386 (1:1.6.2-0ubuntu4) ...
Removing wine1.6 (1:1.6.2-0ubuntu4) ...
update-binfmts: warning: no executable /usr/bin/wine found, but continuing anyway as you request
Purging configuration files for wine1.6 (1:1.6.2-0ubuntu4) ...
Removing gconf2 (3.2.6-0ubuntu2) ...
Purging configuration files for gconf2 (3.2.6-0ubuntu2) ...
Removing gconf-service (3.2.6-0ubuntu2) ...
Removing gconf-service-backend (3.2.6-0ubuntu2) ...
Removing libldap-2.4-2:amd64 (2.4.31-1+nmu2ubuntu8.2) ...
Purging configuration files for libldap-2.4-2:amd64 (2.4.31-1+nmu2ubuntu8.2) ...
Removing libgssapi3-heimdal:amd64 (1.6~git20131207+dfsg-1ubuntu1.1) ...
Purging configuration files for libgssapi3-heimdal:amd64 (1.6~git20131207+dfsg-1ubuntu1.1) ...
Removing libheimntlm0-heimdal:amd64 (1.6~git20131207+dfsg-1ubuntu1.1) ...
Purging configuration files for libheimntlm0-heimdal:amd64 (1.6~git20131207+dfsg-1ubuntu1.1) ...
Removing libkrb5-26-heimdal:amd64 (1.6~git20131207+dfsg-1ubuntu1.1) ...
Purging configuration files for libkrb5-26-heimdal:amd64 (1.6~git20131207+dfsg-1ubuntu1.1) ...
Removing libhx509-5-heimdal:amd64 (1.6~git20131207+dfsg-1ubuntu1.1) ...
Purging configuration files for libhx509-5-heimdal:amd64 (1.6~git20131207+dfsg-1ubuntu1.1) ...
Removing libwind0-heimdal:amd64 (1.6~git20131207+dfsg-1ubuntu1.1) ...
Purging configuration files for libwind0-heimdal:amd64 (1.6~git20131207+dfsg-1ubuntu1.1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for menu (2.1.46ubuntu1) ...
Processing triggers for libc-bin (2.19-0ubuntu6.6) ...
Processing triggers for libglib2.0-0:i386 (2.40.2-0ubuntu1) ...
Processing triggers for libglib2.0-0:amd64 (2.40.2-0ubuntu1) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Processing triggers for shared-mime-info (1.2-0ubuntu3) ...
Processing triggers for libreoffice-common (1:4.2.8-0ubuntu3) ...
```

I'm freaking out, I'd like to reinstall all the things that got uninstalled. What should I do? I'm not sure how to locate what got uninstalled in that log.
My mind is pudding right now, sorry..

I'm on Mate 14.04.3
Help please

EDIT: to be a bit more precise, I ran the command, let it run till it finished and didn't do anything else after that. I'm still in the ubuntu session, haven't rebooted, didn't shut the terminal off.

---

### Post by howefield on 2015-12-31
> **White_Wind said:**
> ```
The following packages will be REMOVED:
  apt-transport-https* apturl* brasero* brasero-cdrkit* caja-gksu* compiz*
  compiz-gnome* compiz-mate* curl* deja-dup-backend-gvfs* gconf-service*
  gconf-service-backend* gconf2* gksu* gstreamer0.10-plugins-bad*
  gstreamer1.0-plugins-bad* gvfs-backends* kerneloops-daemon*
  libbrasero-media3-1* libcmis-0.4-4* libcurl3* libcurl3-gnutls* libgconf2-4*
  libgksu2-0* libgnome2-0* libgnome2-bin* libgnome2-common* libgnomevfs2-0*
  libgnomevfs2-common* libgssapi3-heimdal* libhdb9-heimdal*
  libheimntlm0-heimdal* libhx509-5-heimdal* libkdc2-heimdal*
  libkrb5-26-heimdal* libldap-2.4-2* libldb1* libmate-window-settings1*
  libnss-winbind* libpam-winbind* libquvi7* libraptor2-0* librasqal3* librdf0*
  libreoffice-avmedia-backend-gstreamer* libreoffice-base-core*
  libreoffice-calc* libreoffice-core* libreoffice-draw* libreoffice-gnome*
  libreoffice-gtk* libreoffice-help-en-gb* libreoffice-help-en-us*
  libreoffice-impress* libreoffice-math* libreoffice-ogltrans*
  libreoffice-pdfimport* libreoffice-presentation-minimizer*
  libreoffice-writer* libslv2-9* libsmbclient* libtotem-plparser18*
  libwind0-heimdal* mate-control-center* mate-desktop-environment-core*
  mplayer2* mpv* mythes-en-us* network-manager-gnome* python-gconf*
  python-ldb* python-samba* python-smbc* python3-pycurl*
  python3-software-properties* samba* samba-common-bin* samba-dsdb-modules*
  samba-libs* samba-vfs-modules* seahorse* smbclient* software-center*
  software-properties-common* software-properties-gtk* steam-launcher*
  system-config-printer-common* system-config-printer-gnome* transmission-gtk*
  virtualbox-5.0* whoopsie* winbind* wine* wine-gecko2.21* wine-mono0.0.8*
  wine1.6* wine1.6-amd64* wine1.6-i386:i386* winetricks*
0 upgraded, 0 newly installed, 99 to remove and 0 not upgraded.
After this operation, 854 MB disk space will be freed.
Do you want to continue? [Y/n] y
```

I'm not sure how to locate what got uninstalled in that log..

Read the log, it is telling you what was to be removed, (in order that you can confirm that you are happy or of course, decline to continue).

---

### Post by PaulW2U on 2015-12-31
> **White_Wind said:**
> I am in panic right now, I think I've messed things up big time.
I wanted to reinstall Wine, so to uninstall it first I typed:

```
sudo apt-get remove --purge wine*
```
apt-get uses the '*' as part of a regular expression and not as a wild card so *wine** in this case means win or wine. [http://askubuntu.com/questions/210976/apt-get-remove-with-wildcard-removed-way-more-than-expected-why](http://askubuntu.com/questions/210976/apt-get-remove-with-wildcard-removed-way-more-than-expected-why) explains this quite well.

Unfortunately you have asked apt-get to remove any package that has either *win* or *wine* in its name and then confirmed that it is ok to do so. apt-get has probably then removed further packages which it sees as no longer being required.

As the list of packages removed is somewhat random, apart from having *win* in their name, I can only suggest that you try to reinstall what has been removed.

---

### Post by White_Wind on 2015-12-31
Sure I went too fast in the process, I read 854 kB when it was 854 MB, and I haven't been careful enough..

Okay now my head is a bit cooler. I'm in the process of listing what was removed.
I have 3 questions:
-In the first part of the log, all the objects introduced by "Note, selecting", those have not been touched?
-For reinstalling everything, does order matter? Do I have, like, to install things backwards from the end of the uninstalling log to the beginning? And can I reinstall everything with just one command?
-What should that command be? sudo apt-get install a b c d etc ?

> **PaulW2U said:**
> apt-get has probably then removed further packages which it sees as no longer being required.

Thank you. And you mean that there could be some packages that were removed and that don't appear in the log?

---

### Post by PaulW2U on 2015-12-31
> **White_Wind said:**
> And you mean that there could be some packages that were removed and that don't appear in the log?
No, the list of packages 'REMOVED' shows many that don't have *win* or *wine* in their name so the list of removed packages will be complete.

You might want to wait for someone else to reply with a more constructive solution but I think its pretty much a "trial and error" situation of trying to reinstall all of the removed packages.

---

### Post by White_Wind on 2015-12-31
> **PaulW2U said:**
> No, the list of packages 'REMOVED' shows many that don't have *win* or *wine* in their name so the list of removed packages will be complete.

You might want to wait for someone else to reply with a more constructive solution but I think its pretty much a "trial and error" situation of trying to reinstall all of the removed packages.

Okay, thank you for the advice.
I will soon post a list of what I wish to be reinstalled, and what config files were deleted.

---

### Post by White_Wind on 2015-12-31
Here is what has to be reinstalled. The packages beginning with a * had their config file deleted.

```
 
 apt-transport-https
 apturl
 *brasero
 brasero-cdrkit
 *caja-gksu
 curl
 deja-dup-backend-gvfs
 gconf-service
 gconf-service-backend
 *gconf2
 *gksu
 gstreamer0.10-plugins-bad
 gstreamer1.0-plugins-bad
 gvfs-backends
 *kerneloops-daemon
 *libbrasero-media3-1
 *libcmis-0.4-4
 *libcurl3
 *libcurl3-gnutls
 libgconf2-4
 *libgksu2-0
 *libgnome2-0
 libgnome2-bin
 *libgnome2-common
 *libgnomevfs2-0
 *libgnomevfs2-common
 *libgssapi3-heimdal
 *libhdb9-heimdal
 *libheimntlm0-heimdal
 *libhx509-5-heimdal
 *libkdc2-heimdal
 *libkrb5-26-heimdal
 *libldap-2.4-2
 *libldb1
 *libmate-window-settings1
 libnss-winbind
 libpam-winbind
 *libquvi7
 *libraptor2-0
 *librasqal3
 *librdf0
 libreoffice-avmedia-backend-gstreamer
 libreoffice-base-core
 *libreoffice-calc
 *libreoffice-core
 *libreoffice-draw
 libreoffice-gnome
 libreoffice-gtk
 libreoffice-help-en-gb
 libreoffice-help-en-us
 *libreoffice-impress
 *libreoffice-math
 libreoffice-ogltrans
 libreoffice-pdfimport
 libreoffice-presentation-minimizer
 *libreoffice-writer
 *libslv2-9
 *libsmbclient
 *libtotem-plparser18
 *libwind0-heimdal
 *mate-control-center
 mate-desktop-environment-core
 *mpv
 *mythes-en-us
 *network-manager-gnome
 python-gconf
 *python-ldb
 python-samba
 python-smbc
 python3-pycurl
 python3-software-properties
 *samba
 samba-common-bin
 *samba-dsdb-modules
 *samba-libs
 samba-vfs-modules
 *seahorse
 smbclient
 *software-center
 *software-properties-common
 software-properties-gtk
 *steam-launcher
 *system-config-printer-common
 *system-config-printer-gnome
 *virtualbox-5.0
 *whoopsie
 *winbind

```

Some were marked amd64, I don't know if that matters for reinstallation.
There are also those messages at the end of the log, concerning some other files, I don't know what it means:

```

Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for menu (2.1.46ubuntu1) ...
Processing triggers for libc-bin (2.19-0ubuntu6.6) ...
Processing triggers for libglib2.0-0:i386 (2.40.2-0ubuntu1) ...
Processing triggers for libglib2.0-0:amd64 (2.40.2-0ubuntu1) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Processing triggers for shared-mime-info (1.2-0ubuntu3) ...
Processing triggers for libreoffice-common (1:4.2.8-0ubuntu3) ...

```

I guess I will have to configure the desktop settings and what not all over again. That's so depressing..

---

### Post by yoshii on 2016-01-01
Sorry to hear of your loss.  
the correct syntax would have just been "sudo apt-get remove wine" or maybe 'purge' instead of 'remove' if you absolutely needed to clear out everything.  

If I knew of another way to reinstall the stuff instead of manually, I'd tell ya.  But I don't know that much about scripting.

---

### Post by White_Wind on 2016-01-02
Thank you very much for all your answers. I've decided to try to reinstall manually the removed packages and see what can be restored. Then I will back up the most I can (mostly configurations and personal files), and nuke everything and fresh install MATE 15.10 haha

It's a while now I've had in mind to rethink my drives configuration and my two OSes, and now appears to be the perfect time. One year ago when I build this PC, my first real one, I thought Windows would be my main OS and I had set a RAID 0 array of two SSDs with Windows installed on it, and my MATE has been on a HDD.
But I've been absolutely satisfied with Ubuntu MATE, I'm really liking it a lot, I'm never in Windows, and now there's no doubt that Linux will be and remain my main OS. Thus that's a RAID to be broken and a great distro to sit in a more appropriate place.

Going the Ubuntu route also got me aware of the benefits of free open source software and that trying to evade the giants of the internet can only be a good thing.

---

