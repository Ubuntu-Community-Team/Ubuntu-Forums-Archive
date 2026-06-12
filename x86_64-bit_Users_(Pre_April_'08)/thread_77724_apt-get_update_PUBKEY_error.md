---
title: "apt-get update PUBKEY error"
date: 2005-10-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by shibasu on 2005-10-17
When trying to run

 sudo apt-get update.


:~$ sudo apt-get update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release [19.6kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release.gpg [189B]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Sources
Fetched 19.8kB in 1s (19.4kB/s)
Reading package lists... Done
shibasu@mu14:~$ sudo gedit /etc/apt/sources.list
shibasu@mu14:~$ sudo apt-get update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release.gpg [189B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Get:4 [ftp://ftp.nerim.net](ftp://ftp.nerim.net) etch Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Sources
Get:5 [ftp://ftp.nerim.net](ftp://ftp.nerim.net) etch Release [2864B]
Ign [ftp://ftp.nerim.net](ftp://ftp.nerim.net) etch Release
Get:6 [ftp://ftp.nerim.net](ftp://ftp.nerim.net) etch/main Packages [1690B]
Fetched 4746B in 2s (1884B/s)
Reading package lists... Done
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) etch Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: You may want to run apt-get update to correct these problems

"sudo gedit /etc/apt/sources.list

When Gedit appears, enter the following line, then save and close gedit:

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) etch main" - Extract from RestrictedFormats. 

The issue lies in this. 

I run sudo gedit ***  then copy and past the deb ftp *** into the .list save, close, and run the update. when I do such it gives me that PUBKEY error.

This causes the win32codecs that i'm trying to install via

sudo get-apt install win32codecs to not exist. (Probably becouse they did not download *obvious statment aye*) 


Anyway, a bit wordy, but I wanted to get all possible info. Any suggestions?



EDIT: I can run the Codec needy Media files in Xine. Totem seems to be unable to find the codec files as per where HOWTO:WinCodec32's instructions. Perhaps i'm just setting something up wrong. Ohh well, I got it working. If anyone has the same problems as me I suggest trying the file in XINE

---

