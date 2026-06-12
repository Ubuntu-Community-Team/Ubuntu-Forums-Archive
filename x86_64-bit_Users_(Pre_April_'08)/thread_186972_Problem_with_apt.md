---
title: "Problem with apt"
date: 2006-06-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by lloydsmart on 2006-06-02
Hi. I recently upgraded from 64-bit breezy to 64-bit dapper. Loving it so far, except for one problem - apt and Synaptic are being a bitch.

Here's the output I get from *sudo apt-get update*:

```
Ign http://security.ubuntu.com dapper-security Release.gpg
Ign http://gb.archive.ubuntu.com dapper Release.gpg
Ign http://gb.archive.ubuntu.com dapper-updates Release.gpg
Ign http://gb.archive.ubuntu.com dapper-backports Release.gpg
Ign http://security.ubuntu.com dapper-security Release
Ign http://gb.archive.ubuntu.com dapper Release
Ign http://gb.archive.ubuntu.com dapper-updates Release
Ign http://security.ubuntu.com dapper-security/main Packages
Ign http://gb.archive.ubuntu.com dapper-backports Release
Ign http://security.ubuntu.com dapper-security/restricted Packages
Ign http://security.ubuntu.com dapper-security/universe Packages
Ign http://gb.archive.ubuntu.com dapper/main Packages
Ign http://gb.archive.ubuntu.com dapper/restricted Packages
Ign http://gb.archive.ubuntu.com dapper/universe Packages
Ign http://gb.archive.ubuntu.com dapper/multiverse Packages
Ign http://gb.archive.ubuntu.com dapper/universe Packages
Errhttp://security.ubuntu.com dapper-security/main Packages
  302 Found
Ign http://gb.archive.ubuntu.com dapper-updates/main Packages
Ign http://gb.archive.ubuntu.com dapper-updates/restricted Packages
Ign http://gb.archive.ubuntu.com dapper-backports/main Packages
Ign http://gb.archive.ubuntu.com dapper-backports/restricted Packages
Ign http://gb.archive.ubuntu.com dapper-backports/universe Packages
Ign http://gb.archive.ubuntu.com dapper-backports/multiverse Packages
Errhttp://gb.archive.ubuntu.com dapper/main Packages
  302 Found [IP: 85.133.25.7 80]
Errhttp://security.ubuntu.com dapper-security/restricted Packages
  302 Found
Errhttp://gb.archive.ubuntu.com dapper/restricted Packages
  302 Found [IP: 85.133.25.7 80]
Errhttp://gb.archive.ubuntu.com dapper/universe Packages
  302 Found [IP: 85.133.25.7 80]
Errhttp://gb.archive.ubuntu.com dapper/multiverse Packages
  302 Found [IP: 85.133.25.7 80]
Errhttp://gb.archive.ubuntu.com dapper/universe Packages
  302 Found [IP: 85.133.25.7 80]
Errhttp://gb.archive.ubuntu.com dapper-updates/main Packages
  302 Found [IP: 85.133.25.7 80]
Errhttp://gb.archive.ubuntu.com dapper-updates/restricted Packages
  302 Found [IP: 85.133.25.7 80]
Errhttp://gb.archive.ubuntu.com dapper-backports/main Packages
  302 Found [IP: 85.133.25.7 80]
Errhttp://gb.archive.ubuntu.com dapper-backports/restricted Packages
  302 Found [IP: 85.133.25.7 80]
Errhttp://gb.archive.ubuntu.com dapper-backports/universe Packages
  302 Found [IP: 85.133.25.7 80]
Errhttp://gb.archive.ubuntu.com dapper-backports/multiverse Packages
  302 Found [IP: 85.133.25.7 80]
Errhttp://security.ubuntu.com dapper-security/universe Packages
  302 Found
Reading package lists...

```

Synaptic mostly works, except I get the following error when I click "Reload":
```
Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

http://gb.archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-amd64/Packages.bz2: Sub-process bzip2 returned an error code (2)
```

Can anyone help? This is REALLY starting to annoy me - I can't even install the nVidia drivers! ](*,) 

I'm behind a University proxy, if that makes any difference, but I think I've set it up correctly. It's a HTTP proxy with authentication. Web browsing works, and I can use apt/synaptic sometimes (for some repositories), so it's not a problem with internet access.

Here's my sources.list, if that helps:
```

deb http://gb.archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
# deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu/ dapper universe
# deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
# deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe

```

Thanks in advance for your help.

---

### Post by lloydsmart on 2006-06-02
Never mind - question got answered on LinuxQuestions.org. Absolutely awesome forum.

In case anyone else had the same problem as me, here is the thread that helped me out:

[http://www.linuxquestions.org/questions/showthread.php?p=2275145&posted=1#post2275145]("http://www.linuxquestions.org/questions/showthread.php?p=2275145&posted=1#post2275145")

:D :D :D :D :D 8)

---

### Post by decide on 2006-06-03
[QUOTE=lloydsmart]Never mind - question got answered on LinuxQuestions.org. Absolutely awesome forum.

In case anyone else had the same problem as me, here is the thread that helped me out:

[http://www.linuxquestions.org/questions/showthread.php?p=2275145&posted=1#post2275145]("http://www.linuxquestions.org/questions/showthread.php?p=2275145&posted=1#post2275145")

:D :D :D :D :D 8)[/QUOTE]

I'm having a similar (I believe nearly the same... I just installed Ubuntu Dapper yesterday, my 3rd distro, first time not getting frustrated immediately after install and i'm really trying to keep it as my main OS) problems as you.  I copied the sources.list from the link, and i'm getting the following error in Synaptic:

**Could not download all repository indexes**
The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.
[http://mirror2.ubuntulinux.nl/dists/dapper-seveas/all/binary-amd64/Packages.gz:](http://mirror2.ubuntulinux.nl/dists/dapper-seveas/all/binary-amd64/Packages.gz:) 404 Not Found

It's the same error i've been getting with I believe [I]all[I] non-Ubuntu official indexes.  Being a brand new user, I have no idea what to do, or if it's just my computer or what.  Any help would be appreciated!

---

### Post by decide on 2006-06-03
whoops!  forgot something!

it also gave me this error:

W: GPG error: [http://mirror2.ubuntulinux.nl](http://mirror2.ubuntulinux.nl) dapper-seveas Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 49A120FD1135D466

Thanks!

---

### Post by fromluxembourg on 2006-06-06
SORRY TO BOTHER .. I FOUND THE PROBLEM: I HAVE SET A WRONG PROXY .. NOW IT SEEMS TO WORK PROPERLY
===========================

Hi all! I'm new in the forum!

I just updated my AMD-64 from Ubuntu 5.1 to Dapper 6.06 but I got some problems with X after the first reboot due probably to some packages not uploaded on my system. I friend of mine aided me and we succeded, such that X works fine now, but finally I got a lot of problems with apt-get (synaptic) as I'm not more able to update my OS and even more I dont have anymore Latex and OpenOffice!  
I get always the message: Could not resolve ‘rtsp’ , eg:

[http://it.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg](http://it.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg): Could not resolve ‘rtsp’

what does it means? Is apt-get trying to get the packages through the RTSP protocol, that sounds strange ... I tried to generate the sources.list from [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic) but even that didn't work (I didn't succeded downloading the PGP Keys).

Someone has an idea how to solve that problem?

Thanks in advance for advice

---

