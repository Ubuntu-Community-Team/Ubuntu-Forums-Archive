---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1) during update...."
date: 2008-11-18
forum: x86 64-bit Users
---

### Post by theskunk on 2008-11-18
I've run into this several times prior, and always been able to fix it. Here is the entire code snippet:

```
sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  xulrunner-1.9
The following packages will be upgraded:
  xulrunner-1.9
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0B/8703kB of archives.
After this operation, 8192B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 104438 files and directories currently installed.)
Preparing to replace xulrunner-1.9 1.9.0.3+nobinonly-0ubuntu1 (using .../xulrunner-1.9_1.9.0.4+nobinonly-0ubuntu0.8.10.1_amd64.deb) ...
Unpacking replacement xulrunner-1.9 ...
dpkg-deb: subprocess paste killed by signal (Broken pipe)
dpkg: error processing /var/cache/apt/archives/xulrunner-1.9_1.9.0.4+nobinonly-0ubuntu0.8.10.1_amd64.deb (--unpack):
 short read in buffer_copy (backend dpkg-deb during `./usr/lib/xulrunner-1.9.0.4/libxul.so')
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 /var/cache/apt/archives/xulrunner-1.9_1.9.0.4+nobinonly-0ubuntu0.8.10.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Usually, I can correct this by:

```

sudo rm -rf /var/cache/apt/archives/*
sudo mkdir /var/cache/apt/archives/partial
sudo apt-get autoclean
sudo apt-get update
sudo apt-get upgrade

```

This has not worked this time, and seeing as this has not been a one time occurrence for me, I'd like to figure out what i'm doing wrong, or what i can correct. 

Any additional input anybody would like I'll happily provide.

---

### Post by iponeverything on 2008-11-18
your not doing anything wrong. It looks like one the binaries that dpkg is using is corrupt.

reinstall util-linux, it might fix you up.

Do a:

 ```
dpkg -l | grep util-linux
```

Use google to find and download the matching deb and use:

```
dpkg -i <package>
```

to install it.

---

