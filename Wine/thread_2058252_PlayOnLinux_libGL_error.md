---
title: "PlayOnLinux libGL error"
date: 2012-09-15
forum: Wine
---

### Post by hfa2010 on 2012-09-15
Hi guys!
 Well, it's been a reasonable time since i'm getting this error. The thing is that playonlinux can't open/load 32-bit drivers/libraries. I'm in Ubuntu 64 bits and already installed some time ago ia32-libs and my system has a ppa with updated drivers that is not xorg-edgers. My last try was attempting to create symbolic links between the /usr/lib/x86_64-linux-gnu/dri/
and /usr/lib/i386-linux-gnu/ including the directory dri. And for the dri question, i'm already enabled it and yet i get this error. I don't know what to do.[Here]("http://pastebin.com/Z7jfUCKK")(link) is a log created with  LIBGL_DEBUG=verbose playonlinux &>> output.txt. Therefore thanks for any help. I think that i'm not alone in this.

---

