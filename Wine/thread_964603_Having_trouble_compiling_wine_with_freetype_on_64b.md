---
title: "Having trouble compiling wine with freetype on 64bit Ubuntu 8.04"
date: 2008-10-31
forum: Wine
---

### Post by HappyGoLuckyDude on 2008-10-31
Hello,

I am new to these forums although I've been lurking as an unregistered user for some time... I am using the 64bit version of Ubuntu 8.04 and I've been trying to install Wine, which I managed to successfully do but only when I used the --without-freetype option.  I noticed that it takes a while to load though, even when loading notepad.exe.  It seems to output a bunch of error msgs, which I think has something to do with it not being compiled with freetype.  If I was to run ./configure without using that switch, then the configure script fails with this error message:

checking for freetype-config... freetype-config
checking for -lfreetype... not found
configure: error: FreeType development files not found.
Fonts will not be built. Dialog text may be invisible or unaligned.
Use the --without-freetype option if you really want this.

I followed all the instructions at [http://wiki.winehq.org/WineOn64bit](http://wiki.winehq.org/WineOn64bit) but its been of no help.  I even created a libfreetype.so symlink to libfreetype.so.6.3.16 in /usr/lib32, which seemed to be missing, but that didn't help either.

I've been pulling my hair out on this.  It took me forever to finally figure out how to at least compile it without freetype (the instructions for setting LDFLAGS on the wineon64bit wiki are wrong).  You also need another package just to get gcc -m32 to work.  There's not much info out there on how to get this to compile successfully on 64bit ubuntu.

I've noticed that other people are also having this freetype problem.  Someone even mentioned that its a 64 bit issue and that they supposedly figured it out but I didn't see any solution posted (this was on another site).

Now I've ran 32bit ubuntu on my laptop before and was able to get it to compile ok without pulling my hair out.  I'm thinking maybe I should just install 32bit ubuntu because 64bit is problematic.

To add to that I wrote, I do have the dev files for freetype installed (its the latest version from the repos for ubuntu 8.04).

---

### Post by happyhamster on 2008-10-31
- You can download .deb packages from the wine headquarters here (link at the bottom of the page):

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

- It also gives you the option to enable the wine-repository (for automatic updates).

- Anyway, in case you really need to compile wine yourself, I have a few questions:

- Which version of wine are you trying to compile?

- Try running: 

sudo apt-get build-dep wine

- while the wine repository is enabled.

- What is the output of:

dpkg -l "*freetype*"

---

### Post by HappyGoLuckyDude on 2008-11-01
I got wine to work after I fully updated Ubuntu 8.04 by enabling recommended updates.  Previously I only had security updates enabled.  After fully updating the system, I was able to compile wine without freetype and get it in a usable state.  It runs at least a couple of games I threw at it so thats good.  Also all the errors that it was outputting before when I last compiled and ran it, seems to have gone away now that I'm up to date.  I still can't compile it with freetype though.  This is the output from dpkg -l "*freetype*".

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
un  freetype       <none>         (no description available)
un  freetype0      <none>         (no description available)
un  freetype0-dev  <none>         (no description available)
un  freetype1      <none>         (no description available)
un  freetype1-dev  <none>         (no description available)
ii  libfreetype6   2.3.5-1ubuntu4 FreeType 2 font engine, shared library files
ii  libfreetype6-d 2.3.5-1ubuntu4 FreeType 2 font engine, development files


Also, I noticed that if I do a "sudo apt-get build-dep wine" that I get this error message: "E: Unable to find a source package for wine", which I never recall getting before when I had 32bit Ubuntu installed on my laptop.  But, anyhoo I'm happy that I got wine working finally :D

---

### Post by IntuitiveNipple on 2009-01-06
The reason for wine ./configure reporting
```

configure: error: FreeType 32-bit development files not found. Fonts will not be built.

```
on a 64-bit host/build system is that the 32-bit compatibility library binary debian packages do not create all the expected symbolic links for the target libraries (notably, the ones configure is written to look for).

Comparing /usr/lib/libfreetype* with /usr/lib32/libfreetype* will demonstrate the difference. It can be fixed with:
```

sudo ln -s /usr/lib32/libfreetype.so.6 /usr/lib32/libfreetype.so

```
However, this will lead to many similar problems due to the same cause:
```

configure: libxcursor 32-bit development files not found, the Xcursor extension won't be supported.
configure: libxi 32-bit development files not found, the Xinput extension won't be supported.
configure: XShm 32-bit development files not found, X Shared Memory won't be supported.
configure: XShape 32-bit development files not found, XShape won't be supported.
configure: libXxf86vm 32-bit development files not found, XFree86 Vidmode won't be supported.
configure: libxrandr 32-bit development files not found, XRandr won't be supported.
configure: libxinerama 32-bit development files not found, multi-monitor setups won't be supported.
configure: libxcomposite 32-bit development files not found, Xcomposite won't be supported.
configure: libGLU 32-bit development files not found, GLU won't be supported.
configure: libhal 32-bit development files not found, no dynamic device support.
configure: libgnutls 32-bit development files not found, no schannel support.
configure: libsane 32-bit development files not found, scanners won't be supported.
configure: libgphoto2 32-bit development files not found, digital cameras won't be supported.
configure: liblcms 32-bit development files not found, Color Management won't be supported.
configure: libcapi20 32-bit development files not found, ISDN won't be supported.
configure: libcups 32-bit development files not found, CUPS won't be supported.
configure: fontconfig 32-bit development files not found, fontconfig won't be supported.
configure: libldap (OpenLDAP) 32-bit development files not found, LDAP won't be supported.
configure: WARNING: libxrender 32-bit development files not found, XRender won't be supported.
configure: WARNING: No OpenGL library found on this system.
OpenGL and Direct3D won't be supported.
configure: WARNING: libxml2 32-bit development files not found, XML won't be supported.
configure: WARNING: libxslt 32-bit development files not found, xslt won't be supported.
configure: WARNING: OpenSSL 32-bit development files not found, SSL won't be supported.
configure: WARNING: libjpeg 32-bit development files not found, JPEG won't be supported.
configure: WARNING: libpng 32-bit development files not found, PNG won't be supported.

```
The complete set of fix-ups can be found in wine's debian source package **debian/rules** file:
```

config.status: configure
	dh_testdir
	# Add here commands to configure the package.

	# On amd64 we must use our temporary lib directory to create symlinks
	# since the linker demands *.so files and they are missing from the 
	# 32 bit library packages
ifeq ($(DEB_BUILD_ARCH), amd64) 
	mkdir -p $(LIBTMP)
	ln -s /usr/lib32/libX11.so.6 $(LIBTMP)/libX11.so
	ln -s /usr/lib32/libXext.so.6 $(LIBTMP)/libXext.so
	ln -s /usr/lib32/libfreetype.so.6 $(LIBTMP)/libfreetype.so
	ln -s /usr/lib32/libfontconfig.so.1 $(LIBTMP)/libfontconfig.so
	ln -s /usr/lib32/libGL.so.1 $(LIBTMP)/libGL.so
	ln -s /usr/lib32/libGLU.so.1 $(LIBTMP)/libGLU.so
	ln -s /usr/lib32/libXrender.so.1 $(LIBTMP)/libXrender.so
	ln -s /usr/lib32/libXinerama.so.1 $(LIBTMP)/libXinerama.so
	ln -s /usr/lib32/libXxf86vm.so.1 $(LIBTMP)/libXxf86vm.so
	ln -s /usr/lib32/libXi.so.6 $(LIBTMP)/libXi.so
	ln -s /usr/lib32/libXrandr.so.2 $(LIBTMP)/libXrandr.so
	ln -s /usr/lib32/liblcms.so.1 $(LIBTMP)/liblcms.so
	ln -s /usr/lib32/libpng12.so.0 $(LIBTMP)/libpng.so
	ln -s /usr/lib32/libcrypto.so.0.9.8 $(LIBTMP)/libcrypto.so
	ln -s /usr/lib32/libssl.so.0.9.8 $(LIBTMP)/libssl.so
	ln -s /usr/lib32/libgnutls.so.13 $(LIBTMP)/libgnutls.so
	ln -s /usr/lib32/libxml2.so.2 $(LIBTMP)/libxml2.so
	ln -s /usr/lib32/libjpeg.so.62 $(LIBTMP)/libjpeg.so
	ln -s /usr/lib32/libXcomposite.so.1 $(LIBTMP)/libXcomposite.so
	ln -s /usr/lib32/libcups.so.2 $(LIBTMP)/libcups.so
	ln -s /usr/lib32/libXcursor.so.1 $(LIBTMP)/libXcursor.so
	ln -s /usr/lib32/libdbus-1.so.3 $(LIBTMP)/libdbus-1.so
	ln -s /usr/lib32/libhal.so.1 $(LIBTMP)/libhal.so
	ln -s /usr/lib32/libsane.so.1 $(LIBTMP)/libsane.so
	ln -s /usr/lib32/libgphoto2.so.2 $(LIBTMP)/libgphoto2.so
	ln -s /usr/lib32/libgphoto2_port.so.0 $(LIBTMP)/libgphoto2_port.so
	ln -s /usr/lib32/libldap-2.4.so.2 $(LIBTMP)/libldap.so
	ln -s /usr/lib32/libldap_r-2.4.so.2 $(LIBTMP)/libldap_r.so
	ln -s /usr/lib32/liblber-2.4.so.2 $(LIBTMP)/liblber.so
	ln -s /usr/lib32/libxslt.so.1 $(LIBTMP)/libxslt.so
	ln -s /usr/lib32/libcapi20.so.3 $(LIBTMP)/libcapi20.so
	ln -s /usr/lib32/libjack.so.0 $(LIBTMP)/libjack.so
	ln -s /usr/lib32/libodbc.so.1 $(LIBTMP)/libodbc.so
endif

```
When building on 64-bit platforms the configure invocation should be similar to this (borrowed from **debian/rules**):
```

prefix=/usr ./configure --host=x86_64-linux-gnu --build=x86_64-linux-gnu --prefix=${prefix} --mandir=\${prefix}/share/man --infodir=\${prefix}/share/info --libdir=\${prefix}/lib32

```
Instead of trying to hack the library symbolic-link issues (which could lead to problems with package maintenance and upgrades later on) it is far better and neater to use the debian package-building method to create your custom package.

I'll detail how to do that in the next article.

---

### Post by IntuitiveNipple on 2009-01-06
I've added a [tutorial to my Wiki](http://tjworld.net/wiki/Linux/Ubuntu/BuildWinePackages), where it is easier to maintain and update.

---

### Post by An85Zk9tc8rfjV8i on 2009-03-25
Building Wine on Ubuntu  on a 64-bit (x86-64) system

[Building Wine on Ubuntu / Kubuntu 8.10 (Intrepid Ibex)]("http://wiki.winehq.org/WineOn64bit#head-cd47030932ae0f18400cf837c4cc1a267ab374af")

[Building Wine on Ubuntu / Kubuntu 8.04 (Hardy Heron)]("http://wiki.winehq.org/WineOn64bit#head-7703cf4cc6b63630523cf66e77d621e4f81bc873")

[Building Wine on Ubuntu / Kubuntu 7.10 (Gutsy Gibbon) and Debian 4.0 (Etch)]("http://wiki.winehq.org/WineOn64bit#head-c47d9e53f952c5b6260467e0dc158321229216de")

---

