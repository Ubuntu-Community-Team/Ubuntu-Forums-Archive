---
title: "unable to update"
date: 2018-05-17
forum: Wine
---

### Post by char1312 on 2018-05-17
Hello, I'm trying to install wine. I'm on the Ubuntu WineHQ Wiki and have been running the code its telling me to. I ran sudo apt-get update and got this. I also tried installing from the software center but it won't launch  

Hit:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic InRelease
Get:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates InRelease [83.2 kB]
Ign:3 [https://dl.winehq.org/wine-builds/ubuntu](https://dl.winehq.org/wine-builds/ubuntu) bionic InRelease
Err:4 [https://dl.winehq.org/wine-builds/ubuntu](https://dl.winehq.org/wine-builds/ubuntu) bionic Release
  404  Not Found [IP: 151.101.200.69 443]
Get:5 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease [83.2 kB]
Hit:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-backports InRelease
Reading package lists... Done                               
E: The repository 'https://dl.winehq.org/wine-builds/ubuntu bionic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

---

### Post by Holger_Gehrke on 2018-05-18
Take a look in [https://dl.winehq.org/wine-builds/ubuntu/dists](https://dl.winehq.org/wine-builds/ubuntu/dists). There is no directory for package-lists for bionic for apt to get (yet).

Holger

---

