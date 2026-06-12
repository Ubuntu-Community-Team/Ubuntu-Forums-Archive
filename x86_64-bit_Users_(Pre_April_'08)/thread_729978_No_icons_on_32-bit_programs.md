---
title: "No icons on 32-bit programs?"
date: 2008-03-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by rev_b on 2008-03-20
I'm not sure if it's a Hardy Heron issue or a x86-64 issue, but when starting 32-bit apps (realplayer, 32-bit firefox) they work fine, but there is no icons on app buttons??
Here's an example.
Any ideas? 

[IMG]http://img508.imageshack.us/img508/3848/48585726fq1.jpg[/IMG]

---

### Post by dazedx on 2008-03-20
I've been having the exact same issue. Although the applications are not 32-bit, but they are lunched via 32-bit firefox. If i run totem, it runs fine, if its launched because i'm downloading a video or mp3, using firefox32 the icons are gone. 

If i avoid using 32bit anything, and keep my browser completely 64-bit, i don't have the issue

---

### Post by Cappy on 2008-03-21
> **rev_b said:**
> I'm not sure if it's a Hardy Heron issue or a x86-64 issue, but when starting 32-bit apps (realplayer, 32-bit firefox) they work fine, but there is no icons on app buttons??
Here's an example.
Any ideas? 

[IMG]http://img508.imageshack.us/img508/3848/48585726fq1.jpg[/IMG]

Launch the application in the terminal and it may give an error.

It looks like it may be a 32-bit QT or GTK library missing in Hardy. This guy had the same exact issue and wasn't able to fix it:
[http://ubuntuforums.org/showthread.php?t=474790&page=14#137](http://ubuntuforums.org/showthread.php?t=474790&page=14#137)

```
sudo apt-get install libgtk2.0-0 libqt4-core libqt4-gui
```

---

### Post by rev_b on 2008-03-21
> **Cappy said:**
> Launch the application in the terminal and it may give an error.

It looks like it may be a 32-bit QT or GTK library missing in Hardy. This guy had the same exact issue and wasn't able to fix it:
[http://ubuntuforums.org/showthread.php?t=474790&page=14#137](http://ubuntuforums.org/showthread.php?t=474790&page=14#137)

```
sudo apt-get install libgtk2.0-0 libqt4-core libqt4-gui
```

Installing those libs didn't help.

I get several error messages (one for each icon, I guess) on the terminal:

> (firefox-bin:6995): Gtk-WARNING **: Error loading theme icon 'gtk-stop' for stock: Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so: /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so: wrong ELF class: ELFCLASS64

---

### Post by Cappy on 2008-03-21
For that error, install getlibs ( [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790) ) and use
```
getlibs -p librsvg2-common librsvg2 libgsf libcroco3
```
The last two came from a bug report I just found on your problem: 
[https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/162993](https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/162993)
and
[https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/202448](https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/202448)

You could also use
```
getlibs -l svg_loader.so
```
which would match librsvg2-common

This "image-loading module" is hopefully the culprit!

---

### Post by rev_b on 2008-03-21
> **Cappy said:**
> For that error, install getlibs ( [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790) ) and use
```
getlibs -p librsvg2-common librsvg2 libgsf libcroco3
```
The last two came from a bug report I just found on your problem: 
[https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/162993](https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/162993)
and
[https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/202448](https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/202448)

You could also use
```
getlibs -l svg_loader.so
```
which would match librsvg2-common

This "image-loading module" is hopefully the culprit!

Thank you for your help, but it still doesn't work.

---

### Post by Cappy on 2008-03-21
Looking at those launchpad links, the only solutions it mentions are downgrading gtk or moving/removing the 64-bit gtk so it won't find it.

---

### Post by sawjew on 2008-04-15
same problem here.  Any solutions?

---

### Post by jonthysell on 2008-05-15
I had this problem with gens (32-bit sega emulator) not loading svg icons on 64bit Gutsy.

You need the following 32-bit libraries for svg icons to work: librsvg2-common, librsvg2-2, libgsf-1-114, libcroco3

Here's what I did:

Install getlibs from: [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

To install all of them in one go*:

```
getlibs -p librsvg2-common librsvg2-2 libgsf-1-114 libcroco3
```

* This should work, otherwise, just run your program from the command line, and look at the names of the libraries it's missing, then run:

```
getlibs -l libraryname
```

Try the program again: if it asks from more libraries, run the above command again with the new library. Repeat until no more errors (or the icons show!)

For example in gens, I read the errors and installed the libraries one at a time with:

```
getlibs -l svg_loader.so
getlibs -l librsvg-2.so.2
getlibs -l libgsf-1.so.114
getlibs -l libcroco-0.6.so.3
```

Be happy!

---

