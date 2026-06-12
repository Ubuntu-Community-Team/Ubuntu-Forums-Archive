---
title: "Segmentation fault"
date: 2008-05-13
forum: x86 64-bit Users
---

### Post by srikar on 2008-05-13
Many applications are having a problem.When i start them they get closed after a while.


for ex:-when i launch blender from terminal , i get segmentation error.

```

srikar@immortal:~$ blender
guessing 'blender-bin' == '/usr/bin/blender-bin'
Compiled with Python version 2.5.2.
Checking for installed Python... got it!
Segmentation fault
```

I get this error when i launch some of the games also.
how do i fix it???

---

### Post by hermes0710 on 2008-05-14
Did you compile blender from source or are you using the default package?

---

### Post by srikar on 2008-05-14
I installed blender from synaptic.

---

### Post by hermes0710 on 2008-05-14
Do you use 64 or 32 bit?

---

### Post by srikar on 2008-05-14
64 bit hardy heron.

---

### Post by hermes0710 on 2008-05-14
Go here:

[http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg426755.html]("http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg426755.html")

and here:

[http://forum.fedoraforum.org/forum/showthread.php?t=173692&page=1&pp=15]("http://forum.fedoraforum.org/forum/showthread.php?t=173692&page=1&pp=15")

It seems to be a bug.

---

### Post by srikar on 2008-05-14
> **hermes0710 said:**
> Go here:

[http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg426755.html]("http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg426755.html")

and here:

[http://forum.fedoraforum.org/forum/showthread.php?t=173692&page=1&pp=15]("http://forum.fedoraforum.org/forum/showthread.php?t=173692&page=1&pp=15")

It seems to be a bug.


so any kinda fix???

---

### Post by hermes0710 on 2008-05-14
The only thing i can suggest is download the source code and compile it...

---

### Post by Kilz on 2008-05-14
The bugs linked to are in mesa, not blender according to the links provided. The original poster may want to try the proprietary video drivers for their video card. This should also solve problems with games.

---

### Post by Tynach on 2008-08-26
Not true. I have the same problems with Blender and a few games, and I have the proprietary version of my video drivers.

What's more, if I download Blender from their site, it works JUST FINE.

It is ONLY when I run Blender from the repository version that I have errors.

Using debugging mode, I got this much output from Blender. Doesn't help me, though:

```
~$ blender -d
guessing 'blender-bin' == '/usr/bin/blender-bin'
Blender 2.45 (sub 0) Build
argv[0] = blender-bin
argv[1] = -d
Compiled with Python version 2.5.2.
Checking for installed Python... got it!
Color depth r 8 g 8 b 8
Aux buffers: 4
read file
  Version 242 sub 4
read file /home/tynach/.B.blend
  Version 246 sub 0

ordered
 OBCube
 OBEmpty
 OBCamera
 OBLamp
Segmentation fault
```

---

### Post by Kilz on 2008-08-26
You might want to [file a bug report on launchpad]("https://launchpad.net/ubuntu/+filebug"). That way the developers who really will fix the issue know about it.

---

### Post by webmadman on 2008-09-02
I just switched my Kubuntu install to 64bit from 32bit and got this same error with Blender when I was using the xorg-driver-fglrx, but when I switched to using the envy version, Blender works like a charm. Might be a solution.

---

### Post by Tynach on 2008-10-11
> **webmadman said:**
> I just switched my Kubuntu install to 64bit from 32bit and got this same error with Blender when I was using the xorg-driver-fglrx, but when I switched to using the envy version, Blender works like a charm. Might be a solution.

No solution there.

Its worth noting that I have an nVidia GeForce 6600 LE graphics card with 256 mb of RAM built in.

I switched to the Envy driver, and I still get the random segfault. Using 32 bit Linux, but a 64 bit processor (AMD Athlon 64 3000+ to be exact).

---

