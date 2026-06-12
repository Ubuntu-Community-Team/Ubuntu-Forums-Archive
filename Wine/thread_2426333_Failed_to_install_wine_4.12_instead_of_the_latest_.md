---
title: "Failed to install wine 4.12 instead of the latest one on Ubuntu 18.04"
date: 2019-09-07
forum: Wine
---

### Post by larege2002 on 2019-09-07
Hi,

We are developing a custom application on 64Bit in Windows and we need to run it in Ubuntu 18.04
With wine 4.12 our application worked. The wineprefix used was 64.

With wine 4.15 the same application (no changes were done in the code) is not working anymore.
How can I downgrade from wine-devel 4.15 to wine-devel 4.12?

Thank you,
Lavinia

---

### Post by Xian on 2019-09-07
You could just go direct to the repo to download & install the version you want:

[https://dl.winehq.org/wine-builds/ubuntu/dists/bionic/main/binary-amd64/](https://dl.winehq.org/wine-builds/ubuntu/dists/bionic/main/binary-amd64/)

Read this as well regarding wine-devel 4.15: [http://ubuntuhandbook.org/index.php/2019/09/wine-4-15-released-with-initial-http-service-implementation/](http://ubuntuhandbook.org/index.php/2019/09/wine-4-15-released-with-initial-http-service-implementation/)

Or you can use apt to do this for you. 
See what versions are available in the repo:

```
# apt-cache policy wine-devel
```

For example with the program apache2:

```
# apt-cache policy apache2
apache2:
  Installed: (none)
  Candidate: 2.4.38-2ubuntu2.2
  Version table:
     2.4.38-2ubuntu2.2 500
        500 http://archive.ubuntu.com/ubuntu disco-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu disco-security/main amd64 Packages
     2.4.38-2ubuntu2 500
        500 http://archive.ubuntu.com/ubuntu disco/main amd64 Packages
```

Install the version you want:
```
# apt-get install apache2=2.4.38-2ubuntu2.2
```

If you don't want newer versions to be installed on updates, pin the package:

```
# apt-mark hold wine-devel
```

---

### Post by CatKiller on 2019-09-07
As well as getting the earlier version installed for your own needs it would be nice to start a dialogue with the Wine devs to identify what it is that the application you're writing does that causes problems with the later version. Since it's your own application you are uniquely placed to find the regression.

---

