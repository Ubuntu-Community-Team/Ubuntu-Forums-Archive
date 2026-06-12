---
title: "Compilng Mozilla Lighting..."
date: 2006-08-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by LinuxConvertJune2006 on 2006-08-08
I want to use Mozilla Lightning, caledar plugin for Thunderbird, however they don't have 64bit linux versoins available for download. They do, of course, make source code and build instructions available. I followed the instructionds here:
[http://developer.mozilla.org/en/docs/Build_Documentation#requirements](http://developer.mozilla.org/en/docs/Build_Documentation#requirements)
And I thought I had everytihng but the GTK+ widget toolkit (I'm not sure what to search for in Synaptic).

When I follow the instructions here, to checkout and build:
[http://www.mozilla.org/projects/calendar/lightning/build.html](http://www.mozilla.org/projects/calendar/lightning/build.html)

I get this error , and I can't execute "make":
```

checking for gtk+-2.0 >= 1.3.7 gdk-x11-2.0 glib-2.0 gobject-2.0... Package gtk+-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gtk+-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gtk+-2.0' found Package gdk-x11-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gdk-x11-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gdk-x11-2.0' found Package glib-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `glib-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'glib-2.0' found Package gobject-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gobject-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gobject-2.0' found
configure: error: Library requirements (gtk+-2.0 >= 1.3.7 gdk-x11-2.0 glib-2.0 gobject-2.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.


```

Anyone have any ideas on what I need to add / install ? I searched Google but didn't find anything.

---

### Post by codejunkie on 2006-08-08
> **LinuxConvertJune2006 said:**
> I want to use Mozilla Lightning, caledar plugin for Thunderbird, however they don't have 64bit linux versoins available for download. They do, of course, make source code and build instructions available. I followed the instructionds here:
[http://developer.mozilla.org/en/docs/Build_Documentation#requirements](http://developer.mozilla.org/en/docs/Build_Documentation#requirements)
And I thought I had everytihng but the GTK+ widget toolkit (I'm not sure what to search for in Synaptic).

When I follow the instructions here, to checkout and build:
[http://www.mozilla.org/projects/calendar/lightning/build.html](http://www.mozilla.org/projects/calendar/lightning/build.html)

I get this error , and I can't execute "make":
```

checking for gtk+-2.0 >= 1.3.7 gdk-x11-2.0 glib-2.0 gobject-2.0... Package gtk+-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gtk+-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gtk+-2.0' found Package gdk-x11-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gdk-x11-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gdk-x11-2.0' found Package glib-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `glib-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'glib-2.0' found Package gobject-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gobject-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gobject-2.0' found
configure: error: Library requirements (gtk+-2.0 >= 1.3.7 gdk-x11-2.0 glib-2.0 gobject-2.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.


```

Anyone have any ideas on what I need to add / install ? I searched Google but didn't find anything.

install the common development packages by copying and pasting the commands below into terminal and try it again 
```
sudo apt-get install build-essential linux-headers-`uname -r` gcc-3.4 libgtk2.0-dev
```
then ```
sudo apt-get build-dep mozilla-thunderbird
```

---

### Post by RAOF on 2006-08-09
Incidentally, you really won't need the kernel headers (the linux-headers-`uname -r` bit).

---

### Post by t.n. on 2006-08-09
Note that compiling the Lightning plugin will probably fail if you try the 1.5 version. At least I always got strange linker errors.
The current subversion trunk works though, but you also have to use Thunderbird from the trunk then.

---

### Post by LinuxConvertJune2006 on 2006-08-09
Thanks all! OK I got past that dependency, ran into another (libIDL) which I installed the libidl-dev package to compensate for, however....

```

checking for correct temporary object destruction order... yes
checking for correct overload resolution with const and templates... no
checking for libIDL-2.0 >= 0.8.0 glib-2.0 gobject-2.0... yes
checking LIBIDL_CFLAGS... -I/usr/include/libIDL-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include
checking LIBIDL_LIBS... -lIDL-2 -lgobject-2.0 -lglib-2.0
checking for glib-2.0 >= 1.3.7 gobject-2.0... yes
checking GLIB_CFLAGS... -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include
checking GLIB_LIBS... -lgobject-2.0 -lglib-2.0
checking for stdint.h... yes
checking for inttypes.h... yes
checking for sys/int_types.h... no
configure: error: Could not compile basic X program.

```

Is what I get now, I'm not sure which dependency to install fir that ,doesn't list library name or anything. A quick Google turned up nada...

Also to clarify, I will need to checkout a build a different brach of Thunberdird, or Lightning, or both ?

---

### Post by t.n. on 2006-08-09
Hm, if you have something like libgtk2.0-dev installed all required packages should be there implicitly.

What did you specify as configuration (see [http://developer.mozilla.org/en/docs/Configuring_Build_Options)?](http://developer.mozilla.org/en/docs/Configuring_Build_Options)?) I used ac_add_options --enable-default-toolkit=gtk2 and ac_add_options --enable-xft.

Concerning the trunk, I choosed the normal mozilla trunk, checkout everything and build lightning as specified somewhere on the lightning pages. This worked.

---

### Post by Nickolay on 2006-09-23
You also need libxt-dev, as mentioned in the docs: [http://developer.mozilla.org/en/docs/Linux_Build_Prerequisites](http://developer.mozilla.org/en/docs/Linux_Build_Prerequisites)

---

### Post by fabertawe on 2006-09-23
Would it be possible for someone who's already built this to make it available for others please?

Thanks ... Paul

---

