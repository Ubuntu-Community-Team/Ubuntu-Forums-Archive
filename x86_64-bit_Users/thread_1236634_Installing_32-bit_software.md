---
title: "Installing 32-bit software"
date: 2009-08-10
forum: x86 64-bit Users
---

### Post by das7002 on 2009-08-10
I have all the ia32 libs and I have been googling for hours and I am having a bit of trouble trying to get an i386 deb to install on my AMD64 system gdebi won't do it and dpkg (age architecture (i386) does not match system (amd64)) doesn't like it either 

Please help me

---

### Post by warp99 on 2009-08-11
What program are you trying to install?

---

### Post by Jaesin on 2009-08-11
[http://ubuntuforums.org/showthread.php?t=474790&highlight=getlibs](http://ubuntuforums.org/showthread.php?t=474790&highlight=getlibs)

Try this, it helped me to install my printer drivers.

---

### Post by das7002 on 2009-08-11
After reading through the dpkg man page I found --force-architecture which worked just fine for me, also thanks Jaesin for the getlibs suggestion, as I see a good use for it

---

### Post by Jaesin on 2009-08-11
you're welcome.

---

