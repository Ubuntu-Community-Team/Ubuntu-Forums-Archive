---
title: "clanlib"
date: 2006-01-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by Jpenguin on 2006-01-28
any idea how to install the newest clanlib (0.8.0) from source

---

### Post by ivandatasync on 2008-06-19
Here are some of the notes from the ./configure, make, make install process on my Inspiron 1420 laptop. 

Everyone needs zlib.

sudo apt-get install zlib-dev 

clangl:

sudo apt-get install libclan2c2a-gl 

If that doesn't work&#8230;

sudo apt-get install libsdl-gfx1.2-dev 
sudo apt-get install xinput
sudo apt-get install libxi-dev

clanSDL:

sudo apt-get install libsdl1.2-dev 
sudo dpkg -S sdl-config

Some other requirements:

sudo apt-get install zlib1g-dev libjpeg62-dev libpng12-dev libmikmod2-dev libogg-dev libvorbis-dev libxxf86vm-dev libxmu-dev

To fix "error: alsa/asoundlib.h: No such file or directory":

sudo apt-get install libasound2-dev

---

