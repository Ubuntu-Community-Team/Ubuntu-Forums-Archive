---
title: "apt-get update error"
date: 2006-09-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by nagindian on 2006-09-24
hi

i am unable to install any package and i am unable to update apt-get. i am installing in hp integrity rx2600 server 64bit.

my source code is 
#automaticalla enerated sources.list
# [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) dapper main restricted
deb [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# Ubuntu supported packages (sources, GPG key: 437D05B5)
deb-src [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) dapper universe multiverse
deb [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

# Ubuntu community supported packages (sources, GPG key: 437D05B5)
deb-src [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) dapper universe multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

i get the following error
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Get:2 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper Release.gpg [189B]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper Release.gpg
  Error reading from server - read (104 Connection reset by peer)
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Get:3 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper-updates Release.gpg [189B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper/main Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Sources
Get:4 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper/main Sources [255kB]
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
  Error reading from server - read (104 Connection reset by peer)
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources [13.7kB]
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
  Error reading from server - read (104 Connection reset by peer)
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper/main Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
  Error reading from server - read (104 Connection reset by peer)
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper/restricted Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper/universe Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper/multiverse Packages
Get:6 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper/universe Sources [975kB]
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper/universe Sources
Get:7 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper/multiverse Sources [46.6kB]
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper/multiverse Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper-updates/main Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper-updates/restricted Packages
Get:8 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper-updates/main Sources [46.3kB]
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper-updates/main Sources
Get:9 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper-updates/restricted Sources [14B]
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper-updates/restricted Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper-updates/universe Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper-updates/universe Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper-updates/multiverse Sources
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper/main Packages
  404 Not Found
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper/restricted Packages
  Error reading from server - read (104 Connection reset by peer)
Get:10 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper/main Sources [336kB]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper/main Sources
  Error reading from server - read (104 Connection reset by peer)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper/universe Packages
  404 Not Found
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper/multiverse Packages
  Error reading from server - read (104 Connection reset by peer)
Get:11 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper/universe Sources [1312kB]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper/universe Sources
  Error reading from server - read (104 Connection reset by peer)
Get:12 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper/multiverse Sources [57.5kB]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper/multiverse Sources
  Error reading from server - read (104 Connection reset by peer)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper-updates/main Packages
  404 Not Found
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper-updates/restricted Packages
  Error reading from server - read (104 Connection reset by peer)
Get:13 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper-updates/main Sources [58.4kB]
3% [13 Sources gzip 0] [Waiting for headers]                                                                     49.9kB/s 60s
gzip: stdin: not in gzip format
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper-updates/main Sources
  Sub-process gzip returned an error code (1)
Get:14 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper-updates/restricted Sources [20B]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper-updates/restricted Sources

please guide me.


Nagz

---

### Post by kick6 on 2006-09-25
this is probably obvious, but are you connected to the internet?

---

### Post by siiib on 2006-09-25
i had a dlink wireless router that caused this problem.. i upgraded the firmware and it was ok after that.. mind you it was still a POS;)

---

