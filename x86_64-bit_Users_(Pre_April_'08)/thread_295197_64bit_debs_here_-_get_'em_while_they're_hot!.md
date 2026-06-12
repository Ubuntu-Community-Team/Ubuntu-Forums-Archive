---
title: "64bit debs here - get 'em while they're hot!"
date: 2006-11-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by fabertawe on 2006-11-07
Hi folks,

I've uploaded [some debs here]("http://www.dpb.org.uk/ubuntu/"). Namely...

[LIST]
[*]**[GYachI]("http://gyachi.sourceforge.net/")** [1.05] - a !Yahoo messenger client. Includes Webcam, file transfer, audibles etc. Doesn't include the chat room voice component as the truespeech-codec used is a closed source 32bit codec from the Windows world. I haven't included any plugins as I can't compile them ;)
[*]**[recordMyDesktop]("http://recordmydesktop.sourceforge.net/")** [0.3.0] - a desktop session recorder, using only open formats - theora for video and vorbis for audio, using the ogg container.
[*]**[Xvidcap]("http://xvidcap.sourceforge.net/")** [1.1.4] - Screen video capture for X. Video can be saved in a number of different formats. Also records audio.
[*]**[Scribes]("http://scribes.sourceforge.net/")** - [0.3.0] a text editor for GNOME purporting to be simple, slim and sleek, yet powerful (Still in development).
[*]**[DreamChess]("http://www.dreamchess.org/")** [0.1.0] - a chess game featuring 2D/3D boards. Includes it's own engine or can be used with any XBoard-compatible chess engine.
[*]**[Kiba-Dock]("http://forum.beryl-project.org/forum-17-kiba-dock")** [0.1.0] - a fun dock program with lots of bouncing icons and effects. Needs a running composite manager.
[*]**[xwinwrap]("http://wiki.beryl-project.org/index.php/Tips/XglGoodies")** - display screensavers or movies on the desktop.
[/LIST]

All the debs were built on Edgy 6.10 with the generic kernel.

Cheers ... Paul

Edit: 10/11/06, added kiba-dock 0.1.0
Edit: 11/11/06, added xwinwrap

---

### Post by fabertawe on 2006-11-07
Some additional info...

recordMyDesktop and Xvidcap will both record Beryl (hooray!).

Xvidcap encodes on-the-fly. You get a full screen capture by detaching the selection frame and drawing full screen. However... I find that if I start at the absolute top left corner (0,0) it will crash. Starting down one pixel (1,1) from there works though! Edit: you actually get full screen capture simply by clicking on the backdrop. Maybe next time I should read the instructions first!

recordMyDesktop encodes after capture and therefore will give better results. It is command line driven (there is a GUI but apparently it does not work with the current test release). The best results for me with Beryl with my AMD64 3000+ and nVidia GeForce 6800 are with
```
recordmydesktop --full-shots --with-shared -shared-threshold 1 --zero-compression -fps 15 -dummy-cursor white
```
Scribes is still in development and at the feedback stage but seems to work pretty well.

Please let me know if I botched anything with the debs as I'm still getting the hang of this.

I think they should all work on Dapper with the possible exception of Scribes. Maybe someone can try this.

Cheers ... Paul

---

### Post by FluffyElmo on 2006-11-08
I just tried Scribes and it worked perfectly, interesting app with potential. 

Thanks!

---

### Post by loell on 2006-11-09
my hat's off to you  paul :KS 
 
 would it be ok to let gyachi developers know , that you've now
 successfully build an amd64 deb package for edgy?

 perhaps they can include it in the official download page

---

### Post by John Jason Jordan on 2006-11-10
> **FluffyElmo said:**
> I just tried Scribes and it worked perfectly,
Will this version of Scribus work on Dapper amd-64?

---

### Post by fabertawe on 2006-11-10
> **John Jason Jordan said:**
> Will this version of Scribus work on Dapper amd-64?

It's not Scribus, it's Scribes ;)  Check the link from the first post for info. I don't know if it'll work on Dapper, someone will have to be the "guinea pig" ;) 

Paul

---

### Post by fabertawe on 2006-11-10
> **loell said:**
> my hat's off to you  paul :KS 
 
 would it be ok to let gyachi developers know , that you've now
 successfully build an amd64 deb package for edgy?

 perhaps they can include it in the official download page

Cheers loell! Sure, go ahead if you wish.

It would be nice if someone could install these things to make sure I have built the debs right first though (you can always remove them after testing, thanks :D ).

Paul

---

### Post by fabertawe on 2006-11-10
> **FluffyElmo said:**
> I just tried Scribes and it worked perfectly, interesting app with potential. 

Thanks!

Cheers Fluff :) 

I've just added [kiba-dock]("http://forum.beryl-project.org/topic-3841-info-post"). A  dock for use with a composite manager, like Beryl or Compiz. Doesn't do much right now as it's still in development. It's hoped that it will be a fully blown panel in time.

Anyway, check out these videos...
[Bouncing launchers]("http://video.google.com/videoplay?docid=7822933511469794054")
[Rope effect]("http://video.google.com/videoplay?docid=-2453491154022766602")

Keepy-uppy anyone? ;) 

Paul

---

### Post by fabertawe on 2006-11-11
I've added [xwinwrap]("http://www.dpb.org.uk/ubuntu"). Once downloaded, extract and install with
```
tar -xzvf /path/to/xwinwrap.tar.gz
sudo cp /path/to/xwinwrap /usr/bin
```
Obviously you will need to change '/path/to/' to the location of the downloaded file ;) 

Check out [this link]("http://wiki.beryl-project.org/index.php/Tips/XglGoodies") for ways to display screensavers and movies on the desktop. Pretty useless but fun!

Paul

---

### Post by encho on 2006-12-02
Anyone has link to scribes amd64 version?

---

### Post by fabertawe on 2006-12-03
> **encho said:**
> Anyone has link to scribes amd64 version?

Did you read the first post? :rolleyes: 

Paul

---

### Post by encho on 2006-12-06
> **fabertawe said:**
> Did you read the first post? :rolleyes: 

Paul

Yes, but I was following the link for Scribes below (not the upper link). Thought you meant that there is 64 deb link at their website. Sorry for confusion, will try it now.

---

### Post by encho on 2006-12-06
I got this message when trying to run it:
> 
$ scribes 
Traceback (most recent call last):
  File "/usr/bin/scribes", line 39, in ?
    main(argv[1:])
  File "/usr/lib/python2.4/site-packages/SCRIBES/dbusmain.py", line 79, in main
    proxy_object.new_window(dbus_interface=scribes_service)
  File "/var/lib/python-support/python2.4/dbus/proxies.py", line 25, in __call__
    ret = self._proxy_method (*args, **keywords)
  File "/var/lib/python-support/python2.4/dbus/proxies.py", line 102, in __call__
    reply_message = self._connection.send_with_reply_and_block(message, timeout)
  File "dbus_bindings.pyx", line 455, in dbus_bindings.Connection.send_with_reply_and_block
dbus_bindings.DBusException: Traceback (most recent call last):
  File "/var/lib/python-support/python2.4/dbus/service.py", line 304, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/python2.4/site-packages/SCRIBES/scribesservice.py", line 79, in new_window
    return self.__open_new_window()
  File "/usr/lib/python2.4/site-packages/SCRIBES/scribesservice.py", line 151, in __open_new_window
    proxy_object = session_bus.get_object("net.sourceforge.Scribes", self.__object_paths[0])
IndexError: list index out of range

Maybe some missing lib?

---

### Post by fabertawe on 2006-12-06
Hi Encho... are you using Edgy? I really couldn't say what the problem is otherwise. I built the deb using dpkg-buildpackage so all dependencies should be correct. Hopefully someone else can also try it.

Paul

---

### Post by encho on 2006-12-09
Yeah, but I am using Xubuntu, so it might be some missing gnome lib. No luck I guess.

---

### Post by loell on 2006-12-09
just guessing here, base on the output, i think you need to install 

python-dbus

```
sudo aptitude install python-dbus
```

---

### Post by xopher on 2006-12-10
Nice work! Thanks for the effort!

---

### Post by prince_niceguy on 2006-12-10
hi... have you thought of putting them in the repository... official or unofficial repositories??? 

nice work pal!!!!

---

### Post by fabertawe on 2006-12-11
> **prince_niceguy said:**
> hi... have you thought of putting them in the repository... official or unofficial repositories??? 

nice work pal!!!!

Thanks guys :) 

I don't have the time or resources to maintain my own repo, although anyone else with one is welcome to add them. Plus I'm still fairly new to Linux and I'm not totally confident in what I'm doing ;) 

I made these debs for myself and thought it only fair to share them, like others have done. I'm not sure I have the time to keep on top of updates but I will try. It would be great if there was a single resource we could all contribute our files to, or maybe get linked from the sticky. At least these forums are a great help with everyone chipping in :-D 

Paul

---

### Post by macross3003 on 2006-12-11
thanks! really useful stuff

---

### Post by encho on 2006-12-12
> **loell said:**
> just guessing here, base on the output, i think you need to install 

python-dbus

```
sudo aptitude install python-dbus
```

That's it! Thanks. :D

---

### Post by tonyisntcreative on 2006-12-18
You don't by chance think you could put a Dapper compatible .deb of xvidcap up, do you?  That one won't install :/.

---

### Post by jvc26 on 2006-12-18
Just put together an amd64 JDK 1.6.0 from [http://www.ubuntuforums.org/showpost.php?p=1877195&postcount=15](http://www.ubuntuforums.org/showpost.php?p=1877195&postcount=15) on the edgy 6.10 kernel (currently used).
If someone wants to host/add to a repo please PM
Il

---

### Post by fabertawe on 2006-12-18
> **tonyisntcreative said:**
> You don't by chance think you could put a Dapper compatible .deb of xvidcap up, do you?  That one won't install :/.

I don't run Dapper now so I can't, sorry. I was sure I read that RAOF had it in his repo but I can't see it now. As I recall it compiled easily (if I'm making a deb it must have compiled easily ;) ), give it a go [(homepage)]("http://sourceforge.net/projects/xvidcap/"), it's a good feeling to do it yourself  :) 

Paul

---

### Post by tonyisntcreative on 2006-12-18
> **fabertawe said:**
> I don't run Dapper now so I can't, sorry. I was sure I read that RAOF had it in his repo but I can't see it now. As I recall it compiled easily (if I'm making a deb it must have compiled easily ;) ), give it a go [(homepage)]("http://sourceforge.net/projects/xvidcap/"), it's a good feeling to do it yourself  :) 

PaulI've been trying on and off for like a month with no luck :/.  I did find a .deb for amd64 for the 1.1.3p7 that worked (kind of), but it wouldn't support the ffmpeg encoding, and that's really annoying.  When I was using the i386 kernel I got it to work no problem, but I can't get it to work on the 64bit one.

I don't want to turn this into a help thread (I'll probably be making one soon, anyways), but maybe someone can solve this for me real quick.

The archive untars without a hitch.  When I cd to the new directory and run ./configure, it works fine for a while but then spits this out at me...
```
checking for PACKAGE... configure: error: Package requirements (gtk+-2.0 >= 2.4.0 libglade-2.0 glib-2.0 gthread-2.0) were not met:

No package 'gtk+-2.0' found
No package 'libglade-2.0' found
No package 'glib-2.0' found
No package 'gthread-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PACKAGE_CFLAGS
and PACKAGE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```
From a quick check in synaptic it seems like these are all installed but just named a little bit differently.  I tried ./configure --help to see if I could figure out what it was trying to tell me to do and got this...
```
`configure' configures this package to adapt to many kinds of systems.

Usage: ./configure [OPTION]... [VAR=VALUE]...

To assign environment variables (e.g., CC, CFLAGS...), specify them as
VAR=VALUE.  See below for descriptions of some of the useful variables.

Defaults for the options are specified in brackets.

Configuration:
  -h, --help              display this help and exit
      --help=short        display options specific to this package
      --help=recursive    display the short help of all the included packages
  -V, --version           display version information and exit
  -q, --quiet, --silent   do not print `checking...' messages
      --cache-file=FILE   cache test results in FILE [disabled]
  -C, --config-cache      alias for `--cache-file=config.cache'
  -n, --no-create         do not create output files
      --srcdir=DIR        find the sources in DIR [configure dir or `..']

Installation directories:
  --prefix=PREFIX         install architecture-independent files in PREFIX
                          [/usr/local]
  --exec-prefix=EPREFIX   install architecture-dependent files in EPREFIX
                          [PREFIX]

By default, `make install' will install all the files in
`/usr/local/bin', `/usr/local/lib' etc.  You can specify
an installation prefix other than `/usr/local' using `--prefix',
for instance `--prefix=$HOME'.

For better control, use the options below.

Fine tuning of the installation directories:
  --bindir=DIR           user executables [EPREFIX/bin]
  --sbindir=DIR          system admin executables [EPREFIX/sbin]
  --libexecdir=DIR       program executables [EPREFIX/libexec]
  --datadir=DIR          read-only architecture-independent data [PREFIX/share]
  --sysconfdir=DIR       read-only single-machine data [PREFIX/etc]
  --sharedstatedir=DIR   modifiable architecture-independent data [PREFIX/com]
  --localstatedir=DIR    modifiable single-machine data [PREFIX/var]
  --libdir=DIR           object code libraries [EPREFIX/lib]
  --includedir=DIR       C header files [PREFIX/include]
  --oldincludedir=DIR    C header files for non-gcc [/usr/include]
  --infodir=DIR          info documentation [PREFIX/info]
  --mandir=DIR           man documentation [PREFIX/man]

Program names:
  --program-prefix=PREFIX            prepend PREFIX to installed program names
  --program-suffix=SUFFIX            append SUFFIX to installed program names
  --program-transform-name=PROGRAM   run sed PROGRAM on installed program names

X features:
  --x-includes=DIR    X include files are in DIR
  --x-libraries=DIR   X library files are in DIR

Optional Features:
  --disable-FEATURE       do not include FEATURE (same as --enable-FEATURE=no)
  --enable-FEATURE[=ARG]  include FEATURE [ARG=yes]
  --enable-maintainer-mode  enable make rules and dependencies not useful
                          (and sometimes confusing) to the casual installer
  --disable-dependency-tracking  speeds up one-time build
  --enable-dependency-tracking   do not reject slow dependency extractors

Optional Packages:
  --with-PACKAGE[=ARG]    use PACKAGE [ARG=yes]
  --without-PACKAGE       do not use PACKAGE (same as --with-PACKAGE=no)
  --with-x                use the X Window System
  --with-forced-embedded-ffmpeg
                          don't look for available ffmpeg, also links
                          statically

Some influential environment variables:
  CC          C compiler command
  CFLAGS      C compiler flags
  LDFLAGS     linker flags, e.g. -L<lib dir> if you have libraries in a
              nonstandard directory <lib dir>
  CPPFLAGS    C/C++ preprocessor flags, e.g. -I<include dir> if you have
              headers in a nonstandard directory <include dir>
  CPP         C preprocessor
  PKG_CONFIG  path to pkg-config utility
  PACKAGE_CFLAGS
              C compiler flags for PACKAGE, overriding pkg-config
  PACKAGE_LIBS
              linker flags for PACKAGE, overriding pkg-config

Use these variables to override the choices made by `configure' or to help
it to find libraries and programs with nonstandard names/locations.
```
Between PACKAGE_CFLAGS, PACKAGE_LIBS and pkg-config I'm a little bit confused.  I'm assuming one of these things can tell ./configure that those packages are somewhere where it isn't looking, but I don't really know for sure.

---

### Post by fabertawe on 2006-12-19
> **tonyisntcreative said:**
> I've been trying on and off for like a month with no luck :/.  I did find a .deb for amd64 for the 1.1.3p7 that worked (kind of), but it wouldn't support the ffmpeg encoding, and that's really annoying.  When I was using the i386 kernel I got it to work no problem, but I can't get it to work on the 64bit one.

I don't want to turn this into a help thread (I'll probably be making one soon, anyways), but maybe someone can solve this for me real quick.

The archive untars without a hitch.  When I cd to the new directory and run ./configure, it works fine for a while but then spits this out at me...
```
checking for PACKAGE... configure: error: Package requirements (gtk+-2.0 >= 2.4.0 libglade-2.0 glib-2.0 gthread-2.0) were not met:

No package 'gtk+-2.0' found
No package 'libglade-2.0' found
No package 'glib-2.0' found
No package 'gthread-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PACKAGE_CFLAGS
and PACKAGE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```
From a quick check in synaptic it seems like these are all installed but just named a little bit differently.

Do you have the *-dev versions of these libraries installed? Try this...
```
sudo apt-get install libgtk2.0-dev libglade2-dev libglib2.0-dev
```

If you get missing dependencies you will need to install the development files for the particular library. Post back on how you get on :) 

Paul

Edit: I've just seen you've already been given this advice in the other thread.

---

### Post by sandysandy on 2007-12-02
> **fabertawe said:**
> I've added [xwinwrap]("http://www.dpb.org.uk/ubuntu"). Once downloaded, extract and install with
```
tar -xzvf /path/to/xwinwrap.tar.gz
sudo cp /path/to/xwinwrap /usr/bin
```
Obviously you will need to change '/path/to/' to the location of the downloaded file ;) 

Check out [this link]("http://wiki.beryl-project.org/index.php/Tips/XglGoodies") for ways to display screensavers and movies on the desktop. Pretty useless but fun!

Paul

hi guys

has anyone tried this out on Ubuntu 7.10 (64 bit).

[http://tombuntu.com/index.php/2007/09/14/animated-wallpaper-with-compiz-fusion-on-ubuntu/](http://tombuntu.com/index.php/2007/09/14/animated-wallpaper-with-compiz-fusion-on-ubuntu/)

regards

---

### Post by ZmooZa on 2007-12-04
@sandysandy
yup, works perfectly here (Ubuntu 7.10 AMD64) :)

---

### Post by nss0000 on 2007-12-04
hells-a-poppin' oh yeah. All 13 world-wide Debiolians should sure hustle-on-out while supplies last. 

It's hard-as-hades to keeping chipping granite cuniform slabs.

---

