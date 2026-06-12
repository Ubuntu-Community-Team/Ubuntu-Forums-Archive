---
title: "HOWTO: install winetools for wine under 64bit Dapper"
date: 2006-10-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by Saubazi on 2006-10-10
Firstly I recommend study of this bit since it explains one thing or two about winetools.

[http://ubuntuforums.org/showthread.php?t=149585](http://ubuntuforums.org/showthread.php?t=149585)

first get the 0.9.5 version of wine:

```
 wget http://kent.dl.sourceforge.net/sourceforge/wine/wine_0.9.5-winehq-1_i386.deb

```
force installation:

```
sudo dpkg --force-architecture -i wine_0.9.5-winehq-1_i386.deb
```

Somehow I did not manage with a later version. 
Now comes a difficult part and I think there is a more elegant way of doing this...

Firstly one needs the winetools:

```
wget http://ds80-237-203-29.dedicated.hosteurope.de/wt/winetools-0.9jo-III.tar.gz

```
unpack and install:

```
tar -xf winetools*
cd winetools*
sudo ./install

```
wt and you'll get your messages from missing libraries.
I use chrooted environment parallel to my 64bit so getting the 32bit libraries works by copying them from /chroot/usr/lib to /usr/lib32

I am sure someone can now give a hint (maybe force install libgtk1.2 i386 package?), since I copied following libraries

```
sudo cp /chroot/usr/lib/libgtk-1.2.so.0* /usr/lib32/
sudo cp /chroot/usr/lib/libgdk-1.2.so.0* /usr/lib32/
sudo cp /chroot/usr/lib/libgmodule-1.2.so.0* /usr/lib32/
sudo cp /chroot/usr/lib/libglib-1.2.so.0* /usr/lib32/
sudo cp /chroot/usr/lib/libXxf86dga.so.1* /usr/lib32/
```

Again there must be an easier way to get these 32bit libs under /usr/lib32 without messing with chroot'd environment - I am just no guru and quite new to this.

After this winetools should start with wt and you should get on configuring. I had a problem installing Microsoft Foundation Classes under the Base setup it just would not start downloading the dll files it wanted to have. I closed the download window from the "x" twice and then manually fetched the two dlls from [http://www.dlldump.com/dllfiles/M/](http://www.dlldump.com/dllfiles/M/)

mfc40.dll and mfc42.dll and copied them under ~/.wine/dosfiles/c:/windows/system32 (or whatever)

I am now out to test whether it actually works :)

explorer worked at least...

---

### Post by Kilz on 2006-10-10
A few comments and questions. 
Why are you using such an old version of wine? The current version is 0.9.22. Realise when you do get the current version running you  may have problems setting up the registry and drives. But you will want to have the most current , because a lot of good work has happened in the last 17 versions.
I would not force any libraries since the possibility is that there are 64bit versions of that library. On a 64bit system 64bit libraries are in /usr/lib and 32bit are in /usr/lib32. In the i386 package the 32bit libraries would be in /lib since thats where 32bit libraries are at on a 32bit version. The i386 package when forced would overwrite the 64bit library with a 32bit one. You will have to find out what package those libraries are in and then extract them with ```
sudo dpkg -x nameoffile.deb
``` changing nameoffile for the packages name. Then copy them in.
You do realise the .dll files are copyrighted and you need a license to use them right?

---

### Post by Saubazi on 2006-10-11
Thanks for the advices. Your wine howto is of great help and I am not sure winetools provides any advantages, however, I have been recommended it and I haven't found any remedies for trying it out.

- I did use the older version since the howto was for it and surprisingly some of the installations (for example explorer) did not work with the newer wine. So I figured - take the old one and then upgrade after configuring (it also says the same thing in the 32bit howto what I used as a basis - start with 0.9.5 and then upgrade). However, somewhere explorer got anyway stuck during yesterday evening so this still needs having a look at...(Not that I am so interested in explorer) - on [http://www.von-thadden.de/Joachim/WineTools/](http://www.von-thadden.de/Joachim/WineTools/)
there is an additional wt-config.reg.ie6.reg file for wine 0.9x versions so this might solve it.

- I have had problems running 0.9.22 with my apps that work with 0.9.20 so the newest is not necessarily always the hottest.

- the copyright issue is a valid point therefore I recommend to visit winetools site and read the legal notice. What I wrote about dlls concerns helping the winetools to load the dlls with webbrowser from the address it is trying to use (I am not sure the download would not have worked had I waited, I am not that patient). When getting apps to run and you need the native dlls you won't come around buying a legal windows 98 or something, anyway.

As for the libraries - for those who do not mess with chrooted environment I will search for the relevant packages:

libgtk1.2 for libgtk-1.2.so.0 and libgdk-1.2.so.0 
libglib1.2 for libglib-1.2.so.0 and libgmodule-1.2.so.0
libxxf86dga1 for libXxf86dga.so.1

---

### Post by Saubazi on 2006-10-11
Download links to the packages:
[http://archive.ubuntu.com/ubuntu/pool/main/g/gtk+1.2/libgtk1.2_1.2.10-18_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gtk+1.2/libgtk1.2_1.2.10-18_i386.deb)

[http://archive.ubuntu.com/ubuntu/pool/main/g/glib1.2/libglib1.2_1.2.10-10.1build1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/glib1.2/libglib1.2_1.2.10-10.1build1_i386.deb)

[http://archive.ubuntu.com/ubuntu/pool/main/libx/libxxf86dga/libxxf86dga1_1.0.0-0ubuntu3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/libx/libxxf86dga/libxxf86dga1_1.0.0-0ubuntu3_i386.deb)

Save them to Desktop and then 
cd ~/Desktop
dpkg -x libgtk1.2_1.2.10-18_i386.deb gtklibs
sudo cp gtklibs/usr/lib/libgtk-1.2.so.0* /usr/lib32/
sudo cp gtklibs/usr/lib/libgdk-1.2.so.0* /usr/lib32/
rm -rf gtklibs

dpkg -x libglib1.2_1.2.10-10.1build1_i386.deb libgliblibs
sudo cp libglibs/usr/lib/libglib-1.2.so.0* /usr/lib32/
sudo cp libglibs/usr/lib/libgmodule-1.2.so.0* /usr/lib32/
rm -rf libglibs

dpkg -x libxxf86dga1_1.0.0-0ubuntu3_i386.deb libxxlib
sudo cp libxxlib/usr/lib/libXxf86dga.so.1 /usr/lib32
rm -rf libxxlib

This should be more or less that...

---

