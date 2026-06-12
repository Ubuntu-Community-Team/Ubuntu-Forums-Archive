---
title: "usplash-dev 64-bit"
date: 2009-01-30
forum: x86 64-bit Users
---

### Post by rwalkerIII on 2009-01-30
I want to change the Kubuntu boot splash screen.  I downloaded libusplash-dev but I later found an AMD64 version (I'm on x86_64) of it and so uninstalled libusplash-dev and attempted to install the .deb package for Intrepid AMD64 from [https://launchpad.net/ubuntu/intrepid/lpia/libusplash-dev/0.5.25](https://launchpad.net/ubuntu/intrepid/lpia/libusplash-dev/0.5.25).

However, that dpkg install says my version of libusplash0 is incompatible:

Unpacking libusplash-dev (from libusplash-dev_0.5.19_amd64.deb) ...
dpkg: dependency problems prevent configuration of libusplash-dev:
 libusplash-dev depends on libusplash0 (= 0.5.19); however:
  Version of libusplash0 on system is 0.5.25.
dpkg: error processing libusplash-dev (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libusplash-dev

My question is it safe to remove libusplash0 (don't want any error messages on reboot)?  And will libusplash-dev_0.5.25_lpia.deb allow me to change the Kubuntu boot splash screen?

---

