---
title: "HOWTO: install gizmo on 64bit feisty"
date: 2007-04-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by brt on 2007-04-27
this is how i did it:

```
first download the gizmo...i386.deb file from the gizmoproject website:
[http://www.gizmoproject.com/download-linux.html]("http://www.gizmoproject.com/download-linux.html")
[http://download.gizmoproject.com/GizmoDownload/gizmo-project_2.0.0.56_i386.deb]("http://download.gizmoproject.com/GizmoDownload/gizmo-project_2.0.0.56_i386.deb")
```

following the sticky post i installed it using dpkg forcing to ignore the architecture:

```
sudo dpkg --force-architecture -i gizmo-project_2.0.0.56_i386.deb
```

almost done, but when i tried to run it from terminal i got an error about missing "libsipphoneapi.so.1.6.00.51":
> gizmo: error while loading shared libraries: libsipphoneapi.so.1.6.00.51: cannot open shared object file: No such file or directory

so i did:

```
sudo ln -s /usr/lib/libsipphoneapi.so.1.6.00.51 /usr/lib32/
```

and it works :) gizmo starts up without any problems :D

---

### Post by Cappy on 2007-08-16
nearly the same for me, except my library was different:
```

sudo mv /usr/lib/libsipphoneapi.so.1.7.07.71 /usr/lib32

```

and I had to use getlibs: [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)
to
```

getlibs -32 libXss.so.1

```

Gizmo is terrible though .. it cuts off my calls .. only tried using because skype was down =-/

Gizmo can die.

---

### Post by wolf08 on 2007-08-25
Thank you for the updated info - works with Feisty and Gizmo 3.1.0.77.

---

