---
title: "AMD64 Radeon driver problem"
date: 2005-08-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by ianikeev on 2005-08-26
Hi all!

I have already been advised to download the official driver that allows to build the distribution-specific package. It has never succeeded.  The errors were various, I solved most of them but here's the last log, and I am totally at a loss what to do (tried to install without creating the package -- f**ked up my keyboard layout, when I tried to fix this, refused to start X).

Regards,
Igor

The log:

=== cut here ===

/tmp/fglrx /home/igor/Downloads/fglrx-install
Package build failed!
Package build utility output:
dpkg-buildpackage: source package is fglrx-installer
dpkg-buildpackage: source version is 8.16.20-1
dpkg-buildpackage: source maintainer is ATI Technologies Inc. <http://www.ati.com/support/driver.html>
dpkg-buildpackage: host architecture is amd64
 debian/rules build
make: Entering directory `/tmp/fglrx'
echo "Using architecture: amd64"
Using architecture: amd64
if [ -f /tmp/fglrx/debian/control.template ]; then \
	cat /tmp/fglrx/debian/control.template > /tmp/fglrx/debian/control; \
fi
for i in preinst postinst prerm postrm ; do \
  if [ -f /tmp/fglrx/debian/driver.$i ]; then \
    sed -e "s/#PKGNAME#/xorg-driver-fglrx/" /tmp/fglrx/debian/driver.$i > \
      /tmp/fglrx/debian/xorg-driver-fglrx.$i; \
  fi; \
done
dh_testdir
dh_testdir
make: Leaving directory `/tmp/fglrx'
 fakeroot debian/rules binary
make: Entering directory `/tmp/fglrx'
echo "Using architecture: amd64"
Using architecture: amd64
if [ -f /tmp/fglrx/debian/control.template ]; then \
	cat /tmp/fglrx/debian/control.template > /tmp/fglrx/debian/control; \
fi
for i in preinst postinst prerm postrm ; do \
  if [ -f /tmp/fglrx/debian/driver.$i ]; then \
    sed -e "s/#PKGNAME#/xorg-driver-fglrx/" /tmp/fglrx/debian/driver.$i > \
      /tmp/fglrx/debian/xorg-driver-fglrx.$i; \
  fi; \
done
dh_testdir
dh_testdir
dh_testdir
dh_testroot
dh_clean -k
rm -f /tmp/fglrx/debian/control
sed -e 's/#XSERVER#/xorg/g' debian/control.template > /tmp/fglrx/debian/control
dh_testdir
dh_testroot
dh_clean -k
dh_installdirs
# Create the directories to install into
dh_installdirs -pxorg-driver-fglrx \
	usr/X11R6 \
	usr/X11R6/bin \
	usr/X11R6/lib \
	usr/X11R6/lib/modules \
	usr/share/fglrx/diversions
# the amd64 package includes 32bit compatibility libraries
dh_installdirs -pxorg-driver-fglrx \
	usr/X11R6/lib32 \
	usr/X11R6/lib32/modules \
	emul/ia32-linux/usr/X11R6/lib \
	emul/ia32-linux/usr/X11R6/lib/modules/driver \
	emul/ia32-linux/usr/X11R6/lib/modules/linux \
	emul/ia32-linux/usr/X11R6/lib/modules/dri
dh_installdirs -pxorg-driver-fglrx-dev \
	usr/X11R6 \
	usr/X11R6/include \
	usr/X11R6/lib \
	usr/include
dh_installdirs -pfglrx-kernel-source \
	usr/src/modules/fglrx \
	usr/src/modules/fglrx/debian
dh_installdirs -A -pfglrx-control \
	usr/X11R6 \
	usr/X11R6/bin \
	usr/share \
	usr/share/applnk \
	usr/share/gnome \
	usr/share/gnome/apps \
	usr/share/icons \
	usr/share/pixmaps
dh_installdirs -pfglrx-sources \
	usr/src
dh_install
dh_install -pxorg-driver-fglrx "usr/X11R6/bin/fgl*"      "usr/X11R6/bin"
# amd64 needs some library redirection
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/*.so*"     "usr/X11R6/lib"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/modules/*" "usr/X11R6/lib/modules"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib/*.so*"       "usr/X11R6/lib32"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib/modules/*"   "usr/X11R6/lib32/modules"
dh_link    -pxorg-driver-fglrx "usr/X11R6/lib32/libGL.so.1.2" \
	"emul/ia32-linux/usr/X11R6/lib/libGL.so.1.2"
dh_link    -pxorg-driver-fglrx "usr/X11R6/lib32/libfglrx_gamma.so.1.0" \
	"emul/ia32-linux/usr/X11R6/lib/libfglrx_gamma.so.1.0"
dh_link    -pxorg-driver-fglrx "usr/X11R6/lib32/modules/driver/fglrx_drv.o" \
	"emul/ia32-linux/usr/X11R6/lib/modules/driver/fglrx_drv.o"
dh_link    -pxorg-driver-fglrx "usr/X11R6/lib32/modules/linux/libfglrxdrm.a" \
	"emul/ia32-linux/usr/X11R6/lib/modules/linux/libfglrxdrm.a"
dh_link    -pxorg-driver-fglrx "usr/X11R6/lib32/modules/dri/atiogl_a_dri.so" \
	"emul/ia32-linux/usr/X11R6/lib/modules/dri/atiogl_a_dri.so"
dh_link    -pxorg-driver-fglrx "usr/X11R6/lib32/modules/dri/fglrx_dri.so" \
	"emul/ia32-linux/usr/X11R6/lib/modules/dri/fglrx_dri.so"
dh_install -pxorg-driver-fglrx-dev "usr/X11R6/lib64/*.a" "usr/X11R6/lib"
dh_install -pxorg-driver-fglrx-dev "usr/X11R6/include/*" "usr/X11R6/include"
dh_install -pxorg-driver-fglrx-dev "usr/include/*"       "usr/include"
dh_install -pfglrx-kernel-source \
lib/modules/fglrx/build_mod/*.c            \
	lib/modules/fglrx/build_mod/*.h            \
	lib/modules/fglrx/build_mod/*.sh           \
	lib/modules/fglrx/build_mod/lib*           \
	lib/modules/fglrx/build_mod/2.6.x/Makefile \
	usr/src/modules/fglrx
dh_install -pfglrx-kernel-source "debian/changelog" "usr/src/modules/fglrx/debian"
dh_install -pfglrx-kernel-source  \
	debian/copyright        \
	debian/compat           \
	module/rules            \
	module/control.template \
	module/dirs.template    \
	usr/src/modules/fglrx/debian
(cd debian/fglrx-kernel-source/usr/src \
 && chown -R root:src modules \
 && tar -c modules | bzip2 > fglrx.tar.bz2 \
 && rm -rf modules)
# install panel files
dh_install -A -pfglrx-control "usr/X11R6/bin/fireglcontrolpanel"     "usr/X11R6/bin"
dh_install -A -pfglrx-control "usr/share/icons/ati.xpm"           "usr/share/icons"
dh_install -A -pfglrx-control "usr/share/icons/ati.xpm"           "usr/share/pixmaps"
dh_install -A -pfglrx-control "usr/share/gnome/apps/fireglcontrol.desktop"      "usr/share/gnome/apps"
dh_install -A -pfglrx-control "usr/share/applnk/fireglcontrol.kdelnk" "usr/share/applnk"
dh_install -pfglrx-sources "usr/src/*" "usr/src"
dh_installdocs
dh_installdocs -pxorg-driver-fglrx usr/share/doc/fglrx/*
#dh_installchangelogs
dh_link
dh_strip
+ /usr/bin/strip --remove-section=.comment --remove-section=.note --strip-unneeded debian/xorg-driver-fglrx/usr/X11R6/lib/libfglrx_gamma.so.1.0
+ /usr/bin/strip --remove-section=.comment --remove-section=.note --strip-unneeded debian/xorg-driver-fglrx/usr/X11R6/lib/libGL.so.1.2
+ /usr/bin/strip --remove-section=.comment --remove-section=.note --strip-unneeded debian/xorg-driver-fglrx/usr/X11R6/lib/modules/dri/fglrx_dri.so
+ /usr/bin/strip --remove-section=.comment --remove-section=.note --strip-unneeded debian/xorg-driver-fglrx/usr/X11R6/lib/modules/dri/atiogl_a_dri.so
+ /usr/bin/strip --remove-section=.comment --remove-section=.note --strip-unneeded debian/xorg-driver-fglrx/usr/X11R6/lib32/libGL.so.1.2
+ /usr/bin/strip --remove-section=.comment --remove-section=.note --strip-unneeded debian/xorg-driver-fglrx/usr/X11R6/lib32/modules/dri/fglrx_dri.so
+ /usr/bin/strip --remove-section=.comment --remove-section=.note --strip-unneeded debian/xorg-driver-fglrx/usr/X11R6/lib32/modules/dri/atiogl_a_dri.so
+ /usr/bin/strip --remove-section=.comment --remove-section=.note debian/xorg-driver-fglrx/usr/X11R6/bin/fgl_glxgears
+ /usr/bin/strip --remove-section=.comment --remove-section=.note debian/xorg-driver-fglrx/usr/X11R6/bin/fglrx_xgamma
+ /usr/bin/strip --remove-section=.comment --remove-section=.note debian/xorg-driver-fglrx/usr/X11R6/bin/fglrxconfig
+ /usr/bin/strip --remove-section=.comment --remove-section=.note debian/xorg-driver-fglrx/usr/X11R6/bin/fglrxinfo
+ /usr/bin/strip --strip-debug debian/xorg-driver-fglrx/usr/X11R6/lib/modules/linux/libfglrxdrm.a
+ /usr/bin/strip --strip-debug debian/xorg-driver-fglrx-dev/usr/X11R6/lib/libfglrx_gamma.a
+ /usr/bin/strip --remove-section=.comment --remove-section=.note debian/fglrx-control/usr/X11R6/bin/fireglcontrolpanel
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dpkg: &#1092;&#1072;&#1081;&#1083; /usr/-/lib/libGL.so.1 &#1085;&#1077; &#1085;&#1072;&#1081;&#1076;&#1077;&#1085;.
dpkg: &#1092;&#1072;&#1081;&#1083; /usr/-/lib/libX11.so.6 &#1085;&#1077; &#1085;&#1072;&#1081;&#1076;&#1077;&#1085;.
dpkg: &#1092;&#1072;&#1081;&#1083; /usr/-/lib/libXext.so.6 &#1085;&#1077; &#1085;&#1072;&#1081;&#1076;&#1077;&#1085;.
dpkg: &#1092;&#1072;&#1081;&#1083; /usr/-/lib/libm.so.6 &#1085;&#1077; &#1085;&#1072;&#1081;&#1076;&#1077;&#1085;.
dpkg: &#1092;&#1072;&#1081;&#1083; /usr/-/lib/libc.so.6 &#1085;&#1077; &#1085;&#1072;&#1081;&#1076;&#1077;&#1085;.
dpkg: &#1092;&#1072;&#1081;&#1083; /usr/-/lib/libpthread.so.0 &#1085;&#1077; &#1085;&#1072;&#1081;&#1076;&#1077;&#1085;.
dpkg: &#1092;&#1072;&#1081;&#1083; /usr/-/lib/libstdc++.so.5 &#1085;&#1077; &#1085;&#1072;&#1081;&#1076;&#1077;&#1085;.
dpkg: &#1092;&#1072;&#1081;&#1083; /usr/-/lib/librt.so.1 &#1085;&#1077; &#1085;&#1072;&#1081;&#1076;&#1077;&#1085;.
dpkg: &#1092;&#1072;&#1081;&#1083; /usr/-/lib/libdl.so.2 &#1085;&#1077; &#1085;&#1072;&#1081;&#1076;&#1077;&#1085;.
dpkg-shlibdeps: failure: dpkg --search gave error exit status 1
dh_shlibdeps: command returned error code 256
make: *** [binary] &#1054;&#1096;&#1080;&#1073;&#1082;&#1072; 1
make: Leaving directory `/tmp/fglrx'
/home/igor/Downloads/fglrx-install
[Error] Generate Package - error generating package : Ubuntu/5.04


=== cut here ===

---

### Post by eryk on 2005-08-28
I've found fglrx in synaptic, works ok.

I have Radeon 8500.

---

### Post by Septor on 2005-08-29
Unless you have a complete build system you might not be able to build the Ubuntu packages.  I'd recommend you try the regular installer again, but try it from runlevel 1, so that you don't have problems with X:

From a terminal:
```

# kill X and drop to console mode
sudo telinit 1

<login at console prompt>

# install the driver and libraries
sudo ./ati-installer-....

# backup your old xorg.conf
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.OLD

# make a new xorg.conf
sudo fglrxconfig

# test X
startx

# if all worked fine, reboot
sudo reboot

```

Hope that helps

---

