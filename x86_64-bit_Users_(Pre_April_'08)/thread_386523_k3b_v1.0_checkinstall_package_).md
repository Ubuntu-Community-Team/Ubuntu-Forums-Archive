---
title: "k3b v1.0 checkinstall package :)"
date: 2007-03-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by CyberAngel on 2007-03-17
I have just created a k3b v1.0 package using checkinstall
It is conflicting with some files of the package libk3b2 but installing it with

```
dpkg --force-overwrite -i k3b_1.0-1_amd64.deb
```

has no problems for me :)

Because it is checkinstall it does not have the dependencies marked so you may need to apt-get some extra packages yourself (all the extra packages I used exists in the official repositories).

k3b 1.0 Rocks!!! :)

EDIT: I forgot the most important... A link to the package :P
[http://filebeam.com/eed9c9755ae890f8041e88bd6e120363](http://filebeam.com/eed9c9755ae890f8041e88bd6e120363)

---

