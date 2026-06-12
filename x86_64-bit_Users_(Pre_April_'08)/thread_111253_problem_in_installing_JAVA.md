---
title: "problem in installing JAVA"
date: 2006-01-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by hadian on 2006-01-01
i installed ubuntu on a AMD64 (dual core). then updated and upgraded it. 
i want to install java and first i did this:

root@ubuntu:/home/reza# apt-get install java-package java-common
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package java-package
root@ubuntu:/home/reza#

and this is my source.list file which i uncommented the addresses:
```
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release amd64 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
deb http://ir.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://ir.archive.ubuntu.com/ubuntu breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://ir.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://ir.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ir.archive.ubuntu.com/ubuntu breezy universe
deb-src http://ir.archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ir.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb-src http://ir.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

```

is the problem with introducing the repositories or something else?
Thanks in advance!

---

### Post by kaamos on 2006-01-01
Try adding this repository
> deb [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy free non-free
and then use these command in terminal
```
sudo apt-get update
```
and to install java
```
sudo apt-get install sun-j2re1.5
```
Hope this helps!

---

### Post by bmk789 on 2006-01-02
[QUOTE=kaamos]Try adding this repository

and then use these command in terminal
```
sudo apt-get update
```
and to install java
```
sudo apt-get install sun-j2re1.5
```
Hope this helps![/QUOTE]
Repository cannot be contacted.

---

### Post by hadian on 2006-01-03
[QUOTE=kaamos]Try adding this repository

and then use these command in terminal
```
sudo apt-get update
```
and to install java
```
sudo apt-get install sun-j2re1.5
```
Hope this helps![/QUOTE]

unfortunately it does not work. there are nothing in the 
[http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/free/binary-amd64/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/free/binary-amd64/)
or 
[http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/non-free/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/non-free/) 
for AMD64.

it seems the the pakages for AMD64 are not ready.

is it possible to use the packages for i386 on ubuntu amd64?

---

### Post by FluffyElmo on 2006-01-03
Why not just download and install from Sun? probably less trouble overall than messing with repositories. Just download the amd64 version from [http://java.sun.com]("http://java.sun.com"), make it executable, run the installer and link java to your path. 

For instance, to install the 1.5 jdk go to the location you downloaded to and:
```

chmod 777 jdk-1_5_0_06-linux-amd64.bin
./jdk-1_5_0_06-linux-amd64.bin
sudo rm /usr/bin/java
sudo ln -s /installpath/jdk1.5.0_06/bin/java /usr/bin/java
sudo ln -s /installpath/jdk1.5.0_06/bin/javac /usr/bin/javac

```

Note that getting a browser plug-in working is rather more complex...but for desktop Java apps like Azureus and Eclipse this works fine for me. Also if you want to install outside your home directory you should use *sudo  /jdk-1_5_0_06-linux-amd64.bin*

I also have JRockit and various Sun JDK versions installed this way and it makes it pretty easy to switch versions for testing.

---

