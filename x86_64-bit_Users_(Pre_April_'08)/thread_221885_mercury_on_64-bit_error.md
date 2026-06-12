---
title: "mercury on 64-bit error"
date: 2006-07-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by Donnieboii on 2006-07-24
Hello,

I've just tried to install mercury on my 64-bit system with a 32-bit debian package and --force architecture but then i got this error while trying tu run mercury..> donnieboii@morpheus:~/Desktop$ mercury
nawk: error while loading shared libraries: libdl.so.2: cannot open shared objec t file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared obj ect file: No such file or directory
/bin/ls: error while loading shared libraries: librt.so.1: cannot open shared ob ject file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared ob ject file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared obj ect file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared ob ject file: No such file or directory
grep: error while loading shared libraries: libc.so.6: cannot open shared object  file: No such file or directory
/usr/lib/jvm/ia32-java-1.5.0-sun/jre/bin/java: error while loading shared librar ies: libpthread.so.0: cannot open shared object file: No such file or directory
donnieboii@morpheus:~/Desktop$


Does anyone know what to do??

Thanks...
Donnieboii

---

### Post by Kilz on 2006-07-24
> **Donnieboii said:**
> Hello,

I've just tried to install mercury on my 64-bit system with a 32-bit debian package and --force architecture but then i got this error while trying tu run mercury..

Does anyone know what to do??

Thanks...
Donnieboii

```
sudo apt-get install ia32-libs-sdl
```
should get rid of the libsdl error. Adding 32bit programs can be some work. [I have a page setup]("http://www.tghc.org/staticpages/index.php/32bitapplications") that explains how I do it.

---

### Post by Donnieboii on 2006-07-24
it says it has the latest version already... so thats not it... ill have a look on the site.. thanks...

---

### Post by Donnieboii on 2006-07-24
looked on the site... didn't really help.... i realy need it cause gaim is drivin me nuts...:P

thanks..
Donnieboii

---

### Post by Kilz on 2006-07-24
> **Donnieboii said:**
> looked on the site... didn't really help.... i realy need it cause gaim is drivin me nuts...:P

thanks..
Donnieboii

If the program you want to install is the Mercury is a Java-based MSN client and you are installing it from the Debian package you may run into problems. Some Debian .deb files will not work with Ubuntu. I did a search of packages for the libc.so.6 lib and it dose not exist in Ubuntu.
I have tried to download the linux installer to find out if it will work, but so far its keeps timing out.

---

### Post by Donnieboii on 2006-07-24
do you mean the link keeps timing out? cause thats what i had aswell.. i tried the torrent but that takes like 5 hours...
if it works and you've got it working let us know... i'll keep trying aswell or try from somwhere else.. 

thanks.. 
Donnieboii

---

### Post by Kilz on 2006-07-24
> **Donnieboii said:**
> do you mean the link keeps timing out? cause thats what i had aswell.. i tried the torrent but that takes like 5 hours...
if it works and you've got it working let us know... i'll keep trying aswell or try from somwhere else.. 

thanks.. 
Donnieboii

Looking into it a little more, there is a libc.so.6 in my system. In /lib32 in the main file system, yet it errors out saying it cant find it.
Have you tried gaim, at least to give you a messanger that can be used with msn untill we figure this out?

---

### Post by Donnieboii on 2006-07-25
did you find anything?? ive tried to install those libs but didnt work it said it had latest version already...

im still trying to download the bin file...

Donnieboii

---

### Post by Kilz on 2006-07-25
> **Donnieboii said:**
> did you find anything?? ive tried to install those libs but didnt work it said it had latest version already...

im still trying to download the bin file...

Donnieboii

Not yet, cant get the bin file either

---

### Post by Donnieboii on 2006-07-25
got the bin file.. gonna try it now...

---

### Post by Donnieboii on 2006-07-25
tried it in a few different ways and comes up with this error:

> donnieboii@morpheus:/usr/local/mercury$ ./1709_Linux_VM.bin
Preparing to install...
Extracting the JRE from the installer archive...
Unpacking the JRE...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...
nawk: error while loading shared libraries: libdl.so.2: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/bin/ls: error while loading shared libraries: librt.so.1: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
hostname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory

Launching installer...

grep: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/tmp/install.dir.6409/Linux/resource/jre/bin/java: error while loading shared libraries: libpthread.so.0: cannot open shared object file: No such file or directory
donnieboii@morpheus:/usr/local/mercury$


so it is something with the libs... if you find something tell us.. and ill keep u up to date with my progress..

thanks..

Donnieboii

---

### Post by Donnieboii on 2006-07-27
enyone? what could this be?

Donnieboii

---

### Post by Encryptor on 2006-09-15
I have the same error when installing aptana :(
have you found a fix?

---

### Post by patrickfromspain on 2006-09-16
why not use anti-aliased amsn? Less troubles and it's open source..

---

### Post by afterxleep on 2006-10-06
Install mozilla, then type this on a terminal and try again

```
$export MOZILLA_FIVE_HOME=/usr/lib/mozilla
```

If it does not work, try installing libswt3.1-gtk-java and j2re1.4 and go again.

```
$sudo apt-get install mozilla libswt3.1-gtk-java
```

Aptana will require the same, but there are testing .deb packages for that here.

[http://www.aptana.com/forums/viewtopic.php?t=520](http://www.aptana.com/forums/viewtopic.php?t=520)

---

### Post by FedeXX on 2006-10-10
> **Donnieboii said:**
> looked on the site... didn't really help.... i realy need it cause gaim is drivin me nuts...:P

thanks..
Donnieboii

You should search more... :) The fix is explained in many posts in the Mercury forum.

However, open a terminal and type:

```

gedit /usr/lib/mercury/Mercury
```

Search for two lines like this
```

export LD_ASSUME_KERNEL

```

and comment them out by placing an # before. Save the file, run
```

sudo mercury

```

then close it and run
```

mercury

```

and that's it ;)

---

