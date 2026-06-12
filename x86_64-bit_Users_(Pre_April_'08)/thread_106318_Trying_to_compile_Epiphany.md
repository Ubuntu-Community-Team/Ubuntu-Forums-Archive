---
title: "Trying to compile Epiphany"
date: 2005-12-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by Tilmitt on 2005-12-20
Heya guys I get this error when trying to compile Epiphant:

[I]checking for pkg-config... /usr/bin/pkg-config
***** WARNING: Building without libstartup-notification
checking pkg-config is at least version 0.9.0... yes
checking for EPIPHANY_DEPENDENCY... configure: error: Package requirements (  glib-2.0 >= 2.8.0                gtk+-2.0 >= 2.8.3               libxml-2.0 >= 2.6.12            libxslt >= 1.1.7                libgnomeui-2.0 >= 2.6.0  libglade-2.0 >= 2.3.1            bonobo-activation-2.0                   ORBit-2.0               gnome-vfs-2.0 >= 2.9.2                  gnome-vfs-module-2.0  gconf-2.0                gnome-desktop-2.0 >= 2.9.91  libgnomeprint-2.2 >= 2.4.0               libgnomeprintui-2.2 >= 2.4.0  ) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively you may set the EPIPHANY_DEPENDENCY_CFLAGS and EPIPHANY_DEPENDENCY_LIBS environment variables
to avoid the need to call pkg-config.  See the pkg-config man page for
more details.
tilmitt@Ekiseikakumei:~/Desktop/epiphany-1.8.3$[/I]


It gave me some dependency errors earlier on but I managed to fix those and get this far by installing stuff (which themselves had dependency errors but I managed to get them all done).  Anyway does anyone have any idea how to fix this?

---

### Post by Mr. Picklesworth on 2007-03-04
I'm getting the same error trying to configure the latest Epiphany, and I swear none of those are in the repositories :(
I guess I'll have to go hunting for them. It seems kind of odd that these would all be unavailable (or differently named), though, so perhaps something is wrong elsewhere?

(This isn't a 64-bit problem, by the way; I'm running ancient 32 bit hardware).


Edit:
Looking a bit further down in my search results told me to install gnome-core-dev. That package has nearly everything you'll need to build Gnome apps.

---

