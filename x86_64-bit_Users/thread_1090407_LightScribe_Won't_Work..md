---
title: "LightScribe Won't Work."
date: 2009-03-08
forum: x86 64-bit Users
---

### Post by aikiwolfie on 2009-03-08
Ok I've tried installing LightScribe and the following code is what I get back. I looked around at a few other threads and while a lot of people seem to be suggesting a lot of different solutions none of them seem to work across the board. Even on the same version of Ubuntu.

Does anybody have a guaranteed way to make this work?

```
lynchk@moonstone:~$ sudo apt-get install ia32-libs
[sudo] password for lynchk: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ia32-libs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.



lynchk@moonstone:~$ sudo dpkg --install --force-architecture /home/lynchk/Media/Setup/Linux/LightScribe/lightscribe-1.18.2.1-linux-2.6-intel.deb dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 236201 files and directories currently installed.)
Unpacking lightscribe (from .../lightscribe-1.18.2.1-linux-2.6-intel.deb) ...
dpkg: error processing /home/lynchk/Media/Setup/Linux/LightScribe/lightscribe-1.18.2.1-linux-2.6-intel.deb (--install):
 trying to overwrite `/usr/lib/libstdc++.so.5.0.7', which is also in package libstdc++5
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /home/lynchk/Media/Setup/Linux/LightScribe/lightscribe-1.18.2.1-linux-2.6-intel.deb



lynchk@moonstone:~$ sudo dpkg --install --force-architecture /home/lynchk/Media/Setup/Linux/LightScribe/lightscribeApplications-1.10.19.1-linux-2.6-intel.deb 
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
Selecting previously deselected package lightscribeapplications.
(Reading database ... 236201 files and directories currently installed.)
Unpacking lightscribeapplications (from .../lightscribeApplications-1.10.19.1-linux-2.6-intel.deb) ...
dpkg: dependency problems prevent configuration of lightscribeapplications:
 lightscribeapplications depends on lightscribe; however:
  Package lightscribe is not installed.
dpkg: error processing lightscribeapplications (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 lightscribeapplications
lynchk@moonstone:~$ 

```

Edit: Forgot to mention I'm using Ubuntu 8.10.

---

### Post by marcelkoopman on 2009-03-08
I dont think you should install it. It will probably mess up your system. So dont remove libstdc++5! 
Why not ask for an AMD64 version at lightscibe? There is a forum i believe.
Dont force things,  you will end up with an unstable system.

---

### Post by aikiwolfie on 2009-03-08
This is the first time I've had a problem with the --force-architecture switch. But I didn't know they had a forum. I'll look into that. Thanks.

---

