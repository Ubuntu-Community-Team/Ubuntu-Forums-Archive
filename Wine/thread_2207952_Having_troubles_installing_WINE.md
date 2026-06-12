---
title: "Having troubles installing WINE"
date: 2014-02-25
forum: Wine
---

### Post by chaz2 on 2014-02-25
The purpose for wine for me is to install the ESO beta and its a .exe file.
 this is the terminal codes i got when i tried 
> sudo apt-get install wine

and this is what i get, > Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
The following extra packages will be installed:
  gnome-exe-thumbnailer icoutils libmpg123-0 ttf-mscorefonts-installer ttf-symbol-replacement ttf-umefont
  ttf-unfonts-core winbind wine1.2 wine1.2-gecko
Suggested packages:
  libterm-readline-gnu-perl libterm-readline-perl-perl
Recommended packages:
  winetricks wisotool
The following NEW packages will be installed:
  gnome-exe-thumbnailer icoutils libmpg123-0 ttf-mscorefonts-installer ttf-symbol-replacement ttf-umefont
  ttf-unfonts-core winbind wine wine1.2 wine1.2-gecko
0 upgraded, 11 newly installed, 0 to remove and 67 not upgraded.
Need to get 67.4MB/83.2MB of archives.
After this operation, 222MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  ttf-symbol-replacement libmpg123-0 wine1.2 wine1.2-gecko icoutils ttf-mscorefonts-installer ttf-umefont
  ttf-unfonts-core winbind wine gnome-exe-thumbnailer
Install these packages without verification [y/N]? y
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/universe ttf-symbol-replacement all 1.2.2-0ubuntu2~maverick2
  404  Not Found [IP: 91.189.88.149 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/universe libmpg123-0 i386 1.12.1-3ubuntu1
  404  Not Found [IP: 91.189.88.149 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/universe wine1.2 i386 1.2.2-0ubuntu2~maverick2
  404  Not Found [IP: 91.189.88.149 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main icoutils i386 0.29.1-0ubuntu1
  404  Not Found [IP: 91.189.88.149 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/multiverse ttf-mscorefonts-installer all 3.2ubuntu2
  404  Not Found [IP: 91.189.88.149 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/universe ttf-umefont all 416-2
  404  Not Found [IP: 91.189.88.149 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main winbind i386 2:3.5.4~dfsg-1ubuntu8.5
  404  Not Found [IP: 91.189.88.149 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/universe wine all 1.2.2-0ubuntu2~maverick2
  404  Not Found [IP: 91.189.88.149 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/universe gnome-exe-thumbnailer all 0.7-0ubuntu1
  404  Not Found [IP: 91.189.88.149 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main winbind i386 2:3.5.4~dfsg-1ubuntu8.5
  404  Not Found [IP: 91.189.91.13 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/w/wine1.2/ttf-symbol-replacement_1.2.2-0ubuntu2~maverick2_all.deb](http://archive.ubuntu.com/ubuntu/pool/universe/w/wine1.2/ttf-symbol-replacement_1.2.2-0ubuntu2~maverick2_all.deb) 404  Not Found [IP: 91.189.88.149 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/m/mpg123/libmpg123-0_1.12.1-3ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/m/mpg123/libmpg123-0_1.12.1-3ubuntu1_i386.deb) 404  Not Found [IP: 91.189.88.149 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/w/wine1.2/wine1.2_1.2.2-0ubuntu2~maverick2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/w/wine1.2/wine1.2_1.2.2-0ubuntu2~maverick2_i386.deb) 404  Not Found [IP: 91.189.88.149 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/i/icoutils/icoutils_0.29.1-0ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/i/icoutils/icoutils_0.29.1-0ubuntu1_i386.deb) 404  Not Found [IP: 91.189.88.149 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/multiverse/m/msttcorefonts/ttf-mscorefonts-installer_3.2ubuntu2_all.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/m/msttcorefonts/ttf-mscorefonts-installer_3.2ubuntu2_all.deb) 404  Not Found [IP: 91.189.88.149 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/t/ttf-umefont/ttf-umefont_416-2_all.deb](http://archive.ubuntu.com/ubuntu/pool/universe/t/ttf-umefont/ttf-umefont_416-2_all.deb) 404  Not Found [IP: 91.189.88.149 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/winbind_3.5.4~dfsg-1ubuntu8.5_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/winbind_3.5.4~dfsg-1ubuntu8.5_i386.deb) 404  Not Found [IP: 91.189.91.13 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/w/wine1.2/wine_1.2.2-0ubuntu2~maverick2_all.deb](http://archive.ubuntu.com/ubuntu/pool/universe/w/wine1.2/wine_1.2.2-0ubuntu2~maverick2_all.deb) 404  Not Found [IP: 91.189.88.149 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/g/gnome-exe-thumbnailer/gnome-exe-thumbnailer_0.7-0ubuntu1_all.deb](http://archive.ubuntu.com/ubuntu/pool/universe/g/gnome-exe-thumbnailer/gnome-exe-thumbnailer_0.7-0ubuntu1_all.deb) 404  Not Found [IP: 91.189.88.149 80]
E: Unable to fetch some archives, try running apt-get update or apt-get --fix-missing.




I have no idea what to do, maybe i can just say **** it and try and find a .zip download and do that becasue it would be easier then trying to use wine, or even attempt to install wine. lol

-chaz

---

### Post by chaz2 on 2014-02-25
After the ESO beta has downloaded, could I transfer the file to a flashdrive, place it on a Windows PC and then finish downloading it there, then transfer it back and be able to run it on my linux?

---

### Post by sffvba[e0rt on 2014-02-26
It would seem that something has gone wrong with your repositories or you are running an outdated and not supported version of Ubuntu currently.  And you won't be able to run any Windows applications if you don't have Wine installed.

---

### Post by ian-weisser on 2014-02-26
Maverick (10.10) is long past end of life. Those repositories are long gone and the 404 responses are appropriate. 
You haven't received any security updates in years.
Your upgrade path is long gone, too.

Consider preserving up your data and installing a newer (supported) release of Ubuntu.

---

### Post by Mark Phelps on 2014-02-26
The WineHQ webpage for ESO beta is not encouraging -- has a rating of Garbage for Ubuntu (meaning, it's not going to work): [http://appdb.winehq.org/objectManager.php?sClass=version&iId=29668]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=29668")

---

