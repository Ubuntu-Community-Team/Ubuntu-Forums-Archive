---
title: "Bad with install GStreamer"
date: 2006-10-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by namai on 2006-10-03
Hi, i have a problem with installing GStreamer:
namai@namai-desktop:~$ sudo apt-get install gstreamer0.10-plugins-ugly
Password:
Reading package lists... Done
Building dependency tree... Done
Package gstreamer0.10-plugins-ugly is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gstreamer0.10-plugins-ugly has no installation candidate
namai@namai-desktop:~$
:confused:

---

### Post by Fedcer on 2006-10-03
Do you have the Universe repository enabled ?

If you don't know what I'm talking about look here [http://monkeyblog.org/ubuntu/installing/#enabling_extra_repositories](http://monkeyblog.org/ubuntu/installing/#enabling_extra_repositories) and here [http://psychocats.net/ubuntu/sources](http://psychocats.net/ubuntu/sources)


If you have it enabled run:
```

sudo apt-get update

```

and try again

---

### Post by namai on 2006-10-04
Thank you.

---

