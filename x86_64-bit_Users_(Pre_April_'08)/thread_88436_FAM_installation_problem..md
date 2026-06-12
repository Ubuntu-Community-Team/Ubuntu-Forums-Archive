---
title: "FAM installation problem."
date: 2005-11-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by Shutdownrunner on 2005-11-10
I have a problem, because when I want to install fam apt-get wants to remove almost all my gnome packages. 
```
apt-get install fam
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  cpp-4.0 g++-4.0 gcc-4.0 gcc-4.0-base libcamel1.2-6 libdbus-1-1 libdbus-1-dev
  libdbus-glib-1-1 libdbus-glib-1-dev libdbus-qt-1-1c2 libedataserver1.2-4
  libegroupwise1.2-8 libgcc1 libgcj6 libstdc++6 libstdc++6-4.0-dev portmap
Suggested packages:
  gcc-4.0-locales gcc-4.0-doc lib32stdc++6 libc6-dev-i386 ia32-libs-dev
  libstdc++6-4.0-doc stl-manual
Recommended packages:
  libmudflap0-dev libgcj6-common
The following packages will be REMOVED:
  bluefish bug-buddy contact-lookup-applet eog evolution evolution-data-server
  evolution-exchange evolution-webcal file-roller gamin gcalctool gconf-editor
  gdm gedit gnome-about gnome-app-install gnome-applets gnome-applets-data
  gnome-btdownload gnome-commander gnome-control-center gnome-cups-manager
  gnome-games gnome-gv gnome-media gnome-menus gnome-netstatus-applet
  gnome-panel gnome-pilot gnome-pilot-conduits gnome-session gnome-spell
  gnome-system-monitor gnome-system-tools gnome-terminal gnome-utils
  gnome-volume-manager gstreamer0.8-gnomevfs gthumb gtkhtml3.6 gtkhtml3.8
  gucharmap hal-device-manager hwdb-client k3b k3blibs kcontrol kdebase-bin
  kdelibs-bin kdelibs4c2 libbonoboui2-0 libebook1.2-5 libecal1.2-2
  libecal1.2-3 libedata-book1.2-2 libedata-cal1.2-1 libedataserverui1.2-6
  libeel2-2 libegroupwise1.2-5 libexchange-storage1.2-0 libgal2.4-0
  libgal2.4-common libgamin0 libgnome-desktop-2 libgnome-menu0 libgnome-menu2
  libgnome2-0 libgnome2-perl libgnome2-vfs-perl libgnomecupsui1.0-1
  libgnomeui-0 libgnomevfs2-0 libgnomevfs2-common libgtkhtml3.6-18
  libgtkhtml3.8-15 libgucharmap4 liblpint-bonobo0 libnautilus-extension1
  libpanel-applet2-0 libtotem-plparser0 libwvstreams3-base
  libwvstreams4.0c2-extras nautilus nautilus-cd-burner nautilus-sendto
  python-gmenu python-gnome2 python-gnome2-extras python2.4-gnome2
  python2.4-gnome2-extras rhythmbox sound-juicer totem totem-xine tsclient
  vino wvdial yelp

```

Was any of you in similiar situation? Is it like this that I have to install fam and let apt-get remove gnome packages and then I will be able to install them again?

---

### Post by doclivingston on 2005-11-10
That's because all the gnome programs use **gamin**, which is a replacement for FAM. You can't have both installed at once.

---

### Post by Shutdownrunner on 2005-11-12
[QUOTE=doclivingston]That's because all the gnome programs use **gamin**, which is a replacement for FAM. You can't have both installed at once.[/QUOTE]
Thanks. That helped.
I wonder why ./configure didn't say gamin or fam.

---

