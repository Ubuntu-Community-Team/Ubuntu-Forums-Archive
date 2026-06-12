---
title: "Spore"
date: 2008-09-15
forum: Wine
---

### Post by Dpaulson on 2008-09-15
Yeah, i know there are 50 other topics dealing with spore problems, but i didnt find my problem so please bear with me, i installed spore without a hitch but when i launch it i get 

"The game can not start
There seems to be a problem contacting the license server. Ensure your internet connection is active and try again in a few minutes."

i've gone through this about 3 times now, no other problems but this.

---

### Post by hikaricore on 2008-09-15
I'm assuming you've already read through the installation instructions here right?

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=13652](http://appdb.winehq.org/objectManager.php?sClass=version&iId=13652)

---

### Post by nwlinkvxd on 2008-09-15
Dpaulson: there's a known issue with the DRM/licensing server. The latest version from git has a patch, but that means compiling from source. You can also wait until the 19th, when the next version of Wine (1.1.5) is made available.

[How to use Git for Wine]("http://ubuntuforums.org/showpost.php?p=1446972&postcount=1") You can skip the first step. Once you have this version of Wine, you won't need to patch anything. Just compile following [these instructions]("http://wiki.winehq.org/WineOn64bit#head-7703cf4cc6b63630523cf66e77d621e4f81bc873") if you're running 64-bit Ubuntu, or use the same guide skipping the second step if you're on 32-bit. Be sure to completely uninstall Wine in Synaptic before doing this.

---

