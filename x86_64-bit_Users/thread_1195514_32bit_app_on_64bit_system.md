---
title: "32bit app on 64bit system"
date: 2009-06-23
forum: x86 64-bit Users
---

### Post by darkshadow on 2009-06-23
I have a specialty app I am trying to run, I have no source code and their is no 64bit version yet. I have already manually installed any 32bit libraries into /usr/lib32 that show up when running "ldd rsgui" but when I run it the terminal outputs more errors from libraries that don't get redirected to 32bit versions. How can I fix this?


/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so
/usr/lib/gio/modules/libgioremote-volume-monitor.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgioremote-volume-monitor.so
/usr/lib/gio/modules/libgiogconf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiogconf.so

---

### Post by jespdj on 2009-06-24
Have a look at the [getlibs script](http://ubuntuforums.org/showthread.php?t=474790) which can help you to automatically find and install 32-bit libraries for 32-bit software on a 64-bit system.

---

### Post by darkshadow on 2009-06-24
Thanks for that script, it helped me find the files but since the dependencies I need are not the same ones that you see linked when viewing the output of "ldd" Ubuntu does not redirect anything and it still searches in the 64 bit directory.

In the end I came up with a workaround that should not cause many problems as this program will not be used that much (every few months) I start it with this script



sudo rm /usr/lib/gio/modules
sudo ln -s /usr/lib/gio/modules.32 /usr/lib/gio/modules
./rsgui
sudo rm /usr/lib/gio/modules
sudo ln -s /usr/lib/gio/modules.64 /usr/lib/gio/modules

---

