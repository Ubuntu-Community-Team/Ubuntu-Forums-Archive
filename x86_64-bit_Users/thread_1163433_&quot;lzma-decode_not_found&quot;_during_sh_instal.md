---
title: "&quot;lzma-decode: not found&quot; during sh install of lexmark X2600 driver"
date: 2009-05-18
forum: x86 64-bit Users
---

### Post by mdgill on 2009-05-18
I have 64-bit Jaunty Jackalope triple-booting on a MacBook 4,1.  I have downloaded the DEB, RPM, and TAR packages for my Lexmark X2600.  All files end in an SH extension.  I can't get past the SH extension.

---

michael@michael-laptop:~/Desktop$ sudo sh lexmark-inkjet-08-driver-1.0-1.i386.rpm.sh
Verifying archive integrity... All good.
Uncompressing nixstaller...............................................................
Collecting info for this system...
Operating system: linux
CPU Arch: x86_64
Warning: No installer for "x86_64" found, defaulting to x86...
./startupinstaller.sh: 169: bin/linux/x86/libc.so.6/lzma-decode: not found
./startupinstaller.sh: 169: bin/linux/x86/libc.so.6/lzma-decode: not found
./startupinstaller.sh: 169: bin/linux/x86/libc.so.6/lzma-decode: not found
./startupinstaller.sh: 169: bin/linux/x86/libc.so.6/lzma-decode: not found
./startupinstaller.sh: 169: bin/linux/x86/libc.so.6/lzma-decode: not found
./startupinstaller.sh: 169: bin/linux/x86/libc.so.6/lzma-decode: not found
./startupinstaller.sh: 169: bin/linux/x86/libc.so.6/lzma-decode: not found
./startupinstaller.sh: 169: bin/linux/x86/libc.so.6/lzma-decode: not found
./startupinstaller.sh: 169: bin/linux/x86/libc.so.6/lzma-decode: not found
./startupinstaller.sh: 169: bin/linux/x86/libc.so.6/lzma-decode: not found
./startupinstaller.sh: 169: bin/linux/x86/libc.so.6/lzma-decode: not found
./startupinstaller.sh: 169: bin/linux/x86/libc.so.6/lzma-decode: not found
Error: Couldn't find any suitable frontend for your system
michael@michael-laptop:~/Desktop$ sudo apt-get lzma-decode
E: Invalid operation lzma-decode
michael@michael-laptop:~/Desktop$

---

Any pointers?

---

### Post by Fir3chi3f on 2009-05-19
It looks like you just need some additional 32bit libraries or you could try to find a 64bit version of this program.

I'll post back if I can find what that package is called.

edit: try running this in the terminal:
```
sudo apt-get install libc6-i386
```

---

### Post by mdgill on 2009-05-25
libc6-i386 appears to already be installed in Synaptic.

---

### Post by mdgill on 2009-05-25
Here's what I get with the debian package:

-

michael@michael-laptop:~/Desktop$ sudo sh lexmark-inkjet-08-driver-1.0-1.i386.deb.sh
[sudo] password for michael: 
Verifying archive integrity... All good.
Uncompressing nixstaller...............................................................
Collecting info for this system...
Operating system: linux
CPU Arch: x86_64
Warning: No installer for "x86_64" found, defaulting to x86...
Gtk-Message: Failed to load module "gail": /usr/lib/gtk-2.0/modules/libgail.so: wrong ELF class: ELFCLASS64
Gtk-Message: Failed to load module "atk-bridge": /usr/lib/gtk-2.0/modules/libatk-bridge.so: wrong ELF class: ELFCLASS64
TRACKING IDENT = 14052009
cpu speed = 800 MHz
ram size = 953.953125 MB
hd avail = 7954 MB
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so
/usr/lib/gio/modules/libgioremote-volume-monitor.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgioremote-volume-monitor.so
/usr/lib/gio/modules/libgiogconf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiogconf.so

-

I have all those libraries marked as installed in Synaptic.

---

### Post by oldos2er on 2009-05-25
"wrong ELF class: ELFCLASS64" means the installer expects 32-bit versions of those libraries. You could try using getlibs (see [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)).

---

### Post by mdgill on 2009-05-26
getlibs worked for some other deb packages I was having trouble with (e.g., Avast!AV) but not with this sh file.

---

### Post by mdgill on 2009-07-17
Bump

I tried updating libgiofam via synaptic, but that just added to the list of libraries that aren't compatible with 64-bit.

$ sudo sh lexmark-inkjet-08-driver-1.0-1.i386.deb.sh
Verifying archive integrity... All good.
Uncompressing nixstaller...............................................................
Collecting info for this system...
Operating system: linux
CPU Arch: x86_64
Warning: No installer for "x86_64" found, defaulting to x86...
TRACKING IDENT = 14052009
cpu speed = 800 MHz
ram size = 953.98828125 MB
hd avail = 3761 MB
/usr/lib/gio/modules/libgiofam.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiofam.so
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so
/usr/lib/gio/modules/libgioremote-volume-monitor.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgioremote-volume-monitor.so
/usr/lib/gio/modules/libgiogconf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiogconf.so

getlibs doesn't help.  Is there any way to force i386 libraries?

---

### Post by mdgill on 2009-07-17
And all I really need to do is print.  Isn't there some kind of generic printer driver?  I've tried a few in the CUPS list with no luck.

---

