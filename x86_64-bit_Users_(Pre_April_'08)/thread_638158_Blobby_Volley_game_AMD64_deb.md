---
title: "Blobby Volley game AMD64 deb"
date: 2007-12-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by apienk01 on 2007-12-11
I just thought I should share a deb I made for a brilliant and extremely addictive game which is Blobby Volley 2. On [this]("http://ubuntuforums.org/showthread.php?t=242378") thread there is an i386 deb, but this is old version. You can find current version at the [game website]("http://blobby.redio.de") but again, it's i386 only. For us 64-bitters there's only one option - to compile.

So here's my deb for Gutsy amd64. Contrary to both i386 debs mentioned it includes an icon and a desktop file, so you will be able to start the game from the applications menu right away after installation.

[blobby2_0.6a-1_amd64.deb]("http://rapidshare.de/files/38029191/blobby2_0.6a-1_amd64.deb.html")
(due to size limit on Ubuntu Forums I had to upload it to Rapidshare, sorry for inconvenience)

If you would like to use custom backgrounds or bots, they are available for download [here]("http://http://www.blobby-liga.de/blobby-download.php") together with other goodies. Backgrounds should be copied to your ~/.blobby/gfx dir, and bots to ~/.blobby/scripts.

Happy playing!

---

### Post by lnogueir on 2008-01-27
I'm getting an error:

blobby: error while loading shared libraries: libphysfs.so.1: cannot open shared

HELP please!

---

### Post by Perfect Storm on 2008-01-27
Not a good idea to install a .deb from a complete stranger. It's also made with checkinstall without solving any dependency.


But if you must install libphysfs-1.0-0.


You can compile it by yourself. This one is not difficult.

```
sudo aptitude update && sudo aptitude safe-upgrade
sudo aptitude install build-essential checkinstall
sudo aptitude install libphysfs-dev libsdl1.2-dev libx11-dev libgl1-mesa-dev libglu1-mesa-dev


cd ~/Desktop
wget http://downloads.sourceforge.net/blobby/blobby2-linux-0.6a.tar.gz?modtime=1162136935&big_mirror=0
tar zxfv blobby2-linux-0.6a.tar.gz
cd blobby-alpha-6
./configure
make 
sudo checkinstall
```

with checkinstall you now have a "fake" .deb package which can be uninstall in synaptic or by **sudo  dpkg -r blobby-alpha**

---

### Post by apienk01 on 2008-01-28
The deb indeed has been made with checkinstall, but then I repacked it putting all the necessary info in the control file. So the deb installer downloads and installs all dependencies automatically. Here's the complete list of dependencies included in the deb control file:

Depends: libphysfs-1.0-0, libsdl-mixer1.2, libsdl1.2debian, libsdl-image1.2

It installs the following files:

/usr/local/bin/blobby
/usr/local/bin/blobby-server
/usr/local/share/blobby/sounds.zip
/usr/local/share/blobby/gfx.zip
/usr/local/share/blobby/scripts.zip
/usr/local/share/blobby/gf2x.zip
/usr/local/share/blobby/config.xml
/usr/local/share/blobby/inputconfig.xml
/usr/share/applications/blobby2.desktop
/usr/share/pixmaps/blobby.png

The problem is that apparently libphysfs-1.0.0 package does not include libphysfs.so.1 required by blobby. This might be overcome by manually linking this file to existing libphysfs-1.0.so.0:

```
sudo ln -s /usr/lib/libphysfs-1.0.so.0 /usr/lib/libphysfs.so.1
```

Bottom line: I second Artificial Intelligence in his advice that debs from unknown sources generally should not be installed, because they can contain malicious code, but this one is safe.

---

