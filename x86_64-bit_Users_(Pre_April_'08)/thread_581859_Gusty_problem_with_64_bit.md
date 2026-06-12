---
title: "Gusty problem with 64 bit"
date: 2007-10-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by go_beep_yourself on 2007-10-19
apt-file will not install in 64 bit gusty. During the upgrade I did to Gusty, the upgrade stalled while trying to upgrade apt-file. I killed the process and the upgrade continued. Now I am trying to reinstall apt-file, and it will not reinstall. I am trying to find the source code for apt-file, so that I can compile it. The source code package is available in the repos. How can I compile a source code package?

---

### Post by johnnybirdman on 2007-10-19
will this work?
[http://packages.debian.org/unstable/admin/apt-file](http://packages.debian.org/unstable/admin/apt-file)

---

### Post by go_beep_yourself on 2007-10-19
> **johnnybirdman said:**
> will this work?
[http://packages.debian.org/unstable/admin/apt-file](http://packages.debian.org/unstable/admin/apt-file)

Yes, but I used the source code from that package instead. Here is what I did incase anyone else is having the same problem.

```
chris@ubuntu:~/Desktop$ tar -xf apt-file_2.0.8.2.tar.gz 
chris@ubuntu:~/Desktop$ cd apt-file-2.0.8.2/
chris@ubuntu:~/Desktop/apt-file-2.0.8.2$ ls
apt-file         apt-file.bash_completion  apt-file.fr.1.sgml  debian    TODO
apt-file.1       apt-file.conf             apt-file.spec       Makefile
apt-file.1.sgml  apt-file.fr.1             changelog           README
chris@ubuntu:~/Desktop/apt-file-2.0.8.2$ sudo checkinstall 
[sudo] password for chris:

checkinstall 1.6.1, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.


The package documentation directory ./doc-pak does not exist. 
Should I create a default set of package docs?  [y]: 

Preparing package documentation...OK

Please write a description for the package.
End your description with an empty line or EOF.
>> Made by Chris
>> 

*****************************************
**** Debian package creation selected ***
*****************************************

This package will be built according to these values: 

0 -  Maintainer: [ root@ubuntu ]
1 -  Summary: [ Made by Chris ]
2 -  Name:    [ apt-file ]
3 -  Version: [ 2.0.8.2 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ amd64 ]
8 -  Source location: [ apt-file-2.0.8.2 ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue: 

Installing with make install...

========================= Installation results ===========================
install -d -m 755 /usr/share/man/man1
install -m 644 apt-file.1 /usr/share/man/man1
install: setting permissions for `/usr/share/man/man1/apt-file.1': No such file or directory
install -d -m 755 /usr/bin
install -m 755 apt-file /usr/bin
install: setting permissions for `/usr/bin/apt-file': No such file or directory
install -d -m 755 /etc/apt
install -m 644 apt-file.conf /etc/apt
install: setting permissions for `/etc/apt/apt-file.conf': No such file or directory
install -d -m 755 /etc/bash_completion.d
install -m 644 apt-file.bash_completion /etc/bash_completion.d/apt-file
install: setting permissions for `/etc/bash_completion.d/apt-file': No such file or directory

======================== Installation successful ==========================

Copying documentation directory...
./
./README
./TODO
grep: /var/tmp/ZgqabnLLJDRoRZacEHWrC/newfile: No such file or directory

Copying files to the temporary directory...OK

Striping ELF binaries and libraries...OK

Compressing man pages...OK

Building file list...OK

Building Debian package...OK

Installing Debian package...OK

Erasing temporary files...OK

Deleting temp dir...OK


**********************************************************************

 Done. The new package has been installed and saved to

 /home/chris/Desktop/apt-file-2.0.8.2/apt-file_2.0.8.2-1_amd64.deb

 You can remove it from your system anytime using: 

      dpkg -r apt-file

**********************************************************************

chris@ubuntu:~/Desktop/apt-file-2.0.8.2$ 
```

After that update-manager tries to install the broken apt-file package from the repos. I stopped it from doing that by locking the installed version of apt-file in Synaptic. I did install the dependency packages for apt-file.

---

