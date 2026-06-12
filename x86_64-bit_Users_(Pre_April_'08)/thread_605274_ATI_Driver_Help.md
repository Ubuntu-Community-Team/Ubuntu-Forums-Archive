---
title: "ATI Driver Help"
date: 2007-11-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by mwacky on 2007-11-06
I'm having problems installing the latest ATI driver for my Gutsy AMD64 install, I'm hoping it will address the suspend issues I'm having.

Here is the output:
```
mwacker@Milhouse:~/ATI$ bash ./ati-driver-installer-8.42.3-x86.x86_64.run --buildpkg Ubuntu/gutsy
Created directory fglrx-install.vK6441
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.42.3....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Generating package: Ubuntu/gutsy
Package build failed!
Package build utility output:
dpkg-buildpackage: source package is fglrx-installer
dpkg-buildpackage: source version is 8.42.3-1
dpkg-buildpackage: source changed by ATI Technologies Inc. <http://ati.amd.com/support/driver.html>
dpkg-buildpackage: host architecture amd64
dpkg-buildpackage: source version without epoch 8.42.3-1
 debian/rules build
echo "Using architecture: amd64"
Using architecture: amd64
if [ -f /tmp/fglrx.Ft6525/debian/control.template ]; then \
                cat /tmp/fglrx.Ft6525/debian/control.template > /tmp/fglrx.Ft6525/debian/control; \
        fi
for i in preinst postinst postrm shlibs atieventsd.init ; do \
          if [ -f /tmp/fglrx.Ft6525/debian/driver.$i ]; then \
            sed -e "s/#PKGNAME#/xorg-driver-fglrx/" \
                -e "s/#DISTRO#/gutsy/" /tmp/fglrx.Ft6525/debian/driver.$i > \
              /tmp/fglrx.Ft6525/debian/xorg-driver-fglrx.$i; \
          fi; \
        done
if [ -f /tmp/fglrx.Ft6525/debian/10fglrx.template ]; then \
          sed -e "s|#XMODDIR#|usr/lib|" -e "s|#XMODDIR32#|usr/lib32|" \
            /tmp/fglrx.Ft6525/debian/10fglrx.template > /tmp/fglrx.Ft6525/debian/10fglrx; \
        fi
if [ -f /tmp/fglrx.Ft6525/debian/fglrx.default ]; then \
          mv /tmp/fglrx.Ft6525/debian/fglrx.default /tmp/fglrx.Ft6525/debian/fglrx; \
        fi
dh_testdir
dh_testdir
# move licenses away from binary dir
if [ ! -d usr/share/doc/fglrx ]; then \
                mkdir -p usr/share/doc/fglrx; \
                mv usr/X11R6/bin/LICENSE.* usr/share/doc/fglrx; \
        fi
# set executable on user apps
find usr/X11R6/bin -type f | xargs chmod a+x
# remove exec bit from files that don't deserve it
find usr/X11R6/include \
                usr/X11R6/lib \
                usr/X11R6/lib64 \
                usr/share usr/src     -type f | xargs chmod -x
find: usr/X11R6/lib: No such file or directory
find lib -not -name "*.sh" -type f | xargs chmod -x
find lib      -name "*.sh" -type f | xargs chmod +x
# remove exec bit from 64-bit libs too
find usr/X11R6/lib64       -type f | xargs chmod -x
dh_testdir
 fakeroot debian/rules binary
echo "Using architecture: amd64"
Using architecture: amd64
if [ -f /tmp/fglrx.Ft6525/debian/control.template ]; then \
                cat /tmp/fglrx.Ft6525/debian/control.template > /tmp/fglrx.Ft6525/debian/control; \
        fi
for i in preinst postinst postrm shlibs atieventsd.init ; do \
          if [ -f /tmp/fglrx.Ft6525/debian/driver.$i ]; then \
            sed -e "s/#PKGNAME#/xorg-driver-fglrx/" \
                -e "s/#DISTRO#/gutsy/" /tmp/fglrx.Ft6525/debian/driver.$i > \
              /tmp/fglrx.Ft6525/debian/xorg-driver-fglrx.$i; \
          fi; \
        done
if [ -f /tmp/fglrx.Ft6525/debian/10fglrx.template ]; then \
          sed -e "s|#XMODDIR#|usr/lib|" -e "s|#XMODDIR32#|usr/lib32|" \
            /tmp/fglrx.Ft6525/debian/10fglrx.template > /tmp/fglrx.Ft6525/debian/10fglrx; \
        fi
if [ -f /tmp/fglrx.Ft6525/debian/fglrx.default ]; then \
          mv /tmp/fglrx.Ft6525/debian/fglrx.default /tmp/fglrx.Ft6525/debian/fglrx; \
        fi
dh_testdir
dh_testdir
# move licenses away from binary dir
if [ ! -d usr/share/doc/fglrx ]; then \
                mkdir -p usr/share/doc/fglrx; \
                mv usr/X11R6/bin/LICENSE.* usr/share/doc/fglrx; \
        fi
# set executable on user apps
find usr/X11R6/bin -type f | xargs chmod a+x
# remove exec bit from files that don't deserve it
find usr/X11R6/include \
                usr/X11R6/lib \
                usr/X11R6/lib64 \
                usr/share usr/src     -type f | xargs chmod -x
find: usr/X11R6/lib: No such file or directory
find lib -not -name "*.sh" -type f | xargs chmod -x
find lib      -name "*.sh" -type f | xargs chmod +x
# remove exec bit from 64-bit libs too
find usr/X11R6/lib64       -type f | xargs chmod -x
dh_testdir
dh_testdir
dh_testroot
dh_clean -k
rm -f /tmp/fglrx.Ft6525/debian/control
sed -e 's/#XSERVER#/xorg/g' debian/control.template > /tmp/fglrx.Ft6525/debian/control
dh_testdir
dh_testroot
dh_clean -k
dh_installdirs
# Create the directories to install into
dh_installdirs -pxorg-driver-fglrx \
                usr/lib \
                usr/sbin \
                usr/lib \
                usr/lib/xorg/modules \
                usr/lib/xorg/modules/drivers \
                usr/lib/xorg/modules/linux \
                etc/acpi \
                etc/acpi/events \
                etc/default \
                etc/X11/Xsession.d
# the amd64 package includes 32bit compatibility libraries
dh_installdirs -pxorg-driver-fglrx \
                usr/lib32 \
                usr/lib32
dh_installdirs -A -pxorg-driver-fglrx \
                usr/bin \
                usr/sbin \
                usr/share \
                usr/share/applnk \
                usr/share/gnome \
                usr/share/gnome/apps \
                usr/share/icons \
                usr/share/pixmaps
dh_installdirs -pxorg-driver-fglrx-dev \
                usr/include \
                usr/lib
dh_installdirs -pfglrx-kernel-source \
                usr/src/modules/fglrx \
                usr/src/modules/fglrx/debian
dh_install
# Driver package
dh_install -pxorg-driver-fglrx "usr/X11R6/bin/fgl*"      "usr/bin"
dh_install -pxorg-driver-fglrx "usr/X11R6/bin/aticonfig" "usr/bin"
dh_install -pxorg-driver-fglrx "usr/sbin/atieventsd"     "usr/sbin"
dh_installman -pxorg-driver-fglrx "usr/share/man/man8/atieventsd.8"
# amd64 needs some library redirection
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/*.so*"           "usr/lib"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/modules/dri"     "usr/lib"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/modules/linux"   "usr/lib/xorg/modules"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/modules/drivers" "usr/lib/xorg/modules"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/modules/*.so"    "usr/lib/xorg/modules"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/modules/*.a"     "usr/lib/xorg/modules"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib/*.so*"           "usr/lib32"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib/modules/dri"     "usr/lib32"
cp: cannot stat `./usr/X11R6/lib/modules/dri': No such file or directory
dh_install: command returned error code 256
make: *** [binary] Error 1
Removing temporary directory: fglrx-install.vK6441
mwacker@Milhouse:~/ATI$ 
```


Not sure why this is failing, this is the same way I installed 8.40

---

### Post by rbmorse on 2007-11-06
I just went through this today and found that the Envy script has been updated to support both Gutsy and the ATI 8.42.3 driver.  Using Envy to download the driver package from the ATI site and install it into 64-bit Ubuntu was quick, easy and painless.  

Envy is in the Ubuntu repositories, somewhere.  Synaptic finds it if you have all the repository options enabled.

---

### Post by Yellow Pasque on 2007-11-06
The package build option is known to not be working in the for 64-bit. Just do a regular/express install.

---

### Post by hbvtux on 2007-11-06
You should try with  [Envy]("http://albertomilone.com/nvidia_scripts1.html") this install the drivers for ATi or Nvidia it works great I was able to install the ATI Driver for my Acer Laptop (it got board graphics) now I got Compiz Fusion working perfectly on it without problems.

---

### Post by Sabaki on 2007-11-09
> **rbmorse said:**
> I just went through this today and found that the Envy script has been updated to support both Gutsy and the ATI 8.42.3 driver.  Using Envy to download the driver package from the ATI site and install it into 64-bit Ubuntu was quick, easy and painless.  

Envy is in the Ubuntu repositories, somewhere.  Synaptic finds it if you have all the repository options enabled.


Well, every time I run Envy on my Gutsy 64 box it installs the ati-driver-installer-8.40.4-x86.x86_64.run

instead of the ati-driver-installer-8.42.3-x86.x86_64.run

Any idea why or how I can make it use the 8.42.3 driver?

---

### Post by mwacky on 2007-12-06
> **Sabaki said:**
> Well, every time I run Envy on my Gutsy 64 box it installs the ati-driver-installer-8.40.4-x86.x86_64.run

instead of the ati-driver-installer-8.42.3-x86.x86_64.run

Any idea why or how I can make it use the 8.42.3 driver?

I had problems with the 8.42 driver in 64 bit.  Was advised to go with the older version, so unless your card is not working, I would stick with the version from Envy or the Restricted Drivers Manager.

```
$ bash ./ati-driver-installer-8.42.3-x86.x86_64.run --buildpkg Ubuntu/gutsy
```

---

### Post by esteckis on 2008-01-04
ATI has released a new driver dated 12/20.

There is also another post to install the ATI driver,
Envy site [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

1/3/08 The NEW Envy program installed the new ATI dated 12/20/07 driver and special effects and compiz both work. The only thing with the new ATI driver for me is the screen slightly flickers when the screen saver is running. Out of 12 times of trying to get the ATI installed, special effects to take and Compiz working, this NEW ENVY version worked for me.

ATI 1250 series onboard video using UBUNTU Gutsy 64 bit version

---

