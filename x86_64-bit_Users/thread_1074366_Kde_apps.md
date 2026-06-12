---
title: "Kde apps"
date: 2009-02-19
forum: x86 64-bit Users
---

### Post by wfp on 2009-02-19
Just wondering how this happened i installed digikam on my gnome desktop using sudo apt-get install digikam. now i noticed i have kmail, konqueror k3b, and dolphin now. No big thing i can just remove them. Just looked at my source.list everything there looks good.

---

### Post by Yellow Pasque on 2009-02-19
IIRC apt-get pulls 'Recommended' dependencies by default, even though they're not strictly necessary. In the future, you could use apt's --no-install-recommends parameter to only install the minimum package dependencies.

---

### Post by wfp on 2009-02-20
Thanks for your reply. The only thing i have changed was my server source, any way no big deal i just removed them. I will pay more attention to what i install on updates.

---

### Post by stchman on 2009-02-20
> **wfp said:**
> Just wondering how this happened i installed digikam on my gnome desktop using sudo apt-get install digikam. now i noticed i have kmail, konqueror k3b, and dolphin now. No big thing i can just remove them. Just looked at my source.list everything there looks good.

According to the Ubuntu repos kmail, k3b, and dolphin are not dependencies.

FYI, apt-get only installs needed dependencies not recommended or suggested.

[http://packages.ubuntu.com/intrepid/digikam](http://packages.ubuntu.com/intrepid/digikam)

---

### Post by Yellow Pasque on 2009-02-20
> FYI, apt-get only installs needed dependencies not recommended or suggested.
I'm pretty sure it's configured to install 'Recommended' (but not 'Suggests') packages by default. What's confusing is that apt-get uses different meanings for those words. See my example below (from a very fresh install of Ubuntu 8.10)
```
sudo apt-get install digikam
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dolphin exiv2 gnupg-agent graphicsmagick graphicsmagick-imagemagick-compat
  k3b k3b-data kde-icons-oxygen kdebase-bin kdebase-data kdebase-runtime
  kdebase-runtime-bin-kde4 kdebase-runtime-data kdebase-runtime-data-common
  kdelibs-bin kdelibs-data kdelibs4c2a kdelibs5 kdelibs5-data kdepimlibs-data
  kdepimlibs5 kfind khelpcenter4 kipi-plugins kmail konqueror
  konqueror-nsplugins libakonadiprivate1 libarts1c2a libartsc0 libaudio2
  libavahi-qt3-1 libclucene0ldbl libdbus-qt-1-1c2 libexiv2-4 libflac++6
  libgraphicsmagick1 libk3b3 libkdcraw3 libkdepim4 libkexiv2-3 libkipi-common
  libkipi0 libkleo4 libkonq5 libkonq5-templates libkpgp4 libksieve4 liblua50
  liblualib50 libmimelib4 libmpcdec3 libmpg123-0 libmysqlclient15off
  libphonon4 libpq5 libqt3-mt libqt4-dbus libqt4-designer libqt4-network
  libqt4-opengl libqt4-qt3support libqt4-script libqt4-sql libqt4-sql-mysql
  libqt4-svg libqt4-xml libqtcore4 libqtgui4 libraptor1 librasqal0 librdf0
  libsoprano4 libstreamanalyzer0 libstreams0 libstrigiqtdbusclient0 mpg123
  mysql-common phonon phonon-backend-gstreamer pinentry-gtk2 qt4-qtconfig
  raptor-utils redland-utils soprano-daemon
Suggested packages:
  digikam-doc graphicsmagick-dbg k3b-i18n normalize-audio toolame sox
  movixmaker-2 vcdimager kdebase-kio-plugins kcontrol libk3b3-extracodecs
  transcode kdebase perl-suid gallery kipi-plugins-doc kaddressbook procmail
  clamav f-prot-installer akonadi-server libarts1-akode nas libqt3-mt-mysql
  libqt3-mt-odbc libqt3-mt-psql libqt4-dev libjack0 phonon-backend-xine
  phonon-backend-vlc phonon-backend-mplayer pinentry-doc
Recommended packages:
  kdeprint kooka pinentry-qt4 pinentry-qt pinentry-x11
The following NEW packages will be installed:
  digikam dolphin exiv2 gnupg-agent graphicsmagick
  graphicsmagick-imagemagick-compat k3b k3b-data kde-icons-oxygen kdebase-bin
  kdebase-data kdebase-runtime kdebase-runtime-bin-kde4 kdebase-runtime-data
  kdebase-runtime-data-common kdelibs-bin kdelibs-data kdelibs4c2a kdelibs5
  kdelibs5-data kdepimlibs-data kdepimlibs5 kfind khelpcenter4 kipi-plugins
  kmail konqueror konqueror-nsplugins libakonadiprivate1 libarts1c2a libartsc0
  libaudio2 libavahi-qt3-1 libclucene0ldbl libdbus-qt-1-1c2 libexiv2-4
  libflac++6 libgraphicsmagick1 libk3b3 libkdcraw3 libkdepim4 libkexiv2-3
  libkipi-common libkipi0 libkleo4 libkonq5 libkonq5-templates libkpgp4
  libksieve4 liblua50 liblualib50 libmimelib4 libmpcdec3 libmpg123-0
  libmysqlclient15off libphonon4 libpq5 libqt3-mt libqt4-dbus libqt4-designer
  libqt4-network libqt4-opengl libqt4-qt3support libqt4-script libqt4-sql
  libqt4-sql-mysql libqt4-svg libqt4-xml libqtcore4 libqtgui4 libraptor1
  librasqal0 librdf0 libsoprano4 libstreamanalyzer0 libstreams0
  libstrigiqtdbusclient0 mpg123 mysql-common phonon phonon-backend-gstreamer
  pinentry-gtk2 qt4-qtconfig raptor-utils redland-utils soprano-daemon
0 upgraded, 86 newly installed, 0 to remove and 0 not upgraded.
Need to get 111MB of archives.
After this operation, 328MB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.
```

```
sudo apt-get --no-install-recommends install digikam
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  kdelibs-data kdelibs4c2a libarts1c2a libartsc0 libaudio2 libavahi-qt3-1
  libexiv2-4 libkdcraw3 libkexiv2-3 libkipi-common libkipi0 liblua50
  liblualib50 libqt3-mt
Suggested packages:
  digikam-doc perl-suid libarts1-akode nas libqt3-mt-mysql libqt3-mt-odbc
  libqt3-mt-psql
Recommended packages:
  kipi-plugins kdeprint konqueror exiv2
The following NEW packages will be installed:
  digikam kdelibs-data kdelibs4c2a libarts1c2a libartsc0 libaudio2
  libavahi-qt3-1 libexiv2-4 libkdcraw3 libkexiv2-3 libkipi-common libkipi0
  liblua50 liblualib50 libqt3-mt
0 upgraded, 15 newly installed, 0 to remove and 0 not upgraded.
Need to get 34.1MB of archives.
After this operation, 108MB of additional disk space will be used.
Do you want to continue [Y/n]?
```

---

### Post by stchman on 2009-02-20
Funny think is that dolphin is nowhere to be found anywhere on the Ubuntu packages page.  Why so much installed?  The page below list the dependencies, recommendations, and suggestions.

[http://packages.ubuntu.com/intrepid/digikam](http://packages.ubuntu.com/intrepid/digikam)

Now I am confused.

What does K3b have to do with digikam?  If you install K3b does it install digikam?

---

### Post by Yellow Pasque on 2009-02-20
> What does K3b have to do with digikam?
digikam depends on kipi-plugins, which recommends k3b, konqueror, etc. [http://packages.ubuntu.com/intrepid/kipi-plugins](http://packages.ubuntu.com/intrepid/kipi-plugins)

---

### Post by stchman on 2009-02-20
> **Temüjin said:**
> digikam depends on kipi-plugins, which recommends k3b, konqueror, etc. [http://packages.ubuntu.com/intrepid/kipi-plugins](http://packages.ubuntu.com/intrepid/kipi-plugins)

I see, the only KDE apps I use are K3b and K9Copy.  Neither of those have any recommended packages.

I wonder what the consequences of doing the --no-install-recommends switch?

---

### Post by Yellow Pasque on 2009-02-20
> I wonder what the consequences of doing the --no-install-recommends switch?
apt won't install packages listed as 'Recommended'; it's configured to install them by default.

---

### Post by missmoondog on 2009-09-22
almost exactly what i was looking for. all i need to know now is how to remove everything digikam installed so ican get back to a clean xubuntu environment?

thank you

edit:
did some searches and found the code to remove all kde/libs at once. reinstalled k3b and then installed gthumb. no dependencies and actually works. seen that i had subscribed to that exact thread back in 2006 even, [http://ubuntuforums.org/showthread.php?t=223049](http://ubuntuforums.org/showthread.php?t=223049)!!

---

