---
title: "Amarok won't install"
date: 2008-04-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by bchen8341 on 2008-04-04
Hi, I just installed and updated Feisty on a new AMD64 machine. I tried to install Amarok, but I get the following message:

~$ sudo apt-get install vlc amarok
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  amarok: Depends: amarok-xine but it is not going to be installed
          Depends: kdelibs4c2a (>= 4:3.5.7-1) but 4:3.5.6-0ubuntu14.2 is to be installed
          Depends: libart-2.0-2 (>= 2.3.18) but 2.3.17-1 is to be installed
          Depends: libc6 (>= 2.6-1) but 2.5-0ubuntu14 is to be installed
          Depends: libfreetype6 (>= 2.3.5) but 2.2.1-5ubuntu1.1 is to be installed
          Depends: libgcc1 (>= 1:4.2.1) but 1:4.1.2-0ubuntu4 is to be installed
          Depends: libglib2.0-0 (>= 2.14.0) but 2.12.11-0ubuntu1 is to be installed
          Depends: libgpod2 but it is not installable
          Depends: libmtp6 but it is not installable
          Depends: libruby1.8 (>= 1.8.6.36) but 1.8.5-4ubuntu2.1 is to be installed
          Depends: libstdc++6 (>= 4.2.1) but 4.1.2-0ubuntu4 is to be installed
          Depends: zlib1g (>= 1:1.2.3.3.dfsg-1) but 1:1.2.3-13ubuntu4 is to be installed
E: Broken packages

I tried to install Amarok via Synaptic or the Add/Remove thing in the Applications menu, but it didn't work either. Can anyone help me?

---

### Post by bchen8341 on 2008-04-05
Nevermind, I re-installed Feisty, upgraded to Gutsy, and everything's fine now.

---

