---
title: "Wine Link Problems"
date: 2008-07-23
forum: Wine
---

### Post by kratos777 on 2008-07-23
Hello, I was trying to add add a symbolic link to one of my users on my system so they can use a program I have. The problem is that it is not working. The console says there are too many symbolic links already. Is there any way I can configure wine or my system so that other users can use the programs I have installed on my account?

---

### Post by LinuxRocks713 on 2008-08-03
System-wide programs should not be sitting inside ~/bin in the first place; They should be inside /usr/bin, /bin, /sbin and /usr/local/bin. And why are you trying to run Linux programs in Wine?

I don't know what you are trying to do, but try:

```

ln -s ~/bin/*yourproghere* ~/.wine/drive_c/*yourproghere*

```

if all else, build a Debian package of your program. You can find out how here: [http://www.compdigitec.com/labs/2008/07/28/building-deb-packages-on-ubuntudebian/](http://www.compdigitec.com/labs/2008/07/28/building-deb-packages-on-ubuntudebian/)

---

