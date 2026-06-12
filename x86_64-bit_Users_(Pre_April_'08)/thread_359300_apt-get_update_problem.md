---
title: "apt-get update problem"
date: 2007-02-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by WalmartSniperLX on 2007-02-11
All of a suden when I do any apt related commands, it comes back saying it cannot reach the needed server. When I ran ```
 sudo apt-get update 
``` it spits out 

```
 Err http://us.archive.ubuntu.com dapper Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Get:1 http://security.ubuntu.com dapper-security Release.gpg [191B]
Hit http://security.ubuntu.com dapper-security Release
Err http://us.archive.ubuntu.com dapper-updates Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Hit http://security.ubuntu.com dapper-security/main Packages
Hit http://security.ubuntu.com dapper-security/restricted Packages
Hit http://security.ubuntu.com dapper-security/main Sources
Err http://us.archive.ubuntu.com dapper-backports Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Hit http://security.ubuntu.com dapper-security/restricted Sources
Hit http://security.ubuntu.com dapper-security/universe Packages
Hit http://security.ubuntu.com dapper-security/universe Sources
Ign http://us.archive.ubuntu.com dapper Release
Ign http://us.archive.ubuntu.com dapper-updates Release
Ign http://us.archive.ubuntu.com dapper-backports Release
Ign http://us.archive.ubuntu.com dapper/main Packages
Ign http://us.archive.ubuntu.com dapper/restricted Packages
Ign http://us.archive.ubuntu.com dapper/main Sources
Ign http://us.archive.ubuntu.com dapper/restricted Sources
Ign http://us.archive.ubuntu.com dapper/universe Packages
Ign http://us.archive.ubuntu.com dapper/universe Sources
Ign http://us.archive.ubuntu.com dapper-updates/main Packages
Ign http://us.archive.ubuntu.com dapper-updates/restricted Packages
Ign http://us.archive.ubuntu.com dapper-updates/main Sources
Ign http://us.archive.ubuntu.com dapper-updates/restricted Sources
Ign http://us.archive.ubuntu.com dapper-backports/main Packages
Ign http://us.archive.ubuntu.com dapper-backports/restricted Packages
Ign http://us.archive.ubuntu.com dapper-backports/universe Packages
Ign http://us.archive.ubuntu.com dapper-backports/multiverse Packages
Ign http://us.archive.ubuntu.com dapper-backports/main Sources
Ign http://us.archive.ubuntu.com dapper-backports/restricted Sources
Ign http://us.archive.ubuntu.com dapper-backports/universe Sources
Ign http://us.archive.ubuntu.com dapper-backports/multiverse Sources
Err http://us.archive.ubuntu.com dapper/main Packages
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com dapper/restricted Packages
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com dapper/main Sources
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com dapper/restricted Sources
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com dapper/universe Packages
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com dapper/universe Sources
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com dapper-updates/main Packages
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com dapper-updates/restricted Packages
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com dapper-updates/main Sources
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com dapper-updates/restricted Sources
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com dapper-backports/main Packages
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com dapper-backports/restricted Packages
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com dapper-backports/universe Packages
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com dapper-backports/multiverse Packages
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com dapper-backports/main Sources
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com dapper-backports/restricted Sources
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com dapper-backports/universe Sources
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com dapper-backports/multiverse Sources
  Could not resolve 'us.archive.ubuntu.com'
Fetched 1B in 18s (0B/s)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-amd64/Packages.gz  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-amd64/Packages.gz  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-amd64/Packages.gz  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-amd64/Packages.gz  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-amd64/Packages.gz  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-amd64/Packages.gz  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-amd64/Packages.gz  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-amd64/Packages.gz  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-amd64/Packages.gz  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/source/Sources.gz  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/source/Sources.gz  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/source/Sources.gz  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/source/Sources.gz  Could not resolve 'us.archive.ubuntu.com'
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

Here is my /etc/apt/sources.list file

```
 
deb http://us.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ dapper universe
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

```

What is wrong all of a suden?

---

### Post by tbroderick on 2007-02-11
The server is probably down.

---

### Post by btdown on 2007-02-11
I dont think its you...I think the repository is down.

---

### Post by darkROAM_1 on 2007-02-11
It must be down. I am going the alternate route, though using archive.ubuntu.com

I couldn't install cabextract so I went that route to get the deb file. 

Maybe someone has that as their repo?

---

### Post by Trippen Out on 2007-02-11
what is the alt route

---

### Post by sysarm on 2007-02-11
Seems to be ok here.  I am in the middle of an update with no problems...

---

### Post by Trippen Out on 2007-02-11
yep.. its working again guess it was the server

---

