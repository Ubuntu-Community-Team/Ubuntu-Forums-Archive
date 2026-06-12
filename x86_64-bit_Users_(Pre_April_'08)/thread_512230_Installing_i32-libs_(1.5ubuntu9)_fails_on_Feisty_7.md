---
title: "Installing i32-libs (1.5ubuntu9) fails on Feisty 7.04 AMD64 server"
date: 2007-07-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by davidkahn on 2007-07-28
sudo apt-get install ia32-libs returns the following error:

Unpacking ia32-libs (from .../ia32-libs_1.5ubuntu9_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/ia32-libs_1.5ubuntu9_amd64.deb (--unpack):
 unable to create `./usr/lib32/libGL.so.1.2': No such file or directory
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/ia32-libs_1.5ubuntu9_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

I have previously successfully installed a 32-bit chroot environment using the procedure at [https://help.ubuntu.com/community/DebootstrapChroot](https://help.ubuntu.com/community/DebootstrapChroot), and am thinking that this might be what's preventing ia32-libs from installing.

---

### Post by Kilz on 2007-07-29
/usr/lib32/libGL.so.1.2 has something to do with video drivers, since its a serve, do you even have a desktop installed? Are you sure the package didnt install even with the error?

---

