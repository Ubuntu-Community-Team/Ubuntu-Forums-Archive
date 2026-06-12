---
title: "w32codecs"
date: 2005-04-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by boxxxx117 on 2005-04-06
Any time i try to apt-get install w32codecs i get this msg

 Reading Package Lists... Done
Building Dependency Tree... Done
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_unstable_main_binary-amd64_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Package w32codecs has no installation candidate

any ideas?

---

### Post by metasyntax on 2005-04-06
the w32codecs is the the "stable/main" section of nerim IIRC.

---

### Post by boxxxx117 on 2005-04-06
Reading package lists... Done
Building dependency tree... Done
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable/main Packages (/ var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_stable_main_binary-amd64_P ackages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing/main Packages ( /var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_testing_main_binary-amd64 _Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Package w32codecs has no installation candidate

i added that one too. i run apt-get update still this

---

### Post by poofyhairguy on 2005-04-06
[QUOTE=boxxxx117]Reading package lists... Done
Building dependency tree... Done
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable/main Packages (/ var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_stable_main_binary-amd64_P ackages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing/main Packages ( /var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_testing_main_binary-amd64 _Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Package w32codecs has no installation candidate

i added that one too. i run apt-get update still this[/QUOTE]


There might not be win32codecs for the 64 bit Debian because the 64 bit Windows to pilfer them from doesn't exist yet.

---

### Post by boxxxx117 on 2005-04-06
kinda what i thought
thanx
i just d/l'd mplayer and use that for .avi and it seems to work

---

