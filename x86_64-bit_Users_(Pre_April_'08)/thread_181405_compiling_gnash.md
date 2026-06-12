---
title: "compiling gnash"
date: 2006-05-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by eidex on 2006-05-24
hi, i am trying to compile gnash for ppc, i downloaded the CVS and wanted to build the configure script as described in the readme and get a lot of error messages, what went wrong?:

> paul@wolfos-laptop:~/gnash$ ./autogen.sh
processing .
Running aclocal -I macros  ...
Running autoheader...
Running automake --gnu  ...
automake: server/Makefile.am: not supported: source file `swf/ASHandlers.cpp' is in subdirectory
automake: server/Makefile.am: not supported: source file `swf/TagLoadersTable.cpp' is in subdirectory
automake: server/Makefile.am: not supported: source file `swf/tag_loaders.cpp' is in subdirectory
automake: server/Makefile.am: not supported: source file `swf/ASHandlers.cpp' is in subdirectory
automake: server/Makefile.am: not supported: source file `swf/TagLoadersTable.cpp' is in subdirectory
automake: server/Makefile.am: not supported: source file `swf/tag_loaders.cpp' is in subdirectory
backend/Makefile.am:86: warning: automake does not support conditional definition of RENDER_SOURCES in libgnashbackend_la_SOURCES
backend/Makefile.am:83: invalid unused variable name: `RENDER_SOURCES'
doc/C/Makefile.am:98: INSTALL_DATA_HOOK defined both conditionally and unconditionally
doc/C/Makefile.am:99: UNINSTALL_HOOK defined both conditionally and unconditionally
testsuite/libbase/Makefile.am:45: invalid unused variable name: `AM_LDFLAGS'
testsuite/actionscript.all/Makefile.am:92: EXTRA_DIST defined both conditionally and unconditionally
automake: testsuite/actionscript.all/Makefile.am: warning: automake does not support EXTRA_DIST being defined conditionally
automake: plugin/Makefile.am: not supported: source file `mozilla-sdk/npn_gate.cpp' is in subdirectory
automake: plugin/Makefile.am: not supported: source file `mozilla-sdk/npp_gate.cpp' is in subdirectory
automake: plugin/Makefile.am: not supported: source file `mozilla-sdk/np_entry.cpp' is in subdirectory
plugin/klash/Makefile.am:77: variable `MP3_LIBS' not defined
plugin/klash/Makefile.am:68: invalid variable `dist_rc_DATA'
plugin/klash/Makefile.am:71: invalid variable `dist_conf_DATA'
plugin/klash/Makefile.am:66: invalid variable `dist_kde_services_DATA'
plugin/klash/Makefile.am:75: invalid variable `dist_appsdata_DATA'
gui/Makefile.am:141: variable `FLTK_SRCS' not defined
gui/Makefile.am:141: variable `FLTK_SRCS' not defined
gui/Makefile.am:141: variable `FLTK_SRCS' not defined
gui/Makefile.am:141: variable `FLTK_SRCS' not defined
gui/Makefile.am:141: variable `FLTK_SRCS' not defined
gui/Makefile.am:141: variable `FLTK_SRCS' not defined
gui/Makefile.am:141: variable `FLTK_SRCS' not defined
gui/Makefile.am:141: variable `FLTK_SRCS' not defined
gui/Makefile.am:141: variable `FLTK_SRCS' not defined
gui/Makefile.am:141: variable `FLTK_SRCS' not defined
gui/Makefile.am:141: variable `FLTK_SRCS' not defined
gui/Makefile.am:141: variable `FLTK_SRCS' not defined
gui/Makefile.am:141: variable `FLTK_SRCS' not defined
gui/Makefile.am:141: variable `FLTK_SRCS' not defined
gui/Makefile.am:141: variable `FLTK_SRCS' not defined
gui/Makefile.am:141: variable `FLTK_SRCS' not defined
gui/Makefile.am:114: variable `MP3_LIBS' not defined
gui/Makefile.am:114: variable `MP3_LIBS' not defined
gui/Makefile.am: gnash_OBJECTS should not be defined
gui/Makefile.am:114: variable `MP3_LIBS' not defined
Running autoconf ...


---

### Post by ssam on 2006-05-24
i think you might need to install automake1.9 and remove any older automake versions.

---

### Post by engla on 2006-05-24
I compiled gnash for dapper/ppc. I have a checkinstall .deb from 7th May if you want to have it. Gnash seems to work pretty well as a stand alone application, if you have DRI. I didn't try the browser plugin.

For some reason I don't really remember how I compiled gnash, but I don't think I had any autogen errors at all. Try both automake1.4 and automake1.9

FWIW, I configured gnash with 

./configure --enable-mp3 --enable-png --enable-jpeg

---

### Post by eidex on 2006-05-24
thanks guys, i'll try it with automake1.9 and if it fails again i'd be glad to get engla's .deb

---

### Post by davygravy on 2006-05-24
A followup question...

How does one go about getting Ubuntu to include gnash as a package for Dapper?  Or would this encouragement have to be directed towards the developers of gnash themselves?

A great flash package would be, well, great.

---

### Post by davygravy on 2006-05-24
A big thank you to Engla, because after uninstalling makefile 1.8 and making sure that only 1.9 was installed, and installing some Ogg Vorbis dev and other dev packages, gnash did compile just fine.  Now, finally, I can watch the [Llama Song]("http://www.albinoblacksheep.com/flash/llama.php") in Ubuntu.

Well, the movie plays, but the sound is not working (only get a loud hiss)...?

Anyone else having luck (or otherwise)?

---

### Post by Rxke on 2006-05-25
Can you give a rough outline what you had to do to get this running? (needed libs, devstuff etc.)

I'd love to recreate your effort myself, and then make a HowTo. Seriously, no flash on PPC is a big problem for many users.

---

### Post by Rxke on 2006-05-25
[QUOTE=davygravy]How does one go about getting Ubuntu to include gnash as a package for Dapper?.[/QUOTE]

I'm wondering about that myself, but not only for Gnash, there's stuff in Debian unstable that I'd love to see in the repo's, but haven't found out how to do a request (or even how to become a maintainer (right word?) for such stuff.

I guess it's probably too late for Dapper anyways, it's frozen quite solidly, but could end up in backports...

---

### Post by davygravy on 2006-05-25
I just used Synaptic to make sure I had automake 1.9 installed (and removed all lower versions of automake).  then I wen to the gnash website and downloaded the tarball.  extracted to desktop.  in a terminal, cd the directory (folder) of the source.  then I used Engla's suggestion of

./configure --enable-mp3 --enable-png --enable-jpeg

This did not work at first.  But the error messages gave a clear picture of what dev packages and other stuff (some libs, IIRC) I still had to install.

Once the command listed above completed w/ no errors, I just did

make

and then

sudo make install

As I said, sound doesn't work in the browswer plugin (at least it didn't for me).  I haven't tried it as a standalone yet.

Good luck.

---

### Post by Rxke on 2006-05-25
I read the gnash doc page, and it doesn't really need a big howto, I guess, after all...

or does it?

---

### Post by 3rdalbum on 2006-05-27
I've heard from one or two other sources that sound doesn't work in Gnash, so it must be unimplemented as yet. Still, it beats the bollocks out of GPLFlash!

---

### Post by Rxke on 2006-05-27
Ah yes, It's somewhere buried in the documentation itself: sound doesn't work... At all.

---

### Post by eidex on 2006-06-07
still problems with compiling gnash:

./configure gives me the following errors:

```
ERROR: No GtkGLext development package installed! You need to have the GtkGLext development package installed to build the GTK gui. Try --with-gui=sdl or install** libgtkglext1-dev**  (using apt-get) or gtkglext-devel (using yum).
ERROR: No Gtk2 development package installed!You need to have the Gtk2 development package installedto compile this project or install **libgtk2.0-dev** (using apt-get) or gtk2-devel (using yum).
        Pango flags are: -I/usr/include/pango-1.0
        Pango libs are: -lpango-1.0
        Glib flags are: -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include
        Glib libs are: -lglib-2.0
        Atk flags are: -I/usr/include/atk-1.0
        Atk libs are: -latk-1.0
        Xft flags are: -I/usr/include/X11
        Xft libs are: -lXft
ERROR: No SDL development package installed! You need to have the SDL development package installed to compile, or install **libsdl1.2-dev** (using apt-get) or SDL-devel (using yum).
WARNING: No SDL_Mixer development package installed! You need to have the SDL Mixer development package installed if you wish to have MP3 support for Gnash. To compile this project with SDL sound support, install libsdl-mixer1.2-dev (using apt-get) or SDL_mixer-devel (using yum).
        POSIX Threads flags are: -I/usr/include
        POSIX Threads lib is: -lpthread

```

apt-get refuses installing libgtkglext1-dev, libgtk2.0-dev, libsdl1.2-dev due to dependency errors (e.g. depends on libglu1-mesa-dev which SHOULD (?) not be installed according to apt-get.

a few weeks ago i thought this was a beta issue, but now i am clueless, should i force apt-get to install these packages?

thanks

--

PS: is there a good howto for creating a *.deb after compiling, or is it harmlass in terms of system stability to compile one cvs after the other and install them?

---

