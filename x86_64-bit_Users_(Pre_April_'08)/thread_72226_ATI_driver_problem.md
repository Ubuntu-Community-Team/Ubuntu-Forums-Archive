---
title: "ATI driver problem"
date: 2005-10-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by chs on 2005-10-05
A few days ago i upgraded to all the latest Hoary packages. ia32-libs failed, so I followed the instructions here: 
[http://ubuntuforums.org/showthread.php?t=51983](http://ubuntuforums.org/showthread.php?t=51983)
3d accel no longer works as a regular user though, even after reinstalling the drivers
```
chs@beastor:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)
```
```
[COLOR="Red"]root[/COLOR]@beastor:~ # fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X800 PRO Generic
OpenGL version string: 1.3.4769 (X4.3.0-8.8.25)

```
fgl_glxgears runs ok as root, but crashes when run as a normal user:
```
chs@beastor:~$ fgl_glxgears
X Error of failed request:  BadMatch (invalid parameter attributes)
Major opcode of failed request:  145 (GLX)
Minor opcode of failed request:  5 (X_GLXMakeCurrent)
Serial number of failed request:  33
Current serial number in output stream:  33
```
Is there any way to get this working again?...

---

### Post by mlomker on 2005-10-05
> Is there any way to get this working again?...

Run through my [how-to]("http://www.ubuntuforums.org/showthread.php?p=348911") and I'll help you out if you run into any snags.

I'd guess one of the libraries got overwritten along the way.

---

