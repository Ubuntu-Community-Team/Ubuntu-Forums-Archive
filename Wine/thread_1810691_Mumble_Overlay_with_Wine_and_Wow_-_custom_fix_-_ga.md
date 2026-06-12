---
title: "Mumble Overlay with Wine and Wow - custom fix - gaging interest"
date: 2011-07-23
forum: Wine
---

### Post by dardack on 2011-07-23
Ok so the overlay in wine wow doesn't work if HW cursor is enabled, and is messed up if it's not.  Since I can't live without the given HW cursor since 4.0 and the messed up overlay, i've written code  to add an XOSD overlay for mumble.  Examine SS's for what i'm talking about.

[http://imageshack.us/photo/my-images/804/screenshot44s.png/](http://imageshack.us/photo/my-images/804/screenshot44s.png/)

[http://imageshack.us/photo/my-images/696/screenshot42pv.png/](http://imageshack.us/photo/my-images/696/screenshot42pv.png/)


I will be releasing the code soon, need to talk to 1 person first.  Also in the works, menu to enable, change font size, position, and full channel user overlay, not just who's talking.

---

### Post by dardack on 2011-07-23
OK no menu, or perm list of users, just lights up who's talking.

Examine MumbleXOsd.cpp to change location of XOSD/Color/etc.

First follow (up to the qmake command, don't run this yet): 

[http://mumble.sourceforge.net/BuildingLinux#Installing_from_source]("http://mumble.sourceforge.net/BuildingLinux#Installing_from_source")

These patches are for against the git (at least on 7/23/11).

libxosd is required for this patch:

```
sudo apt-get install libxosd-dev
```

Download every file from:

[http://dardack.is-a-geek.org/MumLinuxOSD/]("http://dardack.is-a-geek.org/MumLinuxOSD/")

put the *.patch files in mumble/

```
cp *.patch mumble/
```

put the MumbleXOsd.cpp/h files in mumble/src/mumble

```
cp MumbleXOsd.* mumble/src/mumble/
```


to patch, in the mumble/ directory:

```

cd mumble
patch -p1 < maincpp.patch
patch -p1 < globalh.patch
patch -p1 < globalcpp.patch
patch -p1 < mumblepro.patch
patch -p1 < usermodelcpp.patch
```

then to compile:

```
qmake -recursive main.pro
```

then

```
make
```

then to run:

```
cd release
./mumble
```

To enable/disable, change the 

```
MumXOsd_Enabled
```

to false in the MumbleXOsd.cpp file.  Look in this file to change the vertical/horizontal position of the OSD.

---

