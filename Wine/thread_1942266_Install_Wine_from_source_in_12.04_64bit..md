---
title: "Install Wine from source in 12.04 64bit."
date: 2012-03-17
forum: Wine
---

### Post by 8Kuula on 2012-03-17
Im trying to Install Wine 1.5.0 from source in Ubuntu 12.04 64bit beta

I ran ```
sudo apt-get build-dep wine
```
Downloaded wine-1.5.0.tar.bz2
Extracted it to ~/scr/wine-1.5.0

From [http://wiki.winehq.org/WineOn64bit](http://wiki.winehq.org/WineOn64bit)
```
sudo apt-get build-dep wine1.4:i386
```
E: Unable to find a source package for wine1.4:i386

```
sudo apt-get build-deb wine:i386
```
Seems to work, but since i ran sudo apt-get build-dep wine allready it spits out
```
$ sudo apt-get build-dep wine:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Picking 'wine1.4' as source package instead of 'wine:i386'
```

configure allways stops in
```
:~/src/wine-1.5.0$ ./configure
checking for X... no
configure: error: X 32-bit development files not found. Wine will be built
without X support, which probably isn't what you want. You will need
to install 32-bit development packages of Xlib/Xfree86 at the very least.
Use the --without-x option if you really want this.
```

So. What im doing wrong?

---

### Post by 3vi1 on 2012-03-17
I don't think you're doing anything wrong.  I've seen the same problem ever since multiarch hit in 12.04, but haven't been motivated enough to figure it out.

[https://bugs.launchpad.net/bugs/944321](https://bugs.launchpad.net/bugs/944321)

---

### Post by dino99 on 2012-03-17
as said into the above report, ubuntu have modified the rules due to multiarch.

what winehq says:  [http://wiki.winehq.org/Wine64](http://wiki.winehq.org/Wine64)

[http://forum.winehq.org/viewtopic.php?t=15013](http://forum.winehq.org/viewtopic.php?t=15013)

---

### Post by 8Kuula on 2012-03-17
Reading those I concluded that, there is currently no way to build 32bit wine in Ubuntu 12.04 64bit. Atleast easily.

Tested building with './configure --enable-win64' well it works, but...
```
wine: Bad EXE format for D:\StarCraft II\StarCraft II.exe
```
:D

Bleh...

---

### Post by krystena on 2012-03-17
Edit: Posted better solutions below, killing this to end confusion.

---

### Post by dino99 on 2012-03-18
as said many times, using a 64 installation is not yet fully supported by some apps (not so rare).
so doing a 32 bits install with a kernel-pae give you less headaches and your whole ram is used too.

---

### Post by 8Kuula on 2012-03-18
Better question would be that is this solved on 12.04 release or not solved at all?
In Ubuntu 10.04 64bit building wasn't problem, this is going backwards in that respect.

Allso I would asume that Wine is not only software that is affected by this.

---

### Post by secretmyth on 2012-03-19
> **8Kuula said:**
> Im trying to Install Wine 1.5.0 from source in Ubuntu 12.04 64bit beta

I ran ```
sudo apt-get build-dep wine
```
Downloaded wine-1.5.0.tar.bz2
Extracted it to ~/scr/wine-1.5.0

From [http://wiki.winehq.org/WineOn64bit](http://wiki.winehq.org/WineOn64bit)
```
sudo apt-get build-dep wine1.4:i386
```
E: Unable to find a source package for wine1.4:i386

```
sudo apt-get build-deb wine:i386
```
Seems to work, but since i ran sudo apt-get build-dep wine allready it spits out
```
$ sudo apt-get build-dep wine:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Picking 'wine1.4' as source package instead of 'wine:i386'
```

configure allways stops in
```
:~/src/wine-1.5.0$ ./configure
checking for X... no
configure: error: X 32-bit development files not found. Wine will be built
without X support, which probably isn't what you want. You will need
to install 32-bit development packages of Xlib/Xfree86 at the very least.
Use the --without-x option if you really want this.
```

So. What im doing wrong?

install those packs 1st:
sudo apt-get install flex bison qt3-dev-tools qt4-qmake

---

### Post by 8Kuula on 2012-03-19
> **secretmyth said:**
> install those packs 1st:
sudo apt-get install flex bison qt3-dev-tools qt4-qmake
```
checking for X... no
configure: error: X 32-bit development files not found. Wine will be built
without X support, which probably isn't what you want. You will need
to install 32-bit development packages of Xlib/Xfree86 at the very least.
Use the --without-x option if you really want this.
```

---

### Post by krystena on 2012-03-22
sudo apt-get install libfontconfig-dev  libfreetype6-dev libglu-dev libgphoto2-2-dev libgsm1-dev libice-dev libjpeg-dev libldap-dev  libmpg123-dev libncurses5-dev libopenal-dev libpng-dev libsm-dev libssl-dev libusb-dev libx11-dev libxcomposite-dev libxcursor-dev libxext-dev libxi-dev libxinerama-dev libxml2-dev libxrandr-dev libxrender-dev libxslt-dev libxt-dev libxxf86vm-dev oss4-dev **ia32-libs-dev**

ia32-libs-dev will get you by the X error

Enjoy, should be a rather clean install from there. Note I did this in Debian and do not have Ubuntu to test it on. Compiles 32-bit wine for anyone confused since the wine64 is useless for many at this stage.

---

### Post by 8Kuula on 2012-03-23
in Ubuntu 12.04:
```
$ apt-get -s install libfontconfig-dev libfreetype6-dev libglu-dev libgphoto2-2-dev libgsm1-dev libice-dev libjpeg-dev libldap-dev libmpg123-dev libncurses5-dev libopenal-dev libpng-dev libsm-dev libssl-dev libusb-dev libx11-dev libxcomposite-dev libxcursor-dev libxext-dev libxi-dev libxinerama-dev libxml2-dev libxrandr-dev libxrender-dev libxslt-dev libxt-dev libxxf86vm-dev oss4-dev ia32-libs-dev
NOTE: This is only a simulation!
      apt-get needs root privileges for real execution.
      Keep also in mind that locking is deactivated,
      so don't depend on the relevance to the real current situation!
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'libfontconfig1-dev' instead of 'libfontconfig-dev'
Note, selecting 'libglu1-mesa-dev' instead of 'libglu-dev'
Note, selecting 'libldap2-dev' instead of 'libldap-dev'
Note, selecting 'libpng12-dev' instead of 'libpng-dev'
Note, selecting 'libxslt1-dev' instead of 'libxslt-dev'
Package ia32-libs-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  lib32z1-dev lib32bz2-dev

E: Package 'ia32-libs-dev' has no installation candidate
```

---

### Post by krystena on 2012-03-23
**apt-cache search ia32 | grep dev**

bout the best I can offer you there. I'm under 64-bit Debian Testing. Try enabling the backports perhaps. I think yours is called "romeo". You'll have to do a bit of research for the Ubuntu equiv of this package I think

---

### Post by 8Kuula on 2012-03-24
```
$ apt-cache search ia32 | grep dev
```
gave empty.

Im not 100% sure is this related.
```
$ apt-cache search ia32
grub-efi - GRand Unified Bootloader, version 2 (dummy package)
grub-efi-ia32 - GRand Unified Bootloader, version 2 (EFI-IA32 version)
grub-efi-ia32-bin - GRand Unified Bootloader, version 2 (EFI-IA32 binaries)
lsb-core - Linux Standard Base 4.0 core support package
lsb-cxx - Linux Standard Base 4.0 C++ support package
lsb-desktop - Linux Standard Base 4.0 Desktop support package
lsb-graphics - Linux Standard Base 4.0 graphics support package
lsb-printing - Linux Standard Base 4.0 Printing package
microcode.ctl - Intel IA32/IA64 CPU Microcode Utility
elilo - Bootloader for systems using EFI-based firmware
ia32-libs - ia32 shared libraries - transitional package
lsb-languages - Linux Standard Base 4.0 Runtime Languages package
lsb-multimedia - Linux Standard Base 4.0 Multimedia package
lsb-qt4 - Linux Standard Base 4.0 Qt4 support package
refit - graphical boot menu for ia32 and x64 EFI systems
ia32-libs-multiarch - Multi-arch versions of former ia32-libraries
```
There is 'ia32-libs-multiarch - Multi-arch versions of former ia32-libraries' package.
Currently it do not help.

Little mode detail in that package...
```
$ apt-cache show ia32-libs-multiarch
Package: ia32-libs-multiarch
Priority: extra
Section: universe/libs
Installed-Size: 39
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian ia32-libs Team <pkg-ia32-libs-maintainers@lists.alioth.debian.org>
Architecture: i386
Source: ia32-libs
Version: 20090808ubuntu35
Depends: bluez-alsa, libgettextpo0, gstreamer0.10-plugins-base, gstreamer0.10-plugins-good, gstreamer0.10-fluendo-mp3, gtk2-engines, gtk2-engines-murrine, gtk2-engines-pixbuf, gtk2-engines-oxygen, gvfs, ibus-gtk, libacl1, libaio1, libao4, libasound2, libasound2-plugins, libasyncns0, libattr1, libaudio2, libcanberra-gtk-module, libcap2, libcapi20-3, libcups2, libcupsimage2, libcurl3, libdbus-glib-1-2, libesd0, libfontconfig1, libfreetype6, libgail-common, libgconf-2-4, libgdbm3, libglapi-mesa, libglu1-mesa, libgphoto2-2, libgphoto2-port0, libgtk2.0-0, libmpg123-0, libncursesw5, libnspr4, libnss3, libodbc1, libopenal1, libpulse-mainloop-glib0, libqt4-dbus, libqt4-network, libqt4-opengl, libqt4-qt3support, libqt4-script, libqt4-scripttools, libqt4-sql, libqt4-svg, libqt4-test, libqt4-xml, libqt4-xmlpatterns, libqtcore4, libqtgui4, libqtwebkit4, librsvg2-common, libsane, libsdl-mixer1.2, libsdl-image1.2, libsdl-net1.2, libsdl-ttf2.0-0, libsdl1.2debian, libsqlite3-0, libssl0.9.8, libssl1.0.0, libstdc++5, libstdc++6, libxaw7, libxml2, libxp6, libxslt1.1, libxss1, libxtst6, odbcinst1debian2, libpulsedsp, xaw3dg
Recommends: libgl1-mesa-glx, libgl1-mesa-dri
Suggests: libpam-ldap, libpam-winbind, libnss-ldap
Filename: pool/universe/i/ia32-libs/ia32-libs-multiarch_20090808ubuntu35_i386.deb
Size: 4554
MD5sum: cda17f80e8c2c7e8ed79390c6462d184
SHA1: 108d0a21f7889331105afeb0a86dad9f3da2d90c
SHA256: 93045368d952407c927000ec582b573bf27b367cc13a06d8a9a6f786dd7818e4
Description-en: Multi-arch versions of former ia32-libraries
 This package depends on i386 versions of packages that were removed from
 ia32-libs and transitioned to multi-arch.  This allows applications using
 ia32-libs in previous Ubuntu releases to continue functioning without missing
 libraries.
Multi-Arch: foreign
Description-md5: 2dfb3546bc498438a76638f4fcd00b0c
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
```

---

### Post by 8Kuula on 2012-03-27
I made Ubuntu 12.04 32bit installation in virtualbox.

used: $ ./configure --prefix=/install/location/path
Tarball /install/location/path and move it back to host (ubuntu 12.04 64bit).

wineprefix is going to cry, so need create new clean one.

Not realy happy on this solution :/

---

### Post by unimatrixdoc on 2012-05-28
FYI: This doesn't solve compiling wine but I found the following at:
[http://wiki.winehq.org/WineOn64bit](http://wiki.winehq.org/WineOn64bit)
```

sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get install wine1.5 wine1.5-i386:i386 wine1.5-amd64

```

---

### Post by LordEager on 2012-07-22
I bump this... actually it's possible to perform a 32 bit wine compiling in a chroot built in 32bit as explained here [http://wiki.winehq.org/WineOn64bit#head-77def7ca75193f24e358dba3dd6bcf674bd61b37](http://wiki.winehq.org/WineOn64bit#head-77def7ca75193f24e358dba3dd6bcf674bd61b37) .
Tried it and it seems to work, but actually i'm not able to run anything by that installations retrieving errors about libs... i suppose there is to set some env variable... Anyone got any hint?

---

### Post by melaiv0r12 on 2012-08-31
Hello there 
I found a way to compile wine on ubuntu 12.04 64bit

```
sudo apt-get install xserver-xorg-dev:i386 libfreetype6-dev:i386
```

and because ubuntu does't find freetype we create a symbolick-link

```
sudo ln -s /usr/include/freetype2/freetype /usr/include/

```

and that should do the trick i hope i helped 
cheers :)

---

### Post by Sidner on 2012-09-11
> **melaiv0r12 said:**
> Hello there 
I found a way to compile wine on ubuntu 12.04 64bit

```
sudo apt-get install xserver-xorg-dev:i386 libfreetype6-dev:i386
```

and because ubuntu does't find freetype we create a symbolick-link

```
sudo ln -s /usr/include/freetype2/freetype /usr/include/

```

and that should do the trick i hope i helped 
cheers :)


This works without the chroot workaround? :O If so, it's great!! :D

---

### Post by Sidner on 2012-09-12
> **Sidner said:**
> This works without the chroot workaround? :O If so, it's great!! :D

After doing what melaiv0r12 said and this:
```

sudo apt-get build-dep wine1.4
apt-get source wine1.4
cd wine1.4-*
patch -p1 < foo.patch # and several more patches
dpkg-buildpackage -rfakeroot
cd ..
sudo dpkg -i wine1.4*.deb

```

I got this:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Picking 'wine1.4' as source package instead of 'wine1.4-amd64'
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
sidner@sidner-N53Jq:~/sandbox$ sudo dpkg -i wine1.4*.deb
Selecting previously unselected package wine1.4.
(Reading database ... 191102 files and directories currently installed.)
Unpacking wine1.4 (from wine1.4_1.4-0ubuntu4.1_amd64.deb) ...
Selecting previously unselected package wine1.4-amd64.
Unpacking wine1.4-amd64 (from wine1.4-amd64_1.4-0ubuntu4.1_amd64.deb) ...
Selecting previously unselected package wine1.4-common.
Unpacking wine1.4-common (from wine1.4-common_1.4-0ubuntu4.1_all.deb) ...
Selecting previously unselected package wine1.4-dbg.
Unpacking wine1.4-dbg (from wine1.4-dbg_1.4-0ubuntu4.1_amd64.deb) ...
Selecting previously unselected package wine1.4-dev.
Unpacking wine1.4-dev (from wine1.4-dev_1.4-0ubuntu4.1_amd64.deb) ...
dpkg: dependency problems prevent configuration of wine1.4:
 wine1.4 depends on binfmt-support (>= 1.1.2); however:
  Package binfmt-support is not installed.
 wine1.4 depends on wine1.4-i386 (= 1.4-0ubuntu4.1); however:
  Package wine1.4-i386 is not installed.
dpkg: error processing wine1.4 (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of wine1.4-common:
 wine1.4-common depends on wine1.4 (= 1.4-0ubuntu4.1); however:
  Package wine1.4 is not configured yet.
dpkg: error processing wine1.4-common (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of wine1.4-amd64:
 wine1.4-amd64 depends on wine1.4-common (= 1.4-0ubuntu4.1); however:
  Package wine1.4-common is not configured yet.
dpkg: error processing wine1.4-amd64 (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of wine1.4-dbg:
 wine1.4-dbg depends on wine1.4-amd64 (= 1.4-0ubuntu4.1); however:
  Package wine1.4-amd64 is not configured yet.
dpkg: error processing wine1.4-dbg (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of wine1.4-dev:
 wine1.4-dev depends on wine1.4-amd64 (= 1.4-0ubuntu4.1); however:
  Package wine1.4-amd64 is not configured yet.
dpkg: error processing wine1.4-dev (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Errors were encountered while processing:
 wine1.4
 wine1.4-common
 wine1.4-amd64
 wine1.4-dbg
 wine1.4-dev

```

Any ideas?

---

### Post by opensshd on 2012-09-22
Workaround - amd64 12.04 - stock repos:

sudo apt-cache policy wine

returns 1.4.0

sudo apt-get build-dep wine

Downloaded the source code for it here:

[http://sourceforge.net/projects/wine/files/Source/wine-1.4.tar.bz2/download](http://sourceforge.net/projects/wine/files/Source/wine-1.4.tar.bz2/download)

unpacked the tarball, enter directory 

(After build dep is done):

./configure --without-x --without-freetype
make
sudo make install

Wine installs no errors.

Then as the workaround to the GUI frontend I:

sudo apt-get install q4wine

Doesn't want to remove any packages...


Having an X issue of course, but I am able to 

sudo apt-get install --reinstall wine without removing packages... *working on it*

---

### Post by garylove on 2013-02-25
> **8Kuula said:**
> Im trying to Install Wine 1.5.0 from source in Ubuntu 12.04 64bit beta

I ran ```
sudo apt-get build-dep wine
```Downloaded wine-1.5.0.tar.bz2
Extracted it to ~/scr/wine-1.5.0

From [http://wiki.winehq.org/WineOn64bit](http://wiki.winehq.org/WineOn64bit)
```
sudo apt-get build-dep wine1.4:i386
```E: Unable to find a source package for wine1.4:i386

```
sudo apt-get build-deb wine:i386
```Seems to work, but since i ran sudo apt-get build-dep wine allready it spits out
```
$ sudo apt-get build-dep wine:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Picking 'wine1.4' as source package instead of 'wine:i386'
```configure allways stops in
```
:~/src/wine-1.5.0$ ./configure
checking for X... no
configure: error: X 32-bit development files not found. Wine will be built
without X support, which probably isn't what you want. You will need
to install 32-bit development packages of Xlib/Xfree86 at the very least.
Use the --without-x option if you really want this.
```So. What im doing wrong?


What we just should do is using the [FONT=Arial Black]synaptic package manager[/FONT] to find the necessary items.And select all the relative items that have Xlib words.Then it would need other items and just do the same~

---

### Post by xREDEMPTIONx on 2013-03-01
I've been using the chroot method as suggested here [http://wiki.winehq.org/WineOn64bit](http://wiki.winehq.org/WineOn64bit) as I have a few different wine builds with different patches for use with Playonlinux. 
The easiest way to do this imo is to run your ./configure and make scripts in the chroot and then copy the wine source folder your working on out of the /var/chroot dir into your home folder(anywhere you want really). Then run the make install from there and wine will install itself by default to the /usr/local dir. Since I am using multiple versions with Playonlinux I created a winebuild dir in /usr/local and I use the ./configure --prefix=/usr/local/winebuilds/mywinebuild command when building in the chroot to have the eventual installs reside there.

---

### Post by sdgiffin on 2013-05-31
Does anybody have some experience doing this another way (other than CHROOT) on 13.04 x64? I'm having a lot of trouble as I'm trying to include a minor tweak (bad hack, really) that should FINALLY allow me to get Adobe CS4 installed in WINE which is otherwise impossible because of [WINE Bug #18070]("http://bugs.winehq.org/show_bug.cgi?id=18070").

---

### Post by Rogue_Mouser on 2013-08-20
I was able to compile 32-bit Wine on 64 bit LMDE without CHROOT by using instructions from a combination of sites. Unfortunately, I didn't note most of the URLs I used.


The first was from wiki.winehq.org/WineOn64bit. Since LMDE is built on Debian, not Ubuntu, I used the instructions for Debian Wheezy:


```
sudo apt-get install ia32-libs libc6-dev-i386 lib32z1-dev ia32-libs-dev
``` 


ia32-libs-dev wasn't found in my repositories, so I dug a little deeper into the web, and found this:

```
sudo apt-get install libc6-dev-i386 lib32z1-dev

```

When I ran ./configure, I got the 32 bit X development libraries error. I fixed that with this command:


```
sudo apt-get install xserver-xorg-dev:i386 libfreetype6-dev:i386

```

Unfortunately, this removed my compiler, and the entire build-essential package. I used the package manager to reinstall build-essential, and 32 bit Wine compiled fine from there.

**Edit:** I ran into some problems on reboot. When I looked into my logs, it seems installing xserver-org-dev:i386 and its dependencies removed not only build-essential, but also dkms and my wireless drivers. I reinstalled those, and everything seems to be working fine now.


I hope this helps!

---

### Post by Elbiot on 2014-01-21
Watch that last step, it's a dooooosie!

```

sudo apt-get install xserver-xorg-dev:i386 libfreetype6-dev:i386

[...]
The following packages will be REMOVED:
  build-essential dkms g++ g++-multilib gcc gcc-multilib libfreetype6-dev nvidia-310 virtualbox-guest-dkms
[...]


```

hmmm: compilers, graphics card driver... I said yes anyways after copy and pasting these to reinstall later.  Seemed to work (had to reinstall nvidia-310 again after a reboot for some reason).  But I could not get both libfreetype6-dev and libfreetype6-dev:i386

No really good answer here as far as I can tell.  After pouring sand from one bucket and back again a few times, I did get it to install, but complaining about all sorts of missing functionality.  Oh well.

---

