---
title: "Deluge 0.5.9.3 for Jaunty AMD64?"
date: 2009-04-25
forum: x86 64-bit Users
---

### Post by tcosync on 2009-04-25
Can I install the 0.5.9.3 version of Deluge on Ubuntu 9.04 AMD64? The latest version in the Jaunty repositories (ver 1.1.6) is too slow & freezes my internet connection for other applications. I obtained a 0.5.9.3 jaunty amd64 deb but the "Install Package" button is greyed out and I can't proceed any further. Can someone please point to a usable deb or instructions on how to compile one. 

Was using Deluge 0.5.9.3 with Intrepid 64bit and it worked very well.

Thanks! :)

PS - Loving my new installation of Jaunty 64bit very much...

---

### Post by evermooingcow on 2009-04-25
deluge 1.1.6 is slow?

I would guess your settings aren't optimized. Do they look similar to this?
[http://dev.deluge-torrent.org/wiki/Faq#WhatbandwidthsettingsshouldIuse](http://dev.deluge-torrent.org/wiki/Faq#WhatbandwidthsettingsshouldIuse)

---

### Post by tcosync on 2009-04-25
> **evermooingcow said:**
> deluge 1.1.6 is slow?

Yeah, tweaked those settings but still no joy. Just curious, how long does it take you to d/l a 350 MB file that has a couple of thousand seeders, using 1.1.6?

---

### Post by dk_zero-cool on 2009-04-27
Well, I have the same problem with 9.04. I had the same problem once with 8.10 to, when I updated the 0.5.9 to 0.9.x from source a while ago. But a downgrade fixed it then. This time the new version is in the repository, so a simple downgrade is not possible. I have tried to do install the 0.5.x from source, but it does not work. When it has been installed, and I type in the "deluge" command, I get this message:

File "usr/bin/deluge", line 43, in <module>
import deluge
ImportError: No module named deluge

Anyone know how to fix this. I have tried all the 0.5.9 source packages...
And deluge versions > 0.5.x just does'nt work. I normally download a package with 200 - 900 Kb/s when using deluge. With the new version in the 9.04 repositories, I am locky if I hit 15Kb/s

---

### Post by dk_zero-cool on 2009-04-27
#3 Go to the deluge website, and get the source for the version you want. Unpack it, and get to a terminal. In the deluge dir, you enter the fallowing:

1: python setup.py build
2: sudo make install

Now, I don't know why, but if I use python for both the build and install (python setup.py build && sudo python setup.py install) I get error messages when trying to start after install. And when I use make for both (make && make install) I also get errors when trying to start. Byt, if I mix it, it starts perfecly after install.

---

