---
title: "doomsday on 8.04 AMD64"
date: 2008-10-24
forum: x86 64-bit Users
---

### Post by lordcap90 on 2008-10-24
I have been trying to compile doomsday on my 64 bit box with no luck. This is what happens when i try with the latest svn verson of doomsday.
> 
~$ cd ~/Desktop/doomsday/build
~/Desktop/doomsday/build$ cmake ../
-- The C compiler identification is GNU
-- The CXX compiler identification is GNU
-- Check for working C compiler: /usr/bin/gcc
-- Check for working C compiler: /usr/bin/gcc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- Looking for include files CMAKE_HAVE_PTHREAD_H
-- Looking for include files CMAKE_HAVE_PTHREAD_H - found
-- Looking for pthread_create in pthreads
-- Looking for pthread_create in pthreads - not found
-- Looking for pthread_create in pthread
-- Looking for pthread_create in pthread - found
-- CURL was not found. Make sure CURL_LIBRARY and CURL_INCLUDE_DIR are set.
-- Found PythonInterp: /usr/bin/python2.5
-- Found Curses: /usr/lib/libcurses.so
-- Looking for XOpenDisplay in /usr/lib/libX11.so;/usr/lib/libXext.so
-- Looking for XOpenDisplay in /usr/lib/libX11.so;/usr/lib/libXext.so - found
-- Looking for gethostbyname
-- Looking for gethostbyname - found
-- Looking for connect
-- Looking for connect - found
-- Looking for remove
-- Looking for remove - found
-- Looking for shmat
-- Looking for shmat - found
-- Looking for IceConnectionNumber in ICE
-- Looking for IceConnectionNumber in ICE - found
-- Found X11: /usr/lib/libX11.so
-- Looking for doxygen...
-- Looking for doxygen... - found /usr/bin/doxygen
-- Looking for dot tool...
-- Looking for dot tool... - found /usr/bin/dot
-- Check if the system is big endian
-- Searching 16 bit integer
-- Looking for sys/types.h
-- Looking for sys/types.h - found
-- Looking for stdint.h
-- Looking for stdint.h - found
-- Looking for stddef.h
-- Looking for stddef.h - found
-- Check size of unsigned short
-- Check size of unsigned short - done
-- Using unsigned short
-- Check if the system is big endian - little endian
CMake Error at CMakeLists.txt:468 (MESSAGE):
  ** libGL not found.  On Ubuntu install libgl1-mesa-dev.  On Mac OSX install
  FIXME.  On Windows install FIXME.


-- Configuring done

If this is possible at all, will someone let me know.

---

### Post by Jouke74 on 2008-10-24
You need to install the development libraries if you are compiling. In your case it starts with libgl1-mesa-dev. Probably, more will come up after this one is fixed, so be prepared. Most of them can be found through synaptic package manager.

---

### Post by Yellow Pasque on 2008-10-24
> -- CURL was not found. Make sure CURL_LIBRARY and CURL_INCLUDE_DIR are set.
Since it's complaing about curl:
```
sudo apt-get install libcurl4-gnutls-dev
```

---

### Post by lordcap90 on 2008-10-25
Installed CURL as per your instutions
> ~/Desktop/doomsday/build$ cmake ../
-- The C compiler identification is GNU
-- The CXX compiler identification is GNU
-- Check for working C compiler: /usr/bin/gcc
-- Check for working C compiler: /usr/bin/gcc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- Looking for include files CMAKE_HAVE_PTHREAD_H
-- Looking for include files CMAKE_HAVE_PTHREAD_H - found
-- Looking for pthread_create in pthreads
-- Looking for pthread_create in pthreads - not found
-- Looking for pthread_create in pthread
-- Looking for pthread_create in pthread - found
-- Found PythonInterp: /usr/bin/python2.5
-- Found Curses: /usr/lib/libcurses.so
-- Looking for XOpenDisplay in /usr/lib/libX11.so;/usr/lib/libXext.so
-- Looking for XOpenDisplay in /usr/lib/libX11.so;/usr/lib/libXext.so - found
-- Looking for gethostbyname
-- Looking for gethostbyname - found
-- Looking for connect
-- Looking for connect - found
-- Looking for remove
-- Looking for remove - found
-- Looking for shmat
-- Looking for shmat - found
-- Looking for IceConnectionNumber in ICE
-- Looking for IceConnectionNumber in ICE - found
-- Found X11: /usr/lib/libX11.so
-- Looking for doxygen...
-- Looking for doxygen... - found /usr/bin/doxygen
-- Looking for dot tool...
-- Looking for dot tool... - found /usr/bin/dot
-- Check if the system is big endian
-- Searching 16 bit integer
-- Looking for sys/types.h
-- Looking for sys/types.h - found
-- Looking for stdint.h
-- Looking for stdint.h - found
-- Looking for stddef.h
-- Looking for stddef.h - found
-- Check size of unsigned short
-- Check size of unsigned short - done
-- Using unsigned short
-- Check if the system is big endian - little endian
CMake Error at CMakeLists.txt:468 (MESSAGE):
  ** libGL not found.  On Ubuntu install libgl1-mesa-dev.  On Mac OSX install
  FIXME.  On Windows install FIXME.


-- Configuring done
I have libgl1 installed in synaptic, but that doesent seem to be helping.

---

### Post by Yellow Pasque on 2008-10-25
```
sudo apt-get install libgl1-mesa-dev
```

---

### Post by lordcap90 on 2008-10-25
> sudo apt-get install libgl1-mesa-dev 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgl1-mesa-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Still doesn't work. This is a 64 bit system remember, this program seems to have trouble with that, if anyone has any more ideas post them.

---

### Post by jpkotta on 2008-10-25
Every few months I try to compile doomsday, and it usually doesn't build.  I just tried it and it worked!  Unfortunately, it segfaulted when I tried to play a map.  It did get to the menu though.  I'd guess it will work pretty well in a few more months.

What I do is just --force-architecture an old 32-bit .deb.  Sound doesn't work, but it's good enough for me.  The .deb is too big to post here, otherwise I would.  File name is deng_1.8.9+1.9.0beta3-1ubuntu2_i386.deb.

---

### Post by jpkotta on 2008-10-25
I spoke too soon.  Some maps work, like the original episode 1.  Still buggy though.

I have tons of dev packages installed, I don't know what is needed for doomsday.  Maybe this will help:

```
$ dpkg -l *mesa* | grep ^i
ii  libgl1-mesa-dev                            7.0.3~rc2-1ubuntu3                       A free implementation of the OpenGL API -- G
ii  libgl1-mesa-glx                            7.0.3~rc2-1ubuntu3                       A free implementation of the OpenGL API -- G
ii  libglu1-mesa                               7.0.3~rc2-1ubuntu3                       The OpenGL utility library (GLU)
ii  libglu1-mesa-dev                           7.0.3~rc2-1ubuntu3                       The OpenGL utility library -- development fi
ii  mesa-common-dev                            7.0.3~rc2-1ubuntu3                       Developer documentation for Mesa
 
```

```
$ dpkg -S libGL.so
libgl1-mesa-dev: /usr/lib/libGL.so
diversion by nvidia-glx-new from: /usr/X11R6/lib/libGL.so.1
diversion by nvidia-glx-new to: /usr/X11R6/lib/nvidia/libGL.so.1.xlibmesa
diversion by nvidia-glx-new from: /usr/X11R6/lib32/libGL.so.1.2
diversion by nvidia-glx-new to: /usr/X11R6/lib32/nvidia/libGL.so.1.2.xlibmesa
diversion by nvidia-glx-new from: /usr/lib/libGL.so.1
diversion by nvidia-glx-new to: /usr/lib/nvidia/libGL.so.1.xlibmesa
libgl1-mesa-glx: /usr/lib/libGL.so.1
diversion by nvidia-glx-new from: /usr/X11R6/lib32/libGL.so.1.2
diversion by nvidia-glx-new to: /usr/X11R6/lib32/nvidia/libGL.so.1.2.xlibmesa
diversion by nvidia-glx-new from: /usr/X11R6/lib/libGL.so.1
diversion by nvidia-glx-new to: /usr/X11R6/lib/nvidia/libGL.so.1.xlibmesa
diversion by nvidia-glx-new from: /usr/lib/libGL.so.1.2
diversion by nvidia-glx-new to: /usr/lib/nvidia/libGL.so.1.2.xlibmesa
diversion by nvidia-glx-new from: /usr/lib/libGL.so.1
diversion by nvidia-glx-new to: /usr/lib/nvidia/libGL.so.1.xlibmesa
diversion by nvidia-glx-new from: /usr/X11R6/lib32/libGL.so.1
diversion by nvidia-glx-new to: /usr/X11R6/lib32/nvidia/libGL.so.1.xlibmesa
diversion by nvidia-glx-new from: /usr/X11R6/lib/libGL.so.1.2
diversion by nvidia-glx-new to: /usr/X11R6/lib/nvidia/libGL.so.1.2.xlibmesa
diversion by nvidia-glx-new from: /usr/lib32/libGL.so.1
diversion by nvidia-glx-new to: /usr/lib32/nvidia/libGL.so.1.xlibmesa
ia32-libs: /usr/lib32/libGL.so.1
diversion by nvidia-glx-new from: /usr/lib32/libGL.so.1.2
diversion by nvidia-glx-new to: /usr/lib32/nvidia/libGL.so.1.2.xlibmesa
diversion by nvidia-glx-new from: /usr/lib32/libGL.so.1
diversion by nvidia-glx-new to: /usr/lib32/nvidia/libGL.so.1.xlibmesa
diversion by nvidia-glx-new from: /usr/X11R6/lib/libGL.so.1.2
diversion by nvidia-glx-new to: /usr/X11R6/lib/nvidia/libGL.so.1.2.xlibmesa
diversion by nvidia-glx-new from: /usr/lib/libGL.so.1.2
diversion by nvidia-glx-new to: /usr/lib/nvidia/libGL.so.1.2.xlibmesa
libgl1-mesa-glx: /usr/lib/libGL.so.1.2
diversion by nvidia-glx-new from: /usr/X11R6/lib32/libGL.so.1
diversion by nvidia-glx-new to: /usr/X11R6/lib32/nvidia/libGL.so.1.xlibmesa
diversion by nvidia-glx-new from: /usr/lib32/libGL.so.1.2
diversion by nvidia-glx-new to: /usr/lib32/nvidia/libGL.so.1.2.xlibmesa
ia32-libs: /usr/lib32/libGL.so.1.2

```

---

### Post by lordcap90 on 2008-10-26
force architecture on the 32 bit deb, first level just about works until the exit. any way to install the 32 bit mesa library.

---

