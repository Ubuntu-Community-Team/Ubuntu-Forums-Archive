---
title: "athlon 64 939p. + ati x550xt grap. card."
date: 2006-01-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by cilimpuli on 2006-01-15
i am a newer in kubuntu. i have this graphic card and i have not solve the driver problem for 2 days yet. i read and proceed on page [http://ubuntuforums.org/showthread.php?t=78466](http://ubuntuforums.org/showthread.php?t=78466)
but it doesn't working. cause its a complicated doc. i can not be aware of which one for 32 and 64 bit user. on the ati driver pages it is said we must install first i386 file and then x64. but as i try to proceed this command sudo sh ./ati-driver-installer-8.20.8-i386.run --buildpkg Ubuntu/breezy
some error following occure.

Generating package: Ubuntu/breezy
cp: cannot stat `/home/mehmet/fglrx-install/x680_64a/*': No such file or directory
/tmp/fglrx ~/fglrx-install
Package build failed!
Package build utility output:
dpkg-buildpackage: source package is fglrx-installer
dpkg-buildpackage: source version is 8.20.8-1
dpkg-buildpackage: source changed by ATI Technologies Inc. <http://www.ati.com/support/driver.html>
dpkg-buildpackage: host architecture amd64
 debian/rules build
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
if [ -f /tmp/fglrx/debian/10fglrx.template ]; then \
  sed -e "s|#XMODDIR#|usr/X11R6/lib/modules|" -e "s|#XMODDIR32#|usr/X11R6/lib32/modules|" \
    /tmp/fglrx/debian/10fglrx.template > /tmp/fglrx/debian/10fglrx; \
fi
dh_testdir
dh_testdir
 fakeroot debian/rules binary
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
if [ -f /tmp/fglrx/debian/10fglrx.template ]; then \
  sed -e "s|#XMODDIR#|usr/X11R6/lib/modules|" -e "s|#XMODDIR32#|usr/X11R6/lib32/modules|" \
    /tmp/fglrx/debian/10fglrx.template > /tmp/fglrx/debian/10fglrx; \
fi
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
        usr/lib \
        usr/X11R6/lib/modules \
        usr/X11R6/lib/modules/dri \
        usr/X11R6/lib/modules/drivers \
        usr/X11R6/lib/modules/linux \
        usr/share/fglrx/diversions
# the amd64 package includes 32bit compatibility libraries
dh_installdirs -pxorg-driver-fglrx \
        usr/lib32 \
        usr/X11R6/lib32/modules \
        usr/X11R6/lib32/modules/dri \
        usr/X11R6/lib32/modules/drivers \
        usr/X11R6/lib32/modules/linux \
        etc/X11/Xsession.d
dh_installdirs -pxorg-driver-fglrx-dev \
        usr/include \
        usr/lib
dh_installdirs -pfglrx-kernel-source \
        usr/src/modules/fglrx \
        usr/src/modules/fglrx/debian
dh_installdirs -A -pfglrx-control \
        usr/bin \
        usr/share \
        usr/share/applnk \
        usr/share/gnome \
        usr/share/gnome/apps \
        usr/share/icons \
        usr/share/pixmaps
dh_installdirs -pfglrx-sources \
        usr/src
dh_install
# Driver package
dh_install -pxorg-driver-fglrx "usr/X11R6/bin/fgl*"      "usr/bin"
dh_install -pxorg-driver-fglrx "usr/X11R6/bin/aticonfig" "usr/bin"
cp: cannot stat `./usr/X11R6/bin/aticonfig': No such file or directory
dh_install: command returned error code 256
make: *** [binary] Error 1
~/fglrx-install
Removing temporary directory: fglrx-install

is there any body having 64 bit amd processor and x550 ati grap. card and the succeed in installing driver?

---

### Post by bonzodog on 2006-01-15
eep...this comes down to the fact that ATI drivers are very difficult to install correctly. you could try creating the aticonfig dir in /usr/X11R6/bin/. Mlomkers how to is complicated, but the drivers are very difficult to install and get working correctly.

---

### Post by cilimpuli on 2006-01-15
as i proceed the ati installer x64, there is no problem. It extracts them correctly but when i reboot kubuntu does not open and i start it in recovery mode and change the ati to vesa so it starts normal mode but finally the driver is not done correctly. I read somewhere it is to be change to vesa first but in there also there was no solution about them. an this page [http://www2.ati.com/drivers/linux/linux_8.16.20.html](http://www2.ati.com/drivers/linux/linux_8.16.20.html) 
there are some informations about my grap. card x550 bot the set up file is different as 8.16.20. I dont know what to do..

---

### Post by cilimpuli on 2006-01-29
there is nobody having AMD 64 processor 939 pin and ati graphic card x550?..I have still install my grap. card to Kubuntu..please help..

---

### Post by WirelessMike on 2006-03-09
I have a similar configuration, but sorry, I can't relate...

I installed kubuntu 5.10 on skt754 AMD Athlon64 (3700+) with an ATI x700 card and have had no issues, whatsoever

---

### Post by Gruner on 2006-03-29
I'm in the same boat.  
A new install of 64-bit Ubuntu 5.10 on an AMD 64 with an ATI X800.  My X never worked at all.  I tried running the same install program from ATI.  I got the same results that **cilimpuli** did - error building the package...[QUOTE=cilimpuli]
Generating package: Ubuntu/breezy
cp: cannot stat `/home/mehmet/fglrx-install/x680_64a/*': No such file or directory
/tmp/fglrx ~/fglrx-install
Package build failed!
Package build utility output:[/QUOTE]So I'll just subscribe to this thread and hope someone can help us both out.

---

### Post by zonky85 on 2007-12-27
I'm in a similar situation only I'm missing a different file

cannot stat `./usr/X11R6/lib/modules/dri': No such file or directory

Running Athalon 3800+ 64 x2 ATI x1900gt 

hoping for a little help

---

