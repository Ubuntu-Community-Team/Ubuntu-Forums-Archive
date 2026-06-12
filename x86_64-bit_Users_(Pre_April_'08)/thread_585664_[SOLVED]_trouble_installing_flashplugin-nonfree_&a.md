---
title: "[SOLVED] trouble installing flashplugin-nonfree &amp;gt;&amp;gt; error code (1)"
date: 2007-10-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by RavanH on 2007-10-21
Hi,

Since a few days, flash on my Swiftweasel 64bit doesn't work anymore. It used to do fine with the flashplugin-nonfree installed via Synaptic. When I entered about: plugins in the address bar, it showed the Flash plugin listed.

However, when I try reïnstalling the package in Synaptic, I get an error. It tried to purge the package and reïnstall but that did not do the trick (only removed the plugin from about: plugins). Also puged nspluginwrapper and reïnstalled it, but still the same error...

This is what shows when doing it via apt-get in terminal (most in dutch language, but error in english):

```
Instellen van flashplugin-nonfree (9.0.48.0.2+really0ubuntu12) ...
Installing from local file /var/cache/flashplugin-nonfree/install_flash_player_9_linux.tar.gz
Flash Plugin installed.
/usr/lib/nspluginwrapper/i386/linux/npviewer.bin: error while loading shared libraries: libglitz.so.1: cannot open shared object file: No such file or directory
nspluginwrapper: no appropriate viewer found for /usr/lib/flashplugin-nonfree/libflashplayer.so
dpkg: fout bij afhandelen van flashplugin-nonfree (--configure):
 subproces post-installation script gaf een foutwaarde 1 terug
Fouten gevonden tijdens behandelen van:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Anybody any idea how to fix this?

---

### Post by RavanH on 2007-10-24
Thanks to chris (go_beep_yourself) this is solved... see details on [http://ubuntuforums.org/showthread.php?p=3620359](http://ubuntuforums.org/showthread.php?p=3620359)

---

