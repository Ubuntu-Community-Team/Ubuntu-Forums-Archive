---
title: "Wine 0.9.25 info"
date: 2006-11-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by bmontgom on 2006-11-22
Here are some notes on how I got Wine 0.9.25 compiled on Edgy AMD64 with the patches for eve-online.  Before you do any of this search for the various other HOWTOs in the forums on how to install the drivers for your graphics hardware.  In my experience the current driver from NVIDIA (9629) does not work, I use 8776.  I use Xinerama, so YMMV.

1. Go to System->Administration->Software Sources and add the winehq source package line:  
```
deb-src http://wine.budgetdedicated.com/apt edgy main
```
2. In a terminal, create a new directory and download the source package.
```

# mkdir wine
# cd wine
# dpkg-source -x wine
```

3. Go to [http://elfe.mine.nu/eve/linux/](http://elfe.mine.nu/eve/linux/) and download the latest patch and the MachoNet.bash files to your home directory.

4. In the wine-0.9.25 directory that dpkg created, apply the patches for eve-online:
```

# patch -p1 < ~/eve-2006-11-08.diff
```
5. Install the build-depends for the wine package.
```
# sudo apt-get build-dep wine
```
6. Uninstall libicu34-dev.
```
# sudo apt-get remove libicu34-dev
```
7. Install lib32asound2-dev.
```
#sudo apt-get install libasound2-dev
```
8. From the instructions at [winehq]("http://wiki.winehq.org/WineOn64bit"), do the following in the wine source directory:
```
# LDFLAGS="-L/lib32 -L/usr/lib32 -Wl,-rpath,/lib32 -Wl,-rpath,/usr/lib32" ./configure CFLAGS=-fno-stack-protector --prefix=/usr/local
# make depend && make
# sudo make install
```
(The winehq instructions don't include the -fno-stack-protector flag, but there are lots of other places on the net that say it is required for a working wine on Edgy.)

This should produce a working wine install.  Run "winecfg" and change the audio settings to use ALSA.  Once that is done you can run the EVE installer.  Run the MachoNet.bash script in the directory you installed EVE to (mine was ~/.wine/drive_c/eve).  Once that is done start EVE and have fun.

Also, I'm also currently having an issue with wine and my Nvidia cards.  I can only run wine once per X session.  Once I stop a wine process, I have to restart the X server or wine failes to start with a "Bad Window Request" error.

---

