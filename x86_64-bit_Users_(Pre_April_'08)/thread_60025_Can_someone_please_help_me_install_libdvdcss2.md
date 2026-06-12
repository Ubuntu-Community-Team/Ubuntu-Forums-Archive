---
title: "Can someone please help me install libdvdcss2?"
date: 2005-08-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by ROUBOS on 2005-08-26
Hi I tried everything in UbuntuGuide and everything people in the noob section of the forum have told me, with no success :(

Is it maybe an AMD64 issue?

I try to isntall libdvdcss2 and I get this:

$ sudo apt-get install libdvdcss2

Reading package lists... Done
Building dependency tree... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate

any help??

---

### Post by DancingSun on 2005-08-26
It's not available for AMD64.

But you may make a request in [this thread](http://ubuntuforums.org/showthread.php?t=48905).

---

### Post by atrus325 on 2005-08-27
I use the AMD64 version of Ubuntu on my desktop, and I have this library installed.. just do so manually.  It works without a hitch.

---

### Post by ROUBOS on 2005-08-27
only if I knew how to do it manualy... noob here  :|

---

### Post by tseliot on 2005-08-27
Try my guide please, and tell me if it works for you.

[http://ubuntuforums.org/showthread.php?t=54399](http://ubuntuforums.org/showthread.php?t=54399)

If you've got any questions, please ask them there.

---

### Post by earthfall on 2005-08-27
* how to build your own libdvdcss package

1. install libdvdread3 package (sudo apt-get install libdvdread3)
2. run install-css.sh script (sudo /usr/share/doc/libdvdread3/examples/install-css.sh)
3. just press enter and wait until it finished
4. check for the /tmp/dvd directory ( ls -asl /tmp/dvd/*.deb)
5. install the libdvdcss2_*.deb package (sudo apt-get install /tmp/dvd/*.deb)

---

### Post by jon_gunnar on 2005-08-27
[QUOTE=ROUBOS]only if I knew how to do it manualy... noob here  :|[/QUOTE]
Tried this?

cat /usr/share/doc/libdvdread3/examples/install-css.sh

To show what it does. And then

sudo /usr/share/doc/libdvdread3/examples/install-css.sh

If not I have built working packages.
libdvdcss2_1.2.5-1_amd64.deb and libdvdcss2-dev_1.2.5-1_amd64.deb

--edit
Built packages for 5.10 RC1 AMD64 today.

---

### Post by ROUBOS on 2005-08-27
I tried that,
the only files in /tmp/dvd/ are:
libdvdcss_1.2.5-1.diff.gz
libdvdcss_1.2.5.orig.tar.gz

---

### Post by ROUBOS on 2005-08-27
>>>  tseliot

I tried your howto, but when I try on untar the file I get an error

---

### Post by Corbelius on 2005-08-27
I create the .deb package for the Tamir's repository, stay tuned ;)

---

### Post by Corbelius on 2005-08-28
double post

---

### Post by lrnzcpmn on 2005-08-28
*I have a amd 64 and I installed libdvdcss2 by adding these sources:* 
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main
*and then in console* : sudo gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 1F41B907
sudo gpg --armor --export 1F41B907 | sudo apt-key add -
[I]and then apt-get update and run synaptic
I must say I've read to not use the marillat repos. but this the only place I've found a working libdvdcss2.
hope it helps[/I]

---

### Post by Tamir on 2005-08-29
[QUOTE=lrnzcpmn]*I have a amd 64 and I installed libdvdcss2 by adding these sources:* 
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main
*and then in console* : sudo gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 1F41B907
sudo gpg --armor --export 1F41B907 | sudo apt-key add -
[I]and then apt-get update and run synaptic
I must say I've read to not use the marillat repos. but this the only place I've found a working libdvdcss2.
hope it helps[/I][/QUOTE]
 Everyone can add our repositories, and it install from the repositories (for ubuntu64)
[http://ubuntuforums.org/showthread.php?t=48905](http://ubuntuforums.org/showthread.php?t=48905)

---

### Post by ROUBOS on 2005-08-29
THANK YOU VERY MUCH.
It all worked out and libdvdcss2 is now installed and DVDs that wouldn't work with Xine now do.

Thanks alot.
I'm a happy man...  \\:D/

---

