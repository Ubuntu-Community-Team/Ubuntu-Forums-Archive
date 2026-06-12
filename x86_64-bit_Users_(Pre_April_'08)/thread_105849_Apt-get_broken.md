---
title: "Apt-get broken?"
date: 2005-12-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by argosreality on 2005-12-19
This is really weird but apt-get seems to have broken itself. Or more accurately, like some of the PPC repositiories are no longer there. When I run apt-get update I get the following:> : Couldn't stat source package list [http://archive.ubuntu.com]("http://archive.ubuntu.com") breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-powerpc_Packages) - stat (2 No such file or directory)

W: Couldn't stat source package list [http://archive.ubuntu.com]("http://archive.ubuntu.com") breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-powerpc_Packages) - stat (2 No such file or directory)Its weird because previously (friday) I was able to apt-get with no difficulties. Not quite sure whats going on but it was doing this last night as well. Any thoughts?

---

