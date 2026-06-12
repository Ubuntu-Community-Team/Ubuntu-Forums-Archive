---
title: "Problems after adding line to apt sources"
date: 2007-09-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by vickistan on 2007-09-20
Started with a dapper system, but I wanted an application that required me to add another entry to the apt sources file. I added the following line to /etc/apt/sources:

deb [http://http.us.debian.org/debian](http://http.us.debian.org/debian) sid main

I was able to add the wireshark package, but then I started getting errors about locale and having trouble adding other packages. I was advised to run apt-get -f install to clear some broken packages. Doing so led to this:

sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  acpi-support dbus dbus-x11 gcc-4.2-base gdm gnome-keyring
  gtk2-engines-pixbuf gtk2-engines-ubuntulooks lib32asound2 libart-2.0-2
  libasound2 libatk1.0-0 libavahi-client3 libavahi-glib1 libbonobo2-0
  libbonobo2-common libbonoboui2-0 libbonoboui2-common libcairo2 libdatrie0
  libdbus-1-3 libdbus-glib-1-2 libfreetype6-dev libgcc1 libglade2-0
  libglib2.0-0 libglib2.0-data libgnome-keyring0 libgnome2-0 libgnome2-common
  libgnomeui-0 libgnomeui-common libgnomevfs2-0 libgnomevfs2-common
  libgnomevfs2-extra libgsf-1-114 libgsf-1-common libgtk2.0-0 libgtk2.0-common
  libhal-storage1 libhal1 libjasper1 liblua50 liblualib50 libnotify1 liborbit2
  libpango1.0-0 libpango1.0-common librsvg2-2 librsvg2-common libscim8c2a
  libstdc++6 libthai-data libthai0 libwmf0.2-7 libxfixes3 libxrandr2
  radeontool scim-gtk2-immodule scim-modules-socket update-notifier x11-apps
  x11-common x11-session-utils x11-utils x11-xfs-utils x11-xkb-utils
  x11-xserver-utils xaw3dg xaw3dg-dev xinit xutils xutils-dev
Suggested packages:
  hibernate apmd gtk-engines-pixmap libasound2-plugins desktop-base
  libjasper-runtime ttf-thryomanes librsvg2-bin
Recommended packages:
  gdm-themes xserver-xephyr xnest libatk1.0-data fam gnome-mount
The following packages will be REMOVED:
  appres atlantik blinken dbus-1-utils editres iceauth kcontrol kdebase-bin
  kdebase-kio-plugins kdelibs-bin kdelibs4c2a kdesktop kfind kicker
  kmplayer-base kmplayer-konq-plugins konqueror libkdegames1 libkonq4 listres
  oclock sessreg smproxy viewres x11perf xbiff xcalc xclipboard xclock
  xconsole xcursorgen xditview xdpyinfo xdriinfo xev xeyes xfd xfontsel xgamma
  xhost xkbutils xkill xload xlogo xlsatoms xlsclients xlsfonts xmag xman
  xmessage xmodmap xmore xprop xrandr xrdb xrefresh xrgb xset xsetmode
  xsetpointer xsetroot xsm xstdcmap xtrap xvidtune xvinfo xwd xwininfo xwud
The following NEW packages will be installed:
  dbus-x11 gcc-4.2-base libdatrie0 libdbus-1-3 libgsf-1-114 libjasper1
  liblua50 liblualib50 libthai-data libthai0 radeontool x11-apps
  x11-session-utils x11-utils x11-xfs-utils x11-xkb-utils x11-xserver-utils
  xutils xutils-dev
The following packages will be upgraded:
  acpi-support dbus gdm gnome-keyring gtk2-engines-pixbuf
  gtk2-engines-ubuntulooks lib32asound2 libart-2.0-2 libasound2 libatk1.0-0
  libavahi-client3 libavahi-glib1 libbonobo2-0 libbonobo2-common
  libbonoboui2-0 libbonoboui2-common libcairo2 libdbus-glib-1-2
  libfreetype6-dev libgcc1 libglade2-0 libglib2.0-0 libglib2.0-data
  libgnome-keyring0 libgnome2-0 libgnome2-common libgnomeui-0
  libgnomeui-common libgnomevfs2-0 libgnomevfs2-common libgnomevfs2-extra
  libgsf-1-common libgtk2.0-0 libgtk2.0-common libhal-storage1 libhal1
  libnotify1 liborbit2 libpango1.0-0 libpango1.0-common librsvg2-2
  librsvg2-common libscim8c2a libstdc++6 libwmf0.2-7 libxfixes3 libxrandr2
  scim-gtk2-immodule scim-modules-socket update-notifier x11-common xaw3dg
  xaw3dg-dev xinit
54 upgraded, 19 newly installed, 69 to remove and 763 not upgraded.
1 not fully installed or removed.
Need to get 0B/27.5MB of archives.
After unpacking 71.1MB disk space will be freed.
Do you want to continue [Y/n]?
WARNING: The following packages cannot be authenticated!
  x11-common x11-apps x11-session-utils x11-utils x11-xfs-utils x11-xkb-utils
  xinit libart-2.0-2 libglib2.0-data libglib2.0-0 libatk1.0-0 libcairo2
  libdbus-1-3 libdbus-glib-1-2 liborbit2 libbonobo2-0 libbonobo2-common
  libavahi-client3 libavahi-glib1 libhal1 libhal-storage1 libpango1.0-common
  libdatrie0 libthai-data libthai0 libpango1.0-0 libxfixes3 libxrandr2
  libgnome-keyring0 gnome-keyring libnotify1 update-notifier dbus dbus-x11
  libgnomevfs2-0 libgnomevfs2-extra libgnomevfs2-common libgnome2-0
  libgnome2-common libbonoboui2-0 libbonoboui2-common libgnomeui-0
  libgnomeui-common gtk2-engines-pixbuf gtk2-engines-ubuntulooks
  libgsf-1-common libgsf-1-114 librsvg2-common librsvg2-2 gcc-4.2-base libgcc1
  libstdc++6 libscim8c2a scim-gtk2-immodule scim-modules-socket libwmf0.2-7
  libgtk2.0-common libgtk2.0-0 libglade2-0 gdm radeontool acpi-support
  x11-xserver-utils xutils-dev lib32asound2 libasound2 libfreetype6-dev
  libjasper1 liblua50 liblualib50 xutils xaw3dg-dev xaw3dg
Install these packages without verification [y/N]? y
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en",
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
Can't exec "locale": No such file or directory at /usr/share/perl5/Debconf/Encoding.pm line 16.
Use of uninitialized value in scalar chomp at /usr/share/perl5/Debconf/Encoding.pm line 17.
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 107011 files and directories currently installed.)
Preparing to replace x11-common 7.0.0-0ubuntu45 (using .../x11-common_1%3a7.3+2_amd64.deb) ...
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en",
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
Can't exec "locale": No such file or directory at /usr/share/perl5/Debconf/Encoding.pm line 16.
Use of uninitialized value in scalar chomp at /usr/share/perl5/Debconf/Encoding.pm line 17.
Unpacking replacement x11-common ...
dpkg: error processing /var/cache/apt/archives/x11-common_1%3a7.3+2_amd64.deb (--unpack):
 trying to overwrite `/usr/share/man/man5/Xsession.5.gz', which is also in package xinit
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en",
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
Can't exec "locale": No such file or directory at /usr/share/perl5/Debconf/Encoding.pm line 16.
Use of uninitialized value in scalar chomp at /usr/share/perl5/Debconf/Encoding.pm line 17.
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en",
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
Errors were encountered while processing:
 /var/cache/apt/archives/x11-common_1%3a7.3+2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Worse yet, I can't run OpenOffice anymore. It appears to initiate and then dies before coming up. I am at the point where I am about ready to reinstall. I've tried to research this, but I can't figure out how to fix it. Can anyone advise?

Captain Vic

---

### Post by ajgreeny on 2007-09-20
Did you install or update any other packages than you installed it?  If so you may be able to remove that line from your sources.list, apt-get upgrade to reload the repos, and then uninstall those other new ones and finally reinstall them back to versions you had before.  This may just show the dangers of using untried repos in a ubuntu system.  OK, debian is not exactly untried or untested, but I know some packages don't work properly on a ubuntu install.

---

### Post by vickistan on 2007-09-20
I removed the line I added from apt/sources and reran apt-get -f install. I ran apt-get remove wireshark. Things appeared better, but I still can't run open office. It still begins to start and then dies without an error message. I tried removing openoffice.org and reinstalling it, but now I get this:

apt-get install openoffice.org
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  openoffice.org-help menu ooqstart-gnome oooqs-kde cupsys-bsd prelink
  openoffice.org-hyphenation openoffice.org-thesaurus xlibmesa-gl libgl1
  openoffice.org-officebean openclipart-openoffice.org pstoedit imagemagick
  openoffice.org-filter-so52
The following NEW packages will be installed:
  openoffice.org
0 upgraded, 1 newly installed, 0 to remove and 12 not upgraded.
Need to get 1844B of archives.
After unpacking 20.5kB of additional disk space will be used.
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main openoffice.org 2.0.2-2ubuntu12.4-1 [1844B]
Fetched 1844B in 0s (1997B/s)
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "C",
        LC_ALL = "",
        LC_CTYPE = "",
        LANG = "en_US"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
Can't exec "locale": No such file or directory at /usr/share/perl5/Debconf/Encoding.pm line 16.
Use of uninitialized value in scalar chomp at /usr/share/perl5/Debconf/Encoding.pm line 17.
Selecting previously deselected package openoffice.org.
(Reading database ... 105953 files and directories currently installed.)
Unpacking openoffice.org (from .../openoffice.org_2.0.2-2ubuntu12.4-1_amd64.deb) ...
Setting up openoffice.org (2.0.2-2ubuntu12.4-1) ...

Any ideas? I really don't have a reinstall in me right now.

Captain Vic

---

### Post by Cappy on 2007-09-20
Adding a debian repos to your ubuntu is obviously a bad idea.

Run ```
ooffice
``` in the terminal and see if you get an error message.

Dapper doesn't have wireshark - it has ethereal
```
sudo apt-get install ethereal
```
Older version of Wireshark.

If I were you I would just take the opportunity to re-install using an Ubuntu Feisty CD.

I'm not sure how perl got messed up since you don't have a log of it. You could try
```
sudo apt-get --reinstall install perl

```

---

### Post by vickistan on 2007-09-20
sudo ooffice yields this:

 sudo ooffice
Password:
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en",
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
no suitable windowing system found, exiting.

** (process:22839): WARNING **: Unknown error forking main binary / abnormal early exit ...

When I try to the command to reinstall perl, I get this:

sudo apt-get --reinstall install perl
Reading package lists... Done
Building dependency tree... Done
Reinstallation of perl is not possible, it cannot be downloaded.
0 upgraded, 0 newly installed, 0 to remove and 12 not upgraded.

Man, I messed this up.

Captain Vic

---

### Post by ajgreeny on 2007-09-21
Why did you run as root and not just as user?  Try **ooffice** without the sudo.

---

### Post by vickistan on 2007-09-21
I did that and got the same perl error and then the same 

no suitable windowing system found, exiting.

** (process:7707): WARNING **: Unknown error forking main binary / abnormal early exit ...

error.

I'm still looking for something that will save me from a reinstall.

Vicki

---

### Post by dcstar on 2007-09-22
> **vickistan said:**
> I did that and got the same perl error and then the same 

no suitable windowing system found, exiting.

** (process:7707): WARNING **: Unknown error forking main binary / abnormal early exit ...

error.

I'm still looking for something that will save me from a reinstall.

Vicki

You will basically have to find what versions have been installed from the Debian repo and downgrade them to the Ubuntu version.

If you have removed the Debian info, then go into Synaptic and look at the "Installed (local or obsolete)" category, then for each package do a "Force Version" back to the correct Ubuntu version.

---

### Post by vickistan on 2007-09-28
Still getting a lot of weird errors, so I guess I'll reinstall this weekend.

Thanks for your help.

Captain Vic

---

### Post by Jouke74 on 2007-09-28
Basically you installed almost a full debian Sid distro over your Ubuntu Dapper. This makes a lot of dependencies fail and hence, a lot of errors. Ubuntu is a lot like Debian, but there are differences (I did the reverse once with same effect). It is time for a fresh install.

---

