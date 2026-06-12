---
title: "Swiftfox Library Problems!"
date: 2009-07-08
forum: x86 64-bit Users
---

### Post by hanbin973 on 2009-07-08
I was trying to use swiftweasel's latest build (3.5RC3 )but it was very~ ( slower then the normal FF3.5) so I tried to use swiftfox. 

Swiftfox was almost 2 times faster then the normal FF 3.5! 

So I tried to stay on Swiftfox but it had problems with the plugins.

I found out that it had problems with the Libraires 32,64 bit problems. the code is
```
Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64
LoadPlugin: failed to initialize shared library /var/lib/flashplugin-installer/npwrapper.libflashplayer.so [/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/xulrunner-addons/plugins/libnullplugin.so [/usr/lib/xulrunner-addons/plugins/libnullplugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/xulrunner-addons/plugins/libunixprintplugin.so [/usr/lib/xulrunner-addons/plugins/libunixprintplugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/IcedTeaPlugin.so [/usr/lib/jvm/java-6-openjdk/jre/lib/amd64/IcedTeaPlugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/xulrunner-addons/plugins/librhythmbox-itms-detection-plugin.so [/usr/lib/xulrunner-addons/plugins/librhythmbox-itms-detection-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/xine-plugin/xineplugin.so [/usr/lib/xine-plugin/xineplugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /var/lib/flashplugin-installer/npwrapper.libflashplayer.so [/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/xulrunner-addons/plugins/libnullplugin.so [/usr/lib/xulrunner-addons/plugins/libnullplugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/xulrunner-addons/plugins/libunixprintplugin.so [/usr/lib/xulrunner-addons/plugins/libunixprintplugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/IcedTeaPlugin.so [/usr/lib/jvm/java-6-openjdk/jre/lib/amd64/IcedTeaPlugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/xulrunner-addons/plugins/librhythmbox-itms-detection-plugin.so [/usr/lib/xulrunner-addons/plugins/librhythmbox-itms-detection-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/xine-plugin/xineplugin.so [/usr/lib/xine-plugin/xineplugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /var/lib/flashplugin-installer/npwrapper.libflashplayer.so [/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so [/usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/libnullplugin.so [/usr/lib/mozilla/plugins/libnullplugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/libunixprintplugin.so [/usr/lib/mozilla/plugins/libunixprintplugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/IcedTeaPlugin.so [/usr/lib/jvm/java-6-openjdk/jre/lib/amd64/IcedTeaPlugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/librhythmbox-itms-detection-plugin.so [/usr/lib/mozilla/plugins/librhythmbox-itms-detection-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/xine-plugin/xineplugin.so [/usr/lib/xine-plugin/xineplugin.so: wrong ELF class: ELFCLASS64]

```

like this. 
I had problems when 32bit programs needed 32bit library, but what kind of situation is this?

A 64 bit program that needs 32bit libraries??

 Ah....

Any one can help? I dont watnt to use swiftweasel anymore.

---

### Post by Yellow Pasque on 2009-07-09
Apparently, you installed a 32-bit swiftfox.
Uninstall that one and try again: [http://www.getswiftfox.com/builds/debian/dists/unstable/non-free/binary-amd64/swiftfox_3.5rc3-1_athlon64.deb](http://www.getswiftfox.com/builds/debian/dists/unstable/non-free/binary-amd64/swiftfox_3.5rc3-1_athlon64.deb)

---

### Post by hanbin973 on 2009-07-17
I installed the one that ends with swiftfox-athlon64..

There was a notice in the swiftfox homepage, It is a 32 bit binary encluding amd64 and blah~~ 

I want to solve these ..

Any one know to build a optimized firefox like swiftfox?

Swiftfox can open the source becasue of the license problems..

---

