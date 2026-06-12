---
title: "Software index is broken"
date: 2007-08-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by phidia on 2007-08-17
running gutsy tribe 4-i would post there but since this appears to be a 64 bit issue i'm trying here 1st.

After the updates of today (8-17-07) from package manager i get this:
> Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.
After entering that command and my password i get this:
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libmtp6
The following NEW packages will be installed:
  libmtp6
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/103kB of archives.
After unpacking 352kB of additional disk space will be used.
Do you want to continue [Y/n]? 
(Reading database ... 125275 files and directories currently installed.)
Unpacking libmtp6 (from .../libmtp6_0.2.1-0ubuntu2_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libmtp6_0.2.1-0ubuntu2_amd64.deb (--unpack):
 trying to overwrite `/etc/udev/rules.d/libmtp.rules', which is also in package libmtp5
Errors were encountered while processing:
 /var/cache/apt/archives/libmtp6_0.2.1-0ubuntu2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Any ideas?

(if this should be in the gutsy forum-i apologize-have a mod move it)

---

### Post by phidia on 2007-08-17
Solved. For anyone else with this issue I followed the work-around [here]("http://ubuntuforums.org/showthread.php?t=528131").

---

