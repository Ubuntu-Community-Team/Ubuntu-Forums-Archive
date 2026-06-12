---
title: "very stuck and new"
date: 2008-08-25
forum: x86 64-bit Users
---

### Post by decimater on 2008-08-25
Hi all

I'm having a lot of difficulty installing flash, following several guides I just keep getting stuck, I cannot install this ia32-libs thing, the update manager tries to install it with this error

E: /var/cache/apt/archives/ia32-libs_2.2ubuntu11_amd64.deb: short read in buffer_copy (backend dpkg-deb during `./usr/lib32/i486/libcrypto.so.0.9.8')

if I try with terminal with sudo apt-get install ia32-libs I get 

sudo apt-get install ia32-libs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  nspluginwrapper
Use 'apt-get autoremove' to remove them.
Recommended packages:
  lib32nss-mdns
The following NEW packages will be installed
  ia32-libs
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/20.9MB of archives.
After this operation, 101MB of additional disk space will be used.
(Reading database ... 95540 files and directories currently installed.)
Unpacking ia32-libs (from .../ia32-libs_2.2ubuntu11_amd64.deb) ...
lzma: Decoder error
dpkg-deb: subprocess <decompress> returned error exit status 1
dpkg: error processing /var/cache/apt/archives/ia32-libs_2.2ubuntu11_amd64.deb (--unpack):
 short read in buffer_copy (backend dpkg-deb during `./usr/lib32/i486/libcrypto.so.0.9.8')
Errors were encountered while processing:
 /var/cache/apt/archives/ia32-libs_2.2ubuntu11_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

absolutely no idea and so fed up with this after hours, linux can't all be like this surely?

---

### Post by rmtatum on 2008-08-26
There is a flash package in the ubuntu repository.

[https://help.ubuntu.com/community/RestrictedFormats/Flash](https://help.ubuntu.com/community/RestrictedFormats/Flash)

---

### Post by decimater on 2008-08-26
probably me being very new but I try and don't get further 

decimator@decimator-desktop:~$ sudo apt-get install flashplugin-nonfree
[sudo] password for decimator: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  ia32-libs nspluginwrapper
Suggested packages:
  konqueror-nsplugins libflashsupport msttcorefonts ttf-xfree86-nonfree xfs
The following NEW packages will be installed
  flashplugin-nonfree ia32-libs nspluginwrapper
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/21.0MB of archives.
After this operation, 101MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 96309 files and directories currently installed.)
Unpacking ia32-libs (from .../ia32-libs_2.2ubuntu11_amd64.deb) ...
lzma: Decoder error
dpkg-deb: subprocess <decompress> returned error exit status 1
dpkg: error processing /var/cache/apt/archives/ia32-libs_2.2ubuntu11_amd64.deb (--unpack):
 short read in buffer_copy (backend dpkg-deb during `./usr/lib32/i486/libcrypto.so.0.9.8')
Selecting previously deselected package nspluginwrapper.
Unpacking nspluginwrapper (from .../nspluginwrapper_0.9.91.5-2ubuntu2_amd64.deb) ...
Selecting previously deselected package flashplugin-nonfree.
Unpacking flashplugin-nonfree (from .../flashplugin-nonfree_9.0.124.0ubuntu2_amd64.deb) ...
Errors were encountered while processing:
 /var/cache/apt/archives/ia32-libs_2.2ubuntu11_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Kilz on 2008-08-26
Try these commands

```

sudo apt-get -f install
sudo apt-get clean
sudo apt-get install lzma
```

then try to install it again.

---

### Post by decimater on 2008-08-26
worked :)

---

