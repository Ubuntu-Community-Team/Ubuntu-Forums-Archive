---
title: "Repository Help for Backport of VLC"
date: 2007-01-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by Didjit on 2007-01-21
So, if I want to get this version of VLC.
[http://home.eng.iastate.edu/~superm1/dists/edgy/vlc-0.8.6/](http://home.eng.iastate.edu/~superm1/dists/edgy/vlc-0.8.6/)

How do I configure apt or appitude to snag it? I keep getting the svn Edgy release.

Didjit

---

### Post by RAOF on 2007-01-22
Well (from that site), you could add ```
deb http://home.eng.iastate.edu/~superm1 edgy vlc-0.8.6
```to your /etc/apt/sources.list file.  You may also want to add the guy's GPG key (instructions on the frontpage, but basically:
```
wget http://home.eng.iastate.edu/~superm1/80DF6D58.gpg -O- | sudo apt-key add -
```)

Then run "sudo aptitude update" and "sudo aptitude upgrade" to get the package.

Alternatively, you could just download the .deb from his site, and install it with a double-click :).

Edit: On a second look, he doesn't have AMD64 packages in that repository.  So you can't.

Well, you can, actually.  Add the "deb-src" line to your sources.list, and then run "sudo aptitude update" followed by "apt-get source -b vlc" (if that doesn't work, run "sudo apt-get build-dep vlc", which will install all the build-dependencies), which will download the source code and build the deb for you.  Then you can install the built deb.

---

### Post by Didjit on 2007-01-22
Thanks for the apt tips. I'll give it a shot. 

I noticed after I posted the pkgs said i386, but I thought maybe I was doing something wrong because the front page said AMD64 was supported.

didjit

---

