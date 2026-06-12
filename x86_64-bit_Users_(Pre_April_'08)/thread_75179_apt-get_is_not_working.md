---
title: "apt-get is not working"
date: 2005-10-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by vtec on 2005-10-13
Just noticed that my apt-get update is giving me errors. Does that have somthing to do with the new release today???

---

### Post by aysiu on 2005-10-13
If you post the errors, that may help others solve your problem.

---

### Post by vtec on 2005-10-13
sudo apt-get update                                          [~ 1067]
Password:
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release [30.9kB]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages [80.2kB]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Sources [46.9kB]
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release [19.6kB]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages [14B]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages [14B]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources [14B]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources [14B]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages [14B]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources [14B]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release.gpg
  Could not connect to us.archive.ubuntu.com:80 (82.211.81.151), connection timed out
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release.gpg [189B]
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release [19.6kB]
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages [2303B]
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages [14B]
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Sources [622B]
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Sources [14B]
Fetched 201kB in 8m29s (394B/s)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg)  Could not connect to us.archive.ubuntu.com:80 (82.211.81.151), connection timed out
Reading package lists... Done
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-amd64_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by grsing on 2005-10-13
I'm having the same problem, with the same errors.  Not sure what is causing it.

---

### Post by InsomniacUK on 2005-10-13
The servers are just busy I reckon. Everyone is trying to upgrade.

---

### Post by vtec on 2005-10-13
I had a feeling it was somthing like that, or that changes were still being made.

---

### Post by occularrifts on 2005-10-13
I thought my network card was screwy at first, [I had some problems it during install]  but it appears the servers are just getting hammered.

Hopefully it will settle down within a few hours

---

### Post by Stereotypical Rage on 2005-10-13
People are going nuts over Ubuntu.:p

---

### Post by jvictor on 2005-11-03
I presume that you may be using DSL Routers which are not supporting IPv6 well. And ubuntu uses ipv6 by default. The soln may be

1) Disable IPV6 on ubuntu
2) Use ur ISPs DNS server in /etc/resolv.conf

I'd similar issues and got it right by doing these, now Ubuntu is rock solid and stable :)

---

### Post by tamskp on 2005-11-07
I'm having similar problems - kind of figured that I need to disable ipv6, but how do i do that?!

Have searched on the forums, but have been trawling through for a while and not found anything that I can actually use yet.

---

