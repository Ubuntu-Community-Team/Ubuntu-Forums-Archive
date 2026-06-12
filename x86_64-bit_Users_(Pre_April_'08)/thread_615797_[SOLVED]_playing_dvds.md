---
title: "[SOLVED] playing dvds"
date: 2007-11-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by ghettosamson on 2007-11-17
Good day
so, im now trying to play a dvd with movie player. but unfortunately it says the following
========================================================
Totem cannot play this type of media(DVD) because it does not have the appropriate plugins to be able to read from disc. 
Please install the necessary plugins and restart Totem to be able to play this media.
========================================================
So i need a point in the right direction please. I am running gutsy gibbons 64bit. If any more information is needed then i will provide it. thank you

---

### Post by ghettosamson on 2007-11-17
so i followed these directions and still problems.
=======================================
This is for those of you having problems playing commercial DVD's with 64bit Gutsy.
Medibuntu should solve your problems.
1) Add the medibuntu repository for Ubuntu 7.10 "Gutsy Gibbon"

sudo wget [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/medibuntu.list

2)Add the GPG Key.

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

3) To play Encrypted DVD's.

sudo apt-get install libdvdcss2

(i think this package gets installed by one of the media players anyway, but it's not a problem)

4)To play Non-Native Media Formats.

sudo apt-get install w64codecs

5)The next part is installing the appropriate players.
6)System>Amin>Synaptic Package Manager.
7)Search.... xine
Install the following packages.

gxine
totem-xine
xine-ui

These three packages should install the rest of the requirements for playing various media.

From a clean install, doing the above, i have the following packages installed (search...xine)
gxine
libdmx1
libxine1
libxine1-ffmpeg
libexinerama1
totem
totem-xine
xine-ui

Now i can play Encrypted DVD's.
(I did a quick test with Lord of the Rings)
I hope this makes sense and is useful to you.
==================================================
when i try to install the libdvdcss and libdvdcss2 the command prompt tells me the following
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate
and the same for libvdvcss. When i try to play Hitch, movie player tells me the following,
The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss?
when i try to play with gxine it tells me the following:
error reading from dvd. so if anyone could help, please do so

---

### Post by binary_bob on 2007-11-17
hi ghettosamson,
Did you do part 1) and 2)

---

### Post by ghettosamson on 2007-11-17
i redid both parts and managed to install the libdvdcss2, but couldnt get libdvdcss to install, it gives me that same message
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libdvdcss is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss has no installation candidate
and movie player still says 
The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss?
and gxine still says
error reading from dvd

---

### Post by binary_bob on 2007-11-17
ghettosamson,
Why are you trying to install libdvdcss?
You have installed libdvdcss2, now install the w64codecs.
Follow on from there...it should work.

---

