---
title: "HOWTO: Run amd64 kernel on i386 install"
date: 2005-11-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by KRavEN on 2005-11-16
I got this going yesterday because I needed it and couldn't see any reason why it wouldn't work.

First question would be why?   Me, I needed it so I could do some chroot compiling on gentoo while still in my main system.  Problem is that my gentoo install is 100% 64bit.  Also I've read in quite a few places that performance of i386 under a 64bit kernel should be even better than a k7 kernel.  True?  I have no idea.  Possible but negligible from what I've seen so far.

Downsides?  Havn't seen many yet.  I play WoW under cedega using nvidia drivers.  No problem at all with it.  

Primary issue I've seen is that apt/synaptic don't like it because the architecture is not the same.  This also causes synaptic update to gripe at you because of broken packages because of having to force binutils.  

This could be fixed by editing the control file in the deb, but would have to be done each time there is a new version.  Also you won't get update notifications for any of the amd64 packages.  

Ideally the developers could add dependancy cases for this scenario in the control files of the packages below and then you could just choose the amd64 kernel under apt/synaptic like you would the k7 kernel.  That might be too easy though... :razz: 

How to do it:

The meta packages aren't required but I put them in just in case the amd64 debs get updated to have dependancy options for this scenario ;) .

First you need to go out on the repositories and get the following files:

binutils-static_2.16.1-2ubuntu7_amd64.deb --> real
linux-image-2.6.12-9-amd64-k8_2.6.12-9.23_amd64.deb --> real
linux-restricted-modules-2.6.12-9-amd64-k8_2.6.12.4-14_amd64.deb --> real
linux-image-amd64-k8_2.6.12.16_amd64.deb --> meta
linux-restricted-modules-amd64-k8_2.6.12.16_amd64 --> meta
linux-amd64-k8_2.6.12.16_amd64.deb --> meta

Now do the following commands from the directory you downloaded into:

sudo dpkg -P --force-all binutils-static_2.16.1-2ubuntu7_i386.deb
sudo dpkg -i --force-architecture binutils-static_2.16.1-2ubuntu7_amd64.deb
sudo dpkg -i --force-architecture linux-image-2.6.12-9-amd64-k8_2.6.12-9.23_amd64.deb
sudo dpkg -i --force-architecture linux-restricted-modules-2.6.12-9-amd64-k8_2.6.12.4-14_amd64.deb
sudo dpkg -i --force-architecture linux-image-amd64-k8_2.6.12.16_amd64.deb
sudo dpkg -i --force-architecture linux-restricted-modules-amd64-k8_2.6.12.16_amd64
sudo dpkg -i --force-architecture linux-amd64-k8_2.6.12.16_amd64.deb

---

### Post by KRavEN on 2005-11-19
Found a dirty hack to make the dependancy issues with nvidia-glx and linux-restricted-modules-common go away.

If you edit /var/lib/dpkg/status and do a search for Architecture: amd64 and change it to Architecture: i386 then problems will be solved.  Then just put the packages above on hold and everythign shoudl be golden.  just make sure to keep a i386 kernel installed so that if you see a new kernel come down you will know to manually update your amd64 kernel files.

---

