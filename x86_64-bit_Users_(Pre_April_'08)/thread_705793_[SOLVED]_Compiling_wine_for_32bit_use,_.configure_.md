---
title: "[SOLVED] Compiling wine for 32bit use, ./configure error"
date: 2008-02-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by DingsBumps on 2008-02-23
I'm trying to build wine on 64bit following [this guide]("http://wiki.winehq.org/WineOn64bit#head-15ce773b2453307f593a3045e558b30a0e8ed64d"), but I'm having a problem. When I get to the ./configure step, I get an error:

```

marc@marc-desktop:~$ CC="gcc-4.2 -m32" LDFLAGS="-L/lib32 -L/usr/lib32 -L`pwd`/lib32 -Wl,-rpath,/lib32 -Wl,-rpath,/usr/lib32" ./configure
bash: ./configure: No such file or directory 
```

Here is the full output of all the directions on the page:

```

marc@marc-desktop:~$ sudo apt-get build-dep wine
[sudo] password for marc:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
marc@marc-desktop:~$ sudo apt-get install libxcomposite-dev gcc-4.2-multilib
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libxcomposite-dev is already the newest version.
gcc-4.2-multilib is already the newest version.
The following packages were automatically installed and are no longer required:
  liblzo1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
marc@marc-desktop:~$ mkdir -p `pwd`/lib32
marc@marc-desktop:~$ ln -s /usr/lib32/libX11.so.6 `pwd`/lib32/libX11.so
ln: creating symbolic link `/home/marc/lib32/libX11.so' to `/usr/lib32/libX11.so.6': File exists
marc@marc-desktop:~$ ln -s /usr/lib32/libXext.so.6 `pwd`/lib32/libXext.so
ln: creating symbolic link `/home/marc/lib32/libXext.so' to `/usr/lib32/libXext.so.6': File exists
marc@marc-desktop:~$ ln -s /usr/lib32/libfreetype.so.6 `pwd`/lib32/libfreetype.so
ln: creating symbolic link `/home/marc/lib32/libfreetype.so' to `/usr/lib32/libfreetype.so.6': File exists
marc@marc-desktop:~$ ln -s /usr/lib32/libfontconfig.so.1 `pwd`/lib32/libfontconfig.so
ln: creating symbolic link `/home/marc/lib32/libfontconfig.so' to `/usr/lib32/libfontconfig.so.1': File exists
marc@marc-desktop:~$ ln -s /usr/lib32/libGL.so.1 `pwd`/lib32/libGL.so
ln: creating symbolic link `/home/marc/lib32/libGL.so' to `/usr/lib32/libGL.so.1': File exists
marc@marc-desktop:~$ ln -s /usr/lib32/libGLU.so.1 `pwd`/lib32/libGLU.so
ln: creating symbolic link `/home/marc/lib32/libGLU.so' to `/usr/lib32/libGLU.so.1': File exists
marc@marc-desktop:~$ ln -s /usr/lib32/libXrender.so.1 `pwd`/lib32/libXrender.so
ln: creating symbolic link `/home/marc/lib32/libXrender.so' to `/usr/lib32/libXrender.so.1': File exists
marc@marc-desktop:~$ ln -s /usr/lib32/libXinerama.so.1 `pwd`/lib32/libXinerama.so
ln: creating symbolic link `/home/marc/lib32/libXinerama.so' to `/usr/lib32/libXinerama.so.1': File exists
marc@marc-desktop:~$ ln -s /usr/lib32/libXi.so.6 `pwd`/lib32/libXi.so
ln: creating symbolic link `/home/marc/lib32/libXi.so' to `/usr/lib32/libXi.so.6': File exists
marc@marc-desktop:~$ ln -s /usr/lib32/libXrandr.so.2 `pwd`/lib32/libXrandr.so
ln: creating symbolic link `/home/marc/lib32/libXrandr.so' to `/usr/lib32/libXrandr.so.2': File exists
marc@marc-desktop:~$ ln -s /usr/lib32/liblcms.so.1 `pwd`/lib32/liblcms.so
ln: creating symbolic link `/home/marc/lib32/liblcms.so' to `/usr/lib32/liblcms.so.1': File exists
marc@marc-desktop:~$ ln -s /usr/lib32/libcrypto.so.0.9.8 `pwd`/lib32/libcrypto.so
ln: creating symbolic link `/home/marc/lib32/libcrypto.so' to `/usr/lib32/libcrypto.so.0.9.8': File exists
marc@marc-desktop:~$ ln -s /usr/lib32/libssl.so.0.9.8 `pwd`/lib32/libssl.so
ln: creating symbolic link `/home/marc/lib32/libssl.so' to `/usr/lib32/libssl.so.0.9.8': File exists
marc@marc-desktop:~$ ln -s /usr/lib32/libxml2.so.2 `pwd`/lib32/libxml2.so
ln: creating symbolic link `/home/marc/lib32/libxml2.so' to `/usr/lib32/libxml2.so.2': File exists
marc@marc-desktop:~$ ln -s /usr/lib32/libjpeg.so.62 `pwd`/lib32/libjpeg.so
ln: creating symbolic link `/home/marc/lib32/libjpeg.so' to `/usr/lib32/libjpeg.so.62': File exists
marc@marc-desktop:~$ ln -s /usr/lib32/libXcomposite.so.1 `pwd`/lib32/libXcomposite.so
ln: creating symbolic link `/home/marc/lib32/libXcomposite.so' to `/usr/lib32/libXcomposite.so.1': File exists
marc@marc-desktop:~$ ln -s /usr/lib32/libcups.so.2 `pwd`/lib32/libcups.so
ln: creating symbolic link `/home/marc/lib32/libcups.so' to `/usr/lib32/libcups.so.2': File exists
marc@marc-desktop:~$ ln -s /usr/lib32/libXcursor.so.1 `pwd`/lib32/libXcursor.so
ln: creating symbolic link `/home/marc/lib32/libXcursor.so' to `/usr/lib32/libXcursor.so.1': File exists
marc@marc-desktop:~$ ln -s /usr/lib32/libsane.so.1 `pwd`/lib32/libsane.so
ln: creating symbolic link `/home/marc/lib32/libsane.so' to `/usr/lib32/libsane.so.1': File exists
marc@marc-desktop:~$ ln -s /usr/lib32/libhal.so.1 `pwd`/lib32/libhal.so
ln: creating symbolic link `/home/marc/lib32/libhal.so' to `/usr/lib32/libhal.so.1': File exists
marc@marc-desktop:~$ ln -s /usr/lib32/libpng12.so.0 `pwd`/lib32/libpng.so
ln: creating symbolic link `/home/marc/lib32/libpng.so' to `/usr/lib32/libpng12.so.0': File exists
marc@marc-desktop:~$ ln -s /usr/lib32/libgphoto2.so.2 `pwd`/lib32/libgphoto2.so
ln: creating symbolic link `/home/marc/lib32/libgphoto2.so' to `/usr/lib32/libgphoto2.so.2': File exists
marc@marc-desktop:~$ ln -s /usr/lib32/libgphoto2_port.so.0 `pwd`/lib32/libgphoto2_port.so
ln: creating symbolic link `/home/marc/lib32/libgphoto2_port.so' to `/usr/lib32/libgphoto2_port.so.0': File exists
marc@marc-desktop:~$ ln -s /usr/lib32/libldap.so.2 `pwd`/lib32/libldap.so
ln: creating symbolic link `/home/marc/lib32/libldap.so' to `/usr/lib32/libldap.so.2': File exists
marc@marc-desktop:~$ ln -s /usr/lib32/libldap_r.so.2 `pwd`/lib32/libldap_r.so
ln: creating symbolic link `/home/marc/lib32/libldap_r.so' to `/usr/lib32/libldap_r.so.2': File exists
marc@marc-desktop:~$ ln -s /usr/lib32/liblber.so.2 `pwd`/lib32/liblber.so
ln: creating symbolic link `/home/marc/lib32/liblber.so' to `/usr/lib32/liblber.so.2': File exists
marc@marc-desktop:~$ ln -s /usr/lib32/libxslt.so.1 `pwd`/lib32/libxslt.so
ln: creating symbolic link `/home/marc/lib32/libxslt.so' to `/usr/lib32/libxslt.so.1': File exists
marc@marc-desktop:~$ CC="gcc-4.2 -m32" LDFLAGS="-L/lib32 -L/usr/lib32 -L`pwd`/lib32 -Wl,-rpath,/lib32 -Wl,-rpath,/usr/lib32" ./configure
bash: ./configure: No such file or directory
marc@marc-desktop:~$ 

```

What can I do so I can build wine? By the way, I don't really understand what I'm doing, I'm just following the [instructions in ahaslams's post on this thread]("http://ubuntuforums.org/showthread.php?t=641987&page=2"). Any ideas?
___________

---

### Post by holihue on 2008-02-23
you have to be inside the directory of the wine source.

```
cd [wine source dir] 
```


EDIT:

1. go to [this site to download the source]("http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=77449")
2. extract the package
3. open a terminal, and cd in to the source directory
4. then you run :
```

sudo apt-get build-dep wine
sudo apt-get install libxcomposite-dev gcc-4.2-multilib

```

and
```

mkdir -p `pwd`/lib32
ln -s /usr/lib32/libX11.so.6 `pwd`/lib32/libX11.so
ln -s /usr/lib32/libXext.so.6 `pwd`/lib32/libXext.so
ln -s /usr/lib32/libfreetype.so.6 `pwd`/lib32/libfreetype.so
ln -s /usr/lib32/libfontconfig.so.1 `pwd`/lib32/libfontconfig.so
ln -s /usr/lib32/libGL.so.1 `pwd`/lib32/libGL.so
ln -s /usr/lib32/libGLU.so.1 `pwd`/lib32/libGLU.so
ln -s /usr/lib32/libXrender.so.1 `pwd`/lib32/libXrender.so
ln -s /usr/lib32/libXinerama.so.1 `pwd`/lib32/libXinerama.so
ln -s /usr/lib32/libXi.so.6 `pwd`/lib32/libXi.so
ln -s /usr/lib32/libXrandr.so.2 `pwd`/lib32/libXrandr.so
ln -s /usr/lib32/liblcms.so.1 `pwd`/lib32/liblcms.so
ln -s /usr/lib32/libcrypto.so.0.9.8 `pwd`/lib32/libcrypto.so
ln -s /usr/lib32/libssl.so.0.9.8 `pwd`/lib32/libssl.so
ln -s /usr/lib32/libxml2.so.2 `pwd`/lib32/libxml2.so
ln -s /usr/lib32/libjpeg.so.62 `pwd`/lib32/libjpeg.so
ln -s /usr/lib32/libXcomposite.so.1 `pwd`/lib32/libXcomposite.so
ln -s /usr/lib32/libcups.so.2 `pwd`/lib32/libcups.so
ln -s /usr/lib32/libXcursor.so.1 `pwd`/lib32/libXcursor.so
ln -s /usr/lib32/libsane.so.1 `pwd`/lib32/libsane.so
ln -s /usr/lib32/libhal.so.1 `pwd`/lib32/libhal.so
ln -s /usr/lib32/libpng12.so.0 `pwd`/lib32/libpng.so
ln -s /usr/lib32/libgphoto2.so.2 `pwd`/lib32/libgphoto2.so
ln -s /usr/lib32/libgphoto2_port.so.0 `pwd`/lib32/libgphoto2_port.so
ln -s /usr/lib32/libldap.so.2 `pwd`/lib32/libldap.so
ln -s /usr/lib32/libldap_r.so.2 `pwd`/lib32/libldap_r.so
ln -s /usr/lib32/liblber.so.2 `pwd`/lib32/liblber.so
ln -s /usr/lib32/libxslt.so.1 `pwd`/lib32/libxslt.so

```

and then to compile:

```

CC="gcc-4.2 -m32" LDFLAGS="-L/lib32 -L/usr/lib32 -L`pwd`/lib32 -Wl,-rpath,/lib32 -Wl,-rpath,/usr/lib32" ./configure
make 
sudo make install

```


I hope it works

---

### Post by DingsBumps on 2008-02-23
Well, you were right, I had to be in the right directory. 

the CC="gcc  step did give me a missing library error but I ignored it, and right now it is compiling. I'll edit and post my results.

Edit:  looking good, wine compiled, we'll see if it works!

---

