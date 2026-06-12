---
title: "Jashaka install help needed"
date: 2007-06-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by willsomebody on 2007-06-22
I once installed jahshaka on 32- bit feisty using the dapper repo posted here [http://www.jahshaka.org/content/view/112/]("http://www.jahshaka.org/content/view/112/"), but when I added that in 64- bit feisty, jahshaka did not return any packages in a search. Would the 32-bit application work in 64-bit ubuntu? And if so does anyone know how to make synaptic (or apt or aptitude) show this program?


I am usig an AMD athlon 64 x2 3600+ with 1 gig of pny ram and a 160 gig WD sata harddrive.

---

### Post by Cappy on 2007-06-23
[http://sourceforge.net/project/downloading.php?groupname=jahshaka&filename=jahshaka-dapper-x86.sh&use_mirror=superb-west](http://sourceforge.net/project/downloading.php?groupname=jahshaka&filename=jahshaka-dapper-x86.sh&use_mirror=superb-west)

You'll have to change to its directory, probably the Desktop
```
cd ~/Desktop
```
and
```
sudo dpkg --force-architecture -i jahshaka-dapper-x86.sh
```

---

### Post by willsomebody on 2007-06-23
Thanks for the response, but unfortunately, it didn't work. It gave the following error:

[INDENT]~/Desktop$ sudo dpkg --force-architecture -i jahshaka-dapper-x86.sh
Password:
Sorry, try again.
Password:
dpkg-deb: `jahshaka-dapper-x86.sh' is not a debian format archive
dpkg: error processing jahshaka-dapper-x86.sh (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 jahshaka-dapper-x86.sh
[/INDENT]

---

### Post by willsomebody on 2007-06-23
I clicked the dapper link on this page [http://www.jahshaka.org/content/view/112/]("http://www.jahshaka.org/content/view/112/") and it brought up an ftp site with a jahshaka.deb file.  I did my best to install its dependencies through synaptic and the other .deb files on that ftp site, but I still get errors:

[INDENT]~/Desktop$ sudo dpkg --force-architecture -i jahshaka_2.0rc3_i386.deb
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 223288 files and directories currently installed.)
Preparing to replace jahshaka 2.0rc3 (using jahshaka_2.0rc3_i386.deb) ...
Unpacking replacement jahshaka ...
dpkg: dependency problems prevent configuration of jahshaka:
 jahshaka depends on openlibraries; however:
  Package openlibraries is not configured yet.
 jahshaka depends on libopenal0; however:
  Package libopenal0 is not installed.
 jahshaka depends on openlibraries; however:
  Package openlibraries is not configured yet.
dpkg: error processing jahshaka (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 jahshaka[/INDENT]

It says that libopenal0 is not installed, when, in fact it is.  It says that openlibraries is not configured, and I have no idea how to do that.

---

### Post by Cappy on 2007-06-23
That should have been ```
sudo sh jahshaka-dapper-x86.sh
``` =(

The problem is that you need 32-bit versions of those things. That looks like a mess. I would probably --force-all and probably solve the the dependencies using [http://packages.ubuntu.com](http://packages.ubuntu.com) or getdebs: [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

If you use package.ubuntu.com you'll have to extract each like
```
dpkg -x packagename.deb folder_to_extract_to
```
and then copy like so:
```
sudo cp -R folder_to_extract_to/usr/lib/* /usr/lib32/
```

---

### Post by willsomebody on 2007-06-23
I have tried to install libopenal0 both ways, but dpkg keeps saying it is not installed.  As for openlibraries, it is installed, but it is just not configured and I don't know how to configure it.

---

### Post by willsomebody on 2007-06-23
Through random trial and error, I have solved the openlibraries dependency, but the libopenal0 is still a problem.  I have discovered that I actually have libopenal0a installed through synaptic, but this may be the same.  I have found some 32-bit rpm's for just libopenal0, bit alien refuses to convert them.

Any help at all would be appreciated.

---

### Post by willsomebody on 2007-06-23
I found a libopenal0 .deb on an ubuntu package search, but none of the mirrors I clicked actually had it, so I just started clicking them from the top of the list until I got to one that had it.  I installed it and jahshaka installed.  Now I get this when I try to use it:


~/Desktop$ jahshaka
jahshaka.bin: error while loading shared libraries: libmlt.so.0.2.1: cannot open shared object file: Error 40

---

### Post by Cappy on 2007-06-23
**$ apt-cache search libmlt**
libmlt-dev - An open source multimedia framework - Development files
libmlt0.2.2 - An open source multimedia framework - Core files
libmlt0.2.2-data - An open source multimedia framework - Core files

[http://packages.ubuntu.com/feisty/libs/libmlt0.2.2-data](http://packages.ubuntu.com/feisty/libs/libmlt0.2.2-data)
[http://packages.ubuntu.com/feisty/libs/libmlt0.2.2](http://packages.ubuntu.com/feisty/libs/libmlt0.2.2)

The -data is arch independent so you can just install it but you'll have to manually extract and move the other package.

---

### Post by willsomebody on 2007-06-24
I did as you said and I now get this error:


[INDENT]jahshaka.bin: error while loading shared libraries: libmlt++.so.0.2.1: cannot open shared object file: No such file or directory[/INDENT]

---

### Post by kurageart on 2008-03-14
jashaka is incredible software... 
just go here 
[http://jahshaka.org/forum/guide-compile-ubuntu-gutsy-amd64-t1604.html](http://jahshaka.org/forum/guide-compile-ubuntu-gutsy-amd64-t1604.html)

---

