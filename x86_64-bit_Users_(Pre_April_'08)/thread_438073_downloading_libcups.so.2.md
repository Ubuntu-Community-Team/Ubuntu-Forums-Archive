---
title: "downloading libcups.so.2"
date: 2007-05-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by reets on 2007-05-09
Anyone know the apt-get command to force installation of the 32-bit libraries for CUPS? (file it wants is libcups.so.2)

Trying to get REALbasic 2007 going but it will only use the 32-bit libs.

---

### Post by Kilz on 2007-05-09
> **reets said:**
> Anyone know the apt-get command to force installation of the 32-bit libraries for CUPS? (file it wants is libcups.so.2)

Trying to get REALbasic 2007 going but it will only use the 32-bit libs.

I recommend not forcing any libraries. The reason is that when you force in a package it places files according to its internal file tree. What dose this mean? 
In a i386 package you have 32bit libraries in /usr/lib.
In a amd64 package you have 64bit libraries in /usr/lib and 32bit libraries in /usr/lib32
If you --force-archetecure the package the 32bit libraries may overwrite 64bit libraries and fubar your install.
What you can do is use ```
dpkg -x TheFilesName.deb
``` to extract the contents of a i386 package. It will extract its internal file tree to that folder the deb is in. Then copy the files in /usr/lib in that tree to /usr/lib32 in your file system.

---

### Post by ectospasm on 2007-05-10
Yes, but where are we supposed to get a .deb file for the 32bit libcups.so.2?  Can you download it through aptitude or something?

---

### Post by gbesso on 2007-05-10
[http://packages.ubuntulinux.org]("http://packages.ubuntulinux.org") 

libcupsys for feisty: 
[http://packages.ubuntulinux.org/feisty/libs/libcupsys2]("http://packages.ubuntulinux.org/feisty/libs/libcupsys2")
You need the i386 version, follow Kilz's instructions.

If you need other packages, or the same package for an older ubuntu release use the url at the top of my post.

---

### Post by ectospasm on 2007-05-10
Got past that shared library problem, thanks for the help.  

But I hit a new one, and I can't find on packages.ubuntulinux.org the i386 version of libcupsimage.so.2 file.  libcupsimage-dev contains a symbolic link to it, but does not contain the binary libcupsimage.so.2 file.

I feel very close now.

EDIT:  Never mind, I think I found it.

---

### Post by reets on 2007-05-13
Awesome information! Had to download around 6 files using this method but it was super easy and now it's running perfectly :D Thanx a TON!!

---

### Post by ecs_pf5 on 2007-06-15
Apologies but can someone simplify the procedure for a newbie?

hang on. think I'm getting it

[edit] just noting down here, the libraries being asked for as I go through it

1. i386 libcupsys > extract > get libcups.so.2 > place in /usr/lib32 ...great ok, next one = [libgnutls.so.13]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fg%2Fgnutls13%2Flibgnutls13_1.4.4-3build1_i386.deb&md5sum=0754ad39768923c7d9d2179a99e7cbce&arch=i386&type=main")
2. same procedure for libgnutls.so.13 (2 files - one a link to the other) ..great, next one the installer asked for = [libtasn1.so.3]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Flibt%2Flibtasn1-3%2Flibtasn1-3_0.3.6-2build1_i386.deb&md5sum=224b25006cd6d7fe955cc3cd4fe155f3&arch=i386&type=main")
3. libtasn1.so.3 taken by the installer ok (a real file and a link).. next one asked for [libgcrypt.so.11]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Flibg%2Flibgcrypt11%2Flibgcrypt11_1.2.3-2build1_i386.deb&md5sum=f61c25e232acb60707c43be7fc517422&arch=i386&type=main")
4. great, took it, (2 files again).. next one [libgpg-error.so.0]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Flibg%2Flibgpg-error%2Flibgpg-error0_1.4-2build1_i386.deb&md5sum=8a720c885fcdb5e4e7cfe77d91c9c4ae&arch=i386&type=main")

that's it, seemed to install okay after that. here's the output from the terminal

```

(process:12655): Gdk-WARNING **: locale not supported by C library

(REALbasic2007:12655): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
[RB] Unable to load plugin RBQT.rbx
[RB] Unable to load plugin RBGameInput.rbx

(REALbasic2007:12655): Gtk-WARNING **: Error loading theme icon for stock: Unable to load image-loading module: /usr/lib32/gtk-2.0/2.10.0/loaders/svg_loader.so: /usr/lib32/gtk-2.0/2.10.0/loaders/svg_loader.so: cannot open shared object file: No such file or directory

```[I]

seems[/I] to be running ok..

Yeahhh groovy... [Hello World!]("http://www.pirateshare.net/?id=12773673")

[IMG]http://img370.imageshack.us/img370/5530/screenieil1.png[/IMG]

---

### Post by Kilz on 2007-06-15
> **ecs_pf5 said:**
> Apologies but can someone simplify the procedure for a newbie?




My last post is as simple as it can be made. But to help clarify. 
On a AMD64 Ubuntu install. Libraries are in 2 seperate folders
1. /usr/lib  This is the location of the 64bit libraries on a 64bit system.
2. /usr/lib32 this is the place for 32bit libraries on a 64bit system

On a 32bit system 32bit libraries are in /usr/lib. This is why we cant force install libraries. Because if we do we can overwrite a 64bit version of the files on or system. Our 64bit system wont be able to use it and may become broken.

Next. In all the deb files is a directory tree that matches the file system on your computer. But its matched to the operating system its designed for . So in a i386 package 32bit libraries are in /usr/lib , in a AMD64 package 64bit libraries are in /usr/lib.
We can download the 32bit package. We can extract the file structure of a deb file. and copy the files into the location they go on our system. Then the 32bit application will use them and the 64bit applications will still have their own version of them.

> **ecs_pf5 said:**
> 

1. i386 libcupsys > extract > get libcups.so.2 > place in /usr/lib32 ...great ok, next one = [libgnutls.so.13](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fg%2Fgnutls13%2Flibgnutls13_1.4.4-3build1_i386.deb&md5sum=0754ad39768923c7d9d2179a99e7cbce&arch=i386&type=main)


You added things while I was typing. To answer that question, search for the package that has that file, exteract it, and copy in the files. rinse and repeat. :D

---

### Post by ecs_pf5 on 2007-06-15
Thanks very much Kilz. Sorry I'm fairly new at Linux so I have a little trouble getting my head around some of the concepts.. got it straight in my head now. I think :p

Seems to be working great, part way through, fingers crossed. Yes I'm just 'documenting as I go' sorry for confusing things back there

---

### Post by Astrodan on 2008-01-16
> **Kilz said:**
> I recommend not forcing any libraries. The reason is that when you force in a package it places files according to its internal file tree. What dose this mean? 
In a i386 package you have 32bit libraries in /usr/lib.
In a amd64 package you have 64bit libraries in /usr/lib and 32bit libraries in /usr/lib32
If you --force-archetecure the package the 32bit libraries may overwrite 64bit libraries and fubar your install.
What you can do is use ```
dpkg -x TheFilesName.deb
``` to extract the contents of a i386 package. It will extract its internal file tree to that folder the deb is in. Then copy the files in /usr/lib in that tree to /usr/lib32 in your file system.


:)  Kilz, you helped me with many of your posts.  And, I stand firmly behind your recommendations not to force things.  As a noobie, I squirrelled a few installs with some of that, and, I know the frustration which you have warned about.

This little tidbit here, installed my REALbasic download after it had reported wrong architecture on my AMD64.  It works now like a charm.  

Special thanks.  Please, please, keep helping like your are.

Dan

---

