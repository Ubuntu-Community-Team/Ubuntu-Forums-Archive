---
title: "Vmware Player+ Existing windows XP = Frustrated"
date: 2007-04-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by krazycure on 2007-04-25
Install 64bit player via automatix. Followed the guide that comes up when you google "existing ubuntu vmware" [http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html]("http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html"), but at the final step, running the vmx file in the player, I get this in the terminal:


```
root@krazycure-desktop:/home/krazycure# sudo vmplayer '/home/krazycure/windows.vmx' 
/usr/lib/vmware-player/bin/vmplayer: /usr/lib/vmware-player/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib32/libcairo.so.2)

(vmplayer:16781): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.

(process:16794): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
/usr/share/themes/Mist/gtk-2.0/gtkrc:6: error: unexpected character `@', expected string constant
Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory
Unable to load image-loading module: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /build/mts/release/bora-29634/bora/build/release/player/vmui/../libdir/libconf/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory

```

---

### Post by jkwarras on 2007-07-15
I get exactly the same problem...

---

### Post by kilroo on 2007-08-03
Same problem here except without the locale warning. Anyone figured it out?

---

### Post by ashvala on 2007-08-04
probably you should just run Windows & remove VMware

---

