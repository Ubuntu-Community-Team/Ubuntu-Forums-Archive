---
title: "ia32-libs update broken?"
date: 2005-07-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by pailhead on 2005-07-26
I'm trying to do the update to my system and it wants to update ia32-libs but it crashes with the following error:

```

E: /var/cache/apt/archives/ia32-libs_0.5ubuntu3.1_amd64.deb:  error creating symbolic link `./usr/lib32/libGL.so.1': No such file or directory

```

How can I remedy this error? I'm running an AMD Athlon64 3000+. Any ideas?

Thanks...

---

### Post by GuyveR800 on 2005-07-26
1. deinstall xorg-driver-fglrx
2. update ia32-libs
3. reinstall xorg-driver-fglrx

worked for me :)

---

### Post by pailhead on 2005-07-26
[QUOTE=GuyveR800]1. deinstall xorg-driver-fglrx
2. update ia32-libs
3. reinstall xorg-driver-fglrx

worked for me :)[/QUOTE]
 I will try that thanks!

---

### Post by jensyt on 2005-07-26
[QUOTE=GuyveR800]1. deinstall xorg-driver-fglrx
2. update ia32-libs
3. reinstall xorg-driver-fglrx

worked for me :)[/QUOTE]

This does work, but unluckily enough, the drivers don't work anymore.

```
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)
```

Perhaps it's just me. Can anyone confirm this?

I've also tried downgrading again, but with no luck...

---

### Post by optikshell on 2005-07-26
this is off topic... but jensyt... your avatar is awesome. It made me laugh when I saw it.   :)

---

### Post by jensyt on 2005-07-26
Thanks, optikshell. I was inspired by the well known Tux 'n Tosh theme, but redrew everything in Inkscape. :D

Also, to remain on topic, I found a bug and added a comment to it.

[http://bugzilla.ubuntu.com/show_bug.cgi?id=12893](http://bugzilla.ubuntu.com/show_bug.cgi?id=12893)

I'd really appreciate any confirmation on my traumatic experience with upgrading.

---

### Post by jerrybme on 2005-07-29
I have the same issue. I'm using the ATI drivers and am waiting to try the uninstall, upgrade & reinstall method until I have lots of time to futz with the ATI drivers. They are working now & I don't want to lose my hard won 3D excelleration  :?

---

### Post by Tamir on 2005-07-29
[QUOTE=jerrybme]I have the same issue. I'm using the ATI drivers and am waiting to try the uninstall, upgrade & reinstall method until I have lots of time to futz with the ATI drivers. They are working now & I don't want to lose my hard won 3D excelleration  :?[/QUOTE]
 try to do:

```
whereis libGL.so.1
```
where ever it will be found, do 

```
 ln -s /path/that/you/found/libGL.so.1 /usr/lib32/libGL.so.1
```
I had this same :/

---

### Post by estel on 2005-07-30
[QUOTE=Tamir]try to do:

```
whereis libGL.so.1
```
where ever it will be found, do 

```
 ln -s /path/that/you/found/libGL.so.1 /usr/lib32/libGL.so.1
```
I had this same :/[/QUOTE]
 Though in Breezy, I've had lots of upgrade troubles with ia32-libs, a zlibs file I can't remember and... something else.
The error is different though, it claims that it's trying to unpack /lib64 which is already in (name of a different package).

---

