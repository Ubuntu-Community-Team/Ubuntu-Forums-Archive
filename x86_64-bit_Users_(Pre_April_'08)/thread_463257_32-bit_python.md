---
title: "32-bit python?"
date: 2007-06-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by dfreer on 2007-06-03
Hello all!

   Right now I am trying to run Ultima's pSX Frontend on my AMD64 install, which was built for 32-bit machines with python from what I understand of it. First off, I try running the program through the terminal on a fresh install, with only ia32-libs installed. I get this message:
```
$ ./pSXFrontend 
./pSXFrontend: error while loading shared libraries: libpython2.5.so.1.0: cannot open shared object file: No such file or directory
```

Ah, ok, so I looked on [http://packages.ubuntu.com](http://packages.ubuntu.com) for libpython2.5.so.1.0, it seems the file is owned by the package python2.5. So I download that package, and throw the libs in /usr/lib32/ (and by throw I mean I created a quick package that installed the files to the correct location that way I can quickly and safely remove them if I ever need to). I then get this new error message:
```
$ ./pSXFrontend 
Traceback (most recent call last):
  File "<string>", line 5, in <module>
RuntimeError: requires zlib
```

Which is kinda weird. I don't quite know how to proceed from here. What file/package does it need?

---

### Post by kuja on 2007-06-04
You need exactly what it says you need: zlib1g (32-bit, most likely)

---

### Post by dfreer on 2007-06-04
Well, I did install ia32-libs like I said earlier. Which includes lib32z1, which is the 32-bit libraries of zlib1g (you can do a search here and compare the two packages:
[http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=lib32z1&version=feisty&arch=amd64](http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=lib32z1&version=feisty&arch=amd64)
[http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=zlib1g&version=feisty&arch=i386](http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=zlib1g&version=feisty&arch=i386)

That's what I was thinking, but zlib 32-bit libraries appear to be installed correctly. Any other ideas?

```
$ ls -l /usr/lib32/
total 22383
-rw-r--r--  1 root root    2743 2007-03-28 10:36 AuErrorDB
drwxr-xr-x  2 root root     560 2007-06-04 20:40 dri
drwxr-xr-x  2 root root    7640 2007-06-04 20:40 gconv
drwxr-xr-x  3 root root      72 2007-06-04 20:40 gtk-2.0
lrwxrwxrwx  1 root root      15 2007-06-04 20:40 libaudio.so.2 -> libaudio.so.2.4
-rw-r--r--  1 root root   88792 2007-03-28 10:36 libaudio.so.2.4
lrwxrwxrwx  1 root root      18 2007-06-04 20:40 libcairo.so.2 -> libcairo.so.2.11.1
-rw-r--r--  1 root root  452824 2007-03-26 08:47 libcairo.so.2.11.1
-rw-r--r--  1 root root  941600 2007-03-05 01:19 libdb-4.3.so
lrwxrwxrwx  1 root root      15 2007-06-04 20:40 libdrm.so.2 -> libdrm.so.2.3.0
-rw-r--r--  1 root root   34492 2007-02-19 11:41 libdrm.so.2.3.0
lrwxrwxrwx  1 root root      13 2007-06-04 20:40 libexpat.so.0 -> libexpat.so.1
lrwxrwxrwx  1 root root      17 2007-06-04 20:40 libexpat.so.1 -> libexpat.so.1.0.0
-rw-r--r--  1 root root  126716 2007-03-05 00:32 libexpat.so.1.0.0
lrwxrwxrwx  1 root root      22 2007-06-04 20:40 libfontconfig.so.1 -> libfontconfig.so.1.2.0
-rw-r--r--  1 root root  176080 2007-01-05 13:52 libfontconfig.so.1.2.0
lrwxrwxrwx  1 root root      21 2007-06-04 20:40 libfreetype.so.6 -> libfreetype.so.6.3.10
-rw-r--r--  1 root root  434892 2006-09-19 13:52 libfreetype.so.6.3.10
-rw-r--r--  1 root root   42836 2007-03-03 04:59 libgcc_s.so.1
lrwxrwxrwx  1 root root      21 2007-06-02 16:15 libGLcore.so.1 -> libGLcore.so.1.0.9755
-rw-r--r--  1 root root 9878564 2007-05-23 17:57 libGLcore.so.1.0.9755
lrwxrwxrwx  1 root root      24 2007-06-04 20:40 libglib-2.0.so.0 -> libglib-2.0.so.0.1200.11
-rw-r--r--  1 root root  606288 2007-03-09 08:45 libglib-2.0.so.0.1200.11
lrwxrwxrwx  1 root root      17 2007-06-02 16:15 libGL.so.1 -> libGL.so.1.0.9755
-rw-r--r--  1 root root  598292 2007-05-23 17:57 libGL.so.1.0.9755
lrwxrwxrwx  1 root root      20 2007-06-04 20:40 libGLU.so.1 -> libGLU.so.1.3.060502
-rw-r--r--  1 root root  521000 2007-03-30 19:07 libGLU.so.1.3.060502
lrwxrwxrwx  1 root root      27 2007-06-04 20:40 libgmodule-2.0.so.0 -> libgmodule-2.0.so.0.1200.11
-rw-r--r--  1 root root    9828 2007-03-09 08:45 libgmodule-2.0.so.0.1200.11
lrwxrwxrwx  1 root root      27 2007-06-04 20:40 libgobject-2.0.so.0 -> libgobject-2.0.so.0.1200.11
-rw-r--r--  1 root root  237072 2007-03-09 08:45 libgobject-2.0.so.0.1200.11
lrwxrwxrwx  1 root root      27 2007-06-04 20:40 libgthread-2.0.so.0 -> libgthread-2.0.so.0.1200.11
-rw-r--r--  1 root root   14200 2007-03-09 08:45 libgthread-2.0.so.0.1200.11
lrwxrwxrwx  1 root root      15 2007-06-04 20:40 libICE.so.6 -> libICE.so.6.3.0
-rw-r--r--  1 root root   87440 2007-02-16 10:40 libICE.so.6.3.0
-rw-r--r--  1 root root     801 2007-03-05 16:54 libidn.la
lrwxrwxrwx  1 root root      17 2007-06-04 20:40 libidn.so.11 -> libidn.so.11.5.19
-rw-r--r--  1 root root  196264 2007-03-05 16:54 libidn.so.11.5.19
lrwxrwxrwx  1 root root      17 2007-06-04 20:40 libjpeg.so.62 -> libjpeg.so.62.0.0
-rw-r--r--  1 root root  121280 2006-06-19 15:05 libjpeg.so.62.0.0
lrwxrwxrwx  1 root root      17 2007-06-04 20:40 liblcms.so.1 -> liblcms.so.1.0.15
-rw-r--r--  1 root root  172496 2006-06-19 15:44 liblcms.so.1.0.15
lrwxrwxrwx  1 root root      25 2007-06-02 16:15 libnvidia-cfg.so.1 -> libnvidia-cfg.so.1.0.9755
-rw-r--r--  1 root root  106324 2007-05-23 17:57 libnvidia-cfg.so.1.0.9755
lrwxrwxrwx  1 root root      25 2007-06-02 16:15 libnvidia-tls.so.1 -> libnvidia-tls.so.1.0.9755
-rw-r--r--  1 root root    2196 2007-05-23 17:57 libnvidia-tls.so.1.0.9755
lrwxrwxrwx  1 root root      18 2007-06-04 20:40 libpng12.so.0 -> libpng12.so.0.15.0
-rw-r--r--  1 root root  139592 2006-12-20 10:01 libpng12.so.0.15.0
lrwxrwxrwx  1 root root      19 2007-06-04 20:38 libpython2.5.so.1 -> libpython2.5.so.1.0
-rw-r--r--  1 root root 1250008 2007-04-12 17:02 libpython2.5.so.1.0
lrwxrwxrwx  1 root root      14 2007-06-04 20:40 libSM.so.6 -> libSM.so.6.0.0
-rw-r--r--  1 root root   32328 2007-02-16 10:39 libSM.so.6.0.0
lrwxrwxrwx  1 root root      20 2007-06-04 20:40 libsndfile.so.1 -> libsndfile.so.1.0.16
-rw-r--r--  1 root root  358224 2007-03-05 01:44 libsndfile.so.1.0.16
lrwxrwxrwx  1 root root      18 2007-06-04 20:40 libstdc++.so.5 -> libstdc++.so.5.0.7
-rw-r--r--  1 root root  737416 2007-01-03 15:22 libstdc++.so.5.0.7
lrwxrwxrwx  1 root root      18 2007-06-04 20:40 libstdc++.so.6 -> libstdc++.so.6.0.8
-rw-r--r--  1 root root  929648 2007-03-03 05:01 libstdc++.so.6.0.8
lrwxrwxrwx  1 root root      16 2007-06-04 20:40 libtiff.so.4 -> libtiff.so.4.2.1
-rw-r--r--  1 root root  335596 2006-08-08 04:53 libtiff.so.4.2.1
lrwxrwxrwx  1 root root      19 2007-06-04 20:40 libwmf-0.2.so.7 -> libwmf-0.2.so.7.1.0
-rw-r--r--  1 root root  315892 2007-03-05 16:05 libwmf-0.2.so.7.1.0
lrwxrwxrwx  1 root root      23 2007-06-04 20:40 libwmflite-0.2.so.7 -> libwmflite-0.2.so.7.0.1
-rw-r--r--  1 root root  103460 2007-03-05 16:05 libwmflite-0.2.so.7.0.1
lrwxrwxrwx  1 root root      15 2007-06-04 20:40 libX11.so.6 -> libX11.so.6.2.0
-rw-r--r--  1 root root  986540 2007-04-02 10:59 libX11.so.6.2.0
lrwxrwxrwx  1 root root      15 2007-06-04 20:40 libXau.so.6 -> libXau.so.6.0.0
-rw-r--r--  1 root root    7356 2007-02-16 09:47 libXau.so.6.0.0
lrwxrwxrwx  1 root root      15 2007-06-04 20:40 libXaw3d.so.6 -> libXaw3d.so.6.1
-rw-r--r--  1 root root  289720 2007-03-12 12:43 libXaw3d.so.6.1
lrwxrwxrwx  1 root root      16 2007-06-04 20:40 libXaw7.so.7 -> libXaw7.so.7.0.0
-rw-r--r--  1 root root  366344 2007-02-17 06:01 libXaw7.so.7.0.0
lrwxrwxrwx  1 root root      12 2007-06-04 20:40 libXaw.so.7 -> libXaw7.so.7
lrwxrwxrwx  1 root root      15 2007-06-04 20:40 libxcb.so.1 -> libxcb.so.1.0.0
-rw-r--r--  1 root root   94484 2007-03-08 22:40 libxcb.so.1.0.0
lrwxrwxrwx  1 root root      20 2007-06-04 20:40 libxcb-xlib.so.0 -> libxcb-xlib.so.0.0.0
-rw-r--r--  1 root root    3512 2007-03-08 22:40 libxcb-xlib.so.0.0.0
lrwxrwxrwx  1 root root      17 2007-06-04 20:40 libXdmcp.so.6 -> libXdmcp.so.6.0.0
-rw-r--r--  1 root root   17080 2007-02-16 09:46 libXdmcp.so.6.0.0
lrwxrwxrwx  1 root root      16 2007-06-04 20:40 libXext.so.6 -> libXext.so.6.4.0
-rw-r--r--  1 root root   56156 2007-02-16 12:41 libXext.so.6.4.0
lrwxrwxrwx  1 root root      20 2007-06-04 20:40 libXinerama.so.1 -> libXinerama.so.1.0.0
-rw-r--r--  1 root root    6548 2006-07-07 09:02 libXinerama.so.1.0.0
lrwxrwxrwx  1 root root      14 2007-06-04 20:40 libXi.so.6 -> libXi.so.6.0.0
-rw-r--r--  1 root root   29176 2007-02-16 14:42 libXi.so.6.0.0
lrwxrwxrwx  1 root root      17 2007-06-04 20:40 libxml2.so.2 -> libxml2.so.2.6.27
-rw-r--r--  1 root root 1160712 2007-02-18 21:19 libxml2.so.2.6.27
lrwxrwxrwx  1 root root      15 2007-06-04 20:40 libXmu.so.6 -> libXmu.so.6.2.0
-rw-r--r--  1 root root   89624 2007-03-09 08:59 libXmu.so.6.2.0
lrwxrwxrwx  1 root root      16 2007-06-04 20:40 libXmuu.so.1 -> libXmuu.so.1.0.0
-rw-r--r--  1 root root   10432 2007-03-09 08:59 libXmuu.so.1.0.0
lrwxrwxrwx  1 root root      16 2007-06-04 20:40 libXpm.so.4 -> libXpm.so.4.11.0
-rw-r--r--  1 root root   63624 2007-02-16 12:42 libXpm.so.4.11.0
lrwxrwxrwx  1 root root      14 2007-06-04 20:40 libXp.so.6 -> libXp.so.6.2.0
-rw-r--r--  1 root root   27860 2007-03-05 15:49 libXp.so.6.2.0
lrwxrwxrwx  1 root root      18 2007-06-04 20:40 libXrandr.so.2 -> libXrandr.so.2.1.0
-rw-r--r--  1 root root   22136 2007-02-22 18:42 libXrandr.so.2.1.0
lrwxrwxrwx  1 root root      19 2007-06-04 20:40 libXrender.so.1 -> libXrender.so.1.3.0
-rw-r--r--  1 root root   29456 2006-12-20 07:51 libXrender.so.1.3.0
lrwxrwxrwx  1 root root      17 2007-06-04 20:40 libXTrap.so.6 -> libXTrap.so.6.4.0
-rw-r--r--  1 root root   29072 2006-07-07 14:08 libXTrap.so.6.4.0
lrwxrwxrwx  1 root root      14 2007-06-04 20:40 libXt.so.6 -> libXt.so.6.0.0
-rw-r--r--  1 root root  326500 2007-02-16 12:42 libXt.so.6.0.0
lrwxrwxrwx  1 root root      16 2007-06-04 20:40 libXtst.so.6 -> libXtst.so.6.1.0
-rw-r--r--  1 root root   17200 2006-07-07 09:00 libXtst.so.6.1.0
lrwxrwxrwx  1 root root      19 2007-06-04 20:40 libXxf86vm.so.1 -> libXxf86vm.so.1.0.0
-rw-r--r--  1 root root   16220 2006-12-20 07:46 libXxf86vm.so.1.0.0
[B]lrwxrwxrwx  1 root root      13 2007-06-04 20:43 libz.so.1 -> libz.so.1.2.3
-rw-r--r--  1 root root   78244 2007-03-05 16:00 libz.so.1.2.3[/B]
drwxr-xr-x  2 root root     128 2007-06-04 20:40 nvidia
drwxr-xr-x 21 root root    5008 2007-06-04 20:38 python2.5
drwxr-xr-x  2 root root      88 2007-04-15 07:55 security
drwxr-xr-x  2 root root     136 2007-06-02 16:15 tls
```

---

