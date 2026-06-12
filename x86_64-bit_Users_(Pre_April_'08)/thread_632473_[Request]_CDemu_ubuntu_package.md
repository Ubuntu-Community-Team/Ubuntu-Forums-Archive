---
title: "[Request] CDemu ubuntu package"
date: 2007-12-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by Major_Kong on 2007-12-05
> CDemu is a kernel module for Linux. It is designed to simulate a CD drive + CD with just simple cue/bin files, which are pretty common in the Windows world. It includes an user space program to control the kernel module. You can use it to watch an SVCD or mount the data track of an bin/cue. However, for watching an SVCD, we would recommend MPlayer which can play bin/cue images directly with the patch a friend and I made for it (more under History). The CDemu project is licensed under the GPL (v2 or later) !
News
2006-08-05

This is CDemu 0.8.0, a CD drive emulator for Linux.

    * 2.6.16 and higher only (no more 2.4).
    * cdemu has file access like in a loop module (Nico Huber).
    * should work on amd64 & SMP systems.
    * .mds, .ccd, .nrg support (Henrik Stokseth).
    * .iso (Calin A. Culianu).
    * some docs.
    * bug fixes.
[http://cdemu.sourceforge.net/](http://cdemu.sourceforge.net/)


This is an excelent module, that's not avaliable in the repo. It's daemon tools for linux. Anyone has a debian package of it that'll work on 7.10 AMD64? Or better yet of userspace-cdemu ?

---

### Post by Jeroi on 2007-12-27
I want this also! I made the amd64 bit version from sources, but kde script mountimage wont work. Also cdemu shows could not connect to daemon.

---

### Post by marx2k on 2007-12-27
Cant you just mount these files as a drive image? You can with ISO's. If you cant do it with cue/bin, cant you just convert them to ISO? 

mkdir /wherever/you/want/to/mount/the/iso
mount myiso.iso /wherever/you/want/to/mount/the/iso/ -t iso9660 -o ro,loop=/dev/loop0

---

### Post by Major_Kong on 2007-12-27
> **marx2k said:**
> Cant you just mount these files as a drive image? You can with ISO's. If you cant do it with cue/bin, cant you just convert them to ISO? 

mkdir /wherever/you/want/to/mount/the/iso
mount myiso.iso /wherever/you/want/to/mount/the/iso/ -t iso9660 -o ro,loop=/dev/loop0

Sure, it's what i do at the moment... But it would be much more convenient just to mount it as i would a .iso, it's an important (to me) feature.

---

### Post by atphalix on 2007-12-29
Good news, they made a deb for ubuntu that you can download at sourceforge project page here: 
[http://sourceforge.net/project/showfiles.php?group_id=93175&package_id=256719]("http://sourceforge.net/project/showfiles.php?group_id=93175&package_id=256719")

---

### Post by Major_Kong on 2007-12-29
Good News indeed, but they're only i386 packages... :S

---

### Post by Kilz on 2007-12-29
> **Major_Kong said:**
> Good News indeed, but they're only i386 packages... :S

Well it looks like that link also has the source packages listed. Why not just compile them? One of the strengths of linux is being able to compile applications. Most of the time its following the README file in the packages.

---

### Post by Major_Kong on 2007-12-30
Already got around to doing that:

[http://rapidshare.com/files/80087070/cdemu-suite.zip.html](http://rapidshare.com/files/80087070/cdemu-suite.zip.html) - Zip with all the debs packages compiled to Ubuntu 7.10 64bit.

And cdemu reached a new version:

> 
This is CDemu 1.0.0, a CD/DVD drive emulator for Linux.

Features:

    * New design - pushed everything possible to userspace.
    * Thin kernel layer (should be more stable & maintainable).
    * .B6T, .CCD, .CDI, .CUE, .ISO, .MDS, .NRG, .TOC support.
    * Command line & GUI clients.


:)

---

### Post by Major_Kong on 2007-12-30
By the way, it works great. :D

---

### Post by Trinidado on 2008-02-08
Sorry for the bump, but I have a dumb question.

I installed all the 64-bit debs, but I can't find the application. Where is it located on my computer, or do I have to run it in the terminal.

When I type "cdemu" in the terminal, it brings up a text-based client thing, which I have no idea how to use.

Thanks!

---

### Post by Major_Kong on 2008-02-09
Don't worry, it's not a dumb question.

Type in the console: 'cdemu -b system status' , to see the avaliable virtual drives.

You should get something like this:
> Devices status:
DEV   LOADED     TYPE       FILENAME
0     0          N/A        N/A
1     0          N/A        N/A


Then you just choose one of the devs, for example dev 0, and type: 'cdemu -b system load 0 mini.cue'
And that's it, the image is mounted.

To unload, just right-click on the virtual drive in nautilus and choose desmount.


PS: Yes, a sort of a graphical interface could be a good idea...

---

### Post by Trinidado on 2008-02-09
Thanks so much! It works great. 

This is a great program for linux, and I hope they continue to develop it. Thanks for the 64-bit debs too!

---

### Post by pxc on 2008-03-30
The debs fail on my box. I'm running Hardy 8.04 beta, so it might be my fault. Anyhow, here's the error info.

```
pxc@cooldude:~/Playground$ cat /var/lib/dkms/vhba/1.0.0/build/make.log
DKMS make.log for vhba-1.0.0 for kernel 2.6.24-12-generic (x86_64)
Sat Mar 29 22:14:15 MST 2008
make -C /lib/modules/`uname -r`/build M=/var/lib/dkms/vhba/1.0.0/build modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-12-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/var/lib/dkms/vhba/1.0.0/build/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[1]: *** [_module_/var/lib/dkms/vhba/1.0.0/build] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-12-generic'
make: *** [modules] Error 2
```

---

### Post by frischi on 2008-04-28
I've had the same issue on kubuntu hardy 64 kde 4 remix

I solved it by downloading deb 64 pkgs from [http://rapidshare.com/files/80087070/cdemu-suite.zip.html]("http://rapidshare.com/files/80087070/cdemu-suite.zip.html")
as suggested in [http://ubuntuforums.org/showthread.php?t=632473]("http://ubuntuforums.org/showthread.php?t=632473")

to get vhba-dkms running:

unpack deb archive to new directory vhba-dkms

```

mkdir vhba-dkms
cd vhba-dkms/
ar -x ../vhba-dkms_1.0.0-1_amd64.deb

```

unpack everything

```

tar xvzf data.tar.gz && rm data.tar.gz
mkdir DEBIAN
cd DEBIAN/
tar xvzf ../control.tar.gz && rm ../control.tar.gz
cd ..

```

(i'm not sure if the next two steps are necessary)

change version number in .DEBIAN/control to 1.0.0-2
change CFLAGS  in  ./usr/src/vhba-1.0.0/Makefile   to EXTRA_CFLAGS

now this is the crucial point!!!!

open file: ./usr/src/vhba-1.0.0/vhba.c

search for the line:
> kaddr = kmap_atomic(sg[i].page, KM_USER0);

and replace with
> kaddr = kmap_atomic(sg[i].page_link, KM_USER0);

now you can rebuild the pkg
```
cd ..
dpkg-deb -b vhba-dkms vhba-dkms_1.0.0-2_adm64.deb
```

as for how to run it I used the ArchLinux guide
[http://wiki.archlinux.org/index.php/CDemu]("http://wiki.archlinux.org/index.php/CDemu")

---

### Post by fede on 2008-05-09
This change suggested by frischi didn't work for me (maybe because I'm using i386?). I had the same error about EXTRA_CFLAGS.

Fixed it by compiling SVN version of vhba module as per instructions in their SourceForge page:

```

sudo apt-get install subversion
svn co https://cdemu.svn.sourceforge.net/svnroot/cdemu/trunk/vhba-module
cd vhba-module
make
sudo checkinstall

```

This error is apparently fixed in SVN version. The gnome tray applet is great!

---

