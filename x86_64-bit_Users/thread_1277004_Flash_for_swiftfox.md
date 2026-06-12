---
title: "Flash for swiftfox"
date: 2009-09-27
forum: x86 64-bit Users
---

### Post by noname580 on 2009-09-27
So i tried to install the 64 bit flash player for ubuntu via the script provided in the tutorial.  when i open swiftfox,which i downloaded via repository in synaptic, in terminal i get this

```

Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64
LoadPlugin: failed to initialize shared library /home/noname580/.mozilla/plugins/libflashplayer.so [/home/noname580/.mozilla/plugins/libflashplayer.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/libvlcplugin.so [/usr/lib/mozilla/plugins/libvlcplugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/xulrunner-addons/plugins/libnullplugin.so [/usr/lib/xulrunner-addons/plugins/libnullplugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/xulrunner-addons/plugins/libunixprintplugin.so [/usr/lib/xulrunner-addons/plugins/libunixprintplugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/jvm/java-6-sun-1.6.0.16/jre/lib/amd64/libnpjp2.so [/usr/lib/jvm/java-6-sun-1.6.0.16/jre/lib/amd64/libnpjp2.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/jvm/jre1.6.0_12/lib/amd64/libnpjp2.so [/usr/lib/jvm/jre1.6.0_12/lib/amd64/libnpjp2.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/libvlcplugin.so [/usr/lib/mozilla/plugins/libvlcplugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/jvm/java-6-sun-1.6.0.16/jre/lib/amd64/libnpjp2.so [/usr/lib/jvm/java-6-sun-1.6.0.16/jre/lib/amd64/libnpjp2.so: wrong ELF class: ELFCLASS64]

```

yet when i run firefox-3.5 via the terminal it open just fine. My slight guess on why firefox works it possibly its a 32 bit version. Would be nice if i could get swiftfox working

any suggestion on how to fix this or the reason behind it at least. Thanks for your time

---

### Post by marcoslai on 2009-09-27
Best way to install Swiftfox is through ubuntuzilla python script,see here [http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page).
After download the deb file,install it,then type 'ubuntuzilla.py' in console,it'll install the Swiftfox without problem.
Flash will work nice but u have to download 32bit adobe flash player.tar.gz,extract it,get the libflashplayer.so move it into usr/lib/mozilla/plugin,and change its permission to: Owner : 'your username',Access: Read & Write. ( Remember to remove 64bit libflashplayer.so that u installed for yr 64bit Firefox).

---

