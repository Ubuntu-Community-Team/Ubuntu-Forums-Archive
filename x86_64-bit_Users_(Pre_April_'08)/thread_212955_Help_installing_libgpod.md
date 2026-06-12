---
title: "Help installing libgpod"
date: 2006-07-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by Kapitalizt on 2006-07-10
When I try to install libgpod I get this error:

```
configure: error: Package requirements (glib-2.0 >= 2.4.0 gobject-2.0) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively you may set the LIBGPOD_CFLAGS and LIBGPOD_LIBS environment variables
to avoid the need to call pkg-config.  See the pkg-config man page for
more details.
```

---

### Post by Kilz on 2006-07-10
> **Kapitalizt said:**
> When I try to install libgpod I get this error:

```
configure: error: Package requirements (glib-2.0 >= 2.4.0 gobject-2.0) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively you may set the LIBGPOD_CFLAGS and LIBGPOD_LIBS environment variables
to avoid the need to call pkg-config.  See the pkg-config man page for
more details.
```
It looks like you are trying to compile libgpod, There is an already compiled libgpod0 in syanptic. Are you trying to install an application that needs the lib?

---

### Post by Kapitalizt on 2006-07-10
> **Kilz said:**
> It looks like you are trying to compile libgpod, There is an already compiled libgpod0 in syanptic. Are you trying to install an application that needs the lib?

Yeah I'm trying to install gtkpod.  And when I try to install gtkpod I get this error:

```
configure: error: *** Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable

```

---

### Post by RAOF on 2006-07-10
Is there any particular reason you want to compile-from-source?  Becuase you could easily do **sudo aptitude install gtkpod** (or gtkpod-aac).

---

### Post by Kapitalizt on 2006-07-10
> **RAOF said:**
> Is there any particular reason you want to compile-from-source?  Becuase you could easily do **sudo aptitude install gtkpod** (or gtkpod-aac).

I didn't now you could do that and thanks it worked.

---

### Post by RAOF on 2006-07-10
> **Kapitalizt said:**
> I didn't now you could do that and thanks it worked.
You'll find Ubuntu **much** easier to use if you use the package manager!  Installing from source is so 1995 :)

For other useful commands, check out **man apt-get** and/or **man aptitude**.   And there's a graphical version: Synaptic Package Manager, under System->Administration (I think)

---

### Post by Kilz on 2006-07-10
> **Kapitalizt said:**
> I didn't now you could do that and thanks it worked.
[You may want to read this page]("http://www.monkeyblog.org/ubuntu/installing/"). It gives lots of information on using Synaptic to install applications from the repositories.

---

### Post by W. James MacLean on 2006-07-10
> **RAOF said:**
> Is there any particular reason you want to compile-from-source?  Becuase you could easily do **sudo aptitude install gtkpod** (or gtkpod-aac).

When I try this I get

```

user@dmachine:~/Software-Linux$ sudo aptitude install gtkpod
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "gtkpod"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
user@machine:~/Software-Linux$ sudo aptitude install gtkpod-aac
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "gtkpod-aac"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

```


I'm using Dapper Drake. Any thoughts?

Regards -

---

### Post by RAOF on 2006-07-10
You probably haven't enabled the Universe and/or Multiverse repositories.  Check out the link above, and go to the first appendix "Enabling extra repositories"

---

### Post by W. James MacLean on 2006-07-11
> **RAOF said:**
> You probably haven't enabled the Universe and/or Multiverse repositories.  Check out the link above, and go to the first appendix "Enabling extra repositories"

Ahh, got it (newbie-itis). It works now, thanks!

James

---

