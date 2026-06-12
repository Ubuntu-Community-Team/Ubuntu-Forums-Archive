---
title: "Can't install anything - please help!"
date: 2005-10-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by ryan76 on 2005-10-22
I was trying to set up a local repository and failed. So I restored my sources.list from a backup and now every time I 'apt-get install' something or open Synaptic I get this:
[I]
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-amd64_Packages) - stat (2 No such file or directory)W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_multiverse_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/unirse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_unirse_binary-amd64_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
[/I]

etc. apt-get update does not correct the problems.

I have some web work to do and can't install anything - can someone help please? I thought that maybe I altered the wrong file when I was setting up the local repository with these instructions:

[http://ubuntuforums.org/showthread.php?t=42862](http://ubuntuforums.org/showthread.php?t=42862)

---

### Post by aysiu on 2005-10-22
mirrormax backports aren't around any more.

[http://www.psychocats.net/sources.html](http://www.psychocats.net/sources.html)

---

### Post by ryan76 on 2005-10-25
Thanks for that, all systems normal.  :)

---

