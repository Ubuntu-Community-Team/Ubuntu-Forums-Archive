---
title: "Installing from i386 debs possible in x86-64?"
date: 2007-07-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by phoenix_fire2005 on 2007-07-27
Is it possible to just force an i386 deb to install on x86-64 ubuntu, and would it work properly? I know 32-bit apps can run on x86-64 ubuntu, but I'm thinking they might need some "coaxing" of some sort. I know this is a big NOOB question, but I didn't find any generic instructions on installing i386 debs... only instructions on how to install specific 32-bit apps on 64-bit ubuntu.

Thanks for the help in advance!

---

### Post by jamesford on 2007-07-27
sometimes it works sometimes it doesent. the method is
sudo dpkg -i --force-architecture somethingi386.deb

not sure if u need to be careful about this

---

### Post by Kilz on 2007-07-27
> **phoenix_fire2005 said:**
> Is it possible to just force an i386 deb to install on x86-64 ubuntu, and would it work properly? I know 32-bit apps can run on x86-64 ubuntu, but I'm thinking they might need some "coaxing" of some sort. I know this is a big NOOB question, but I didn't find any generic instructions on installing i386 debs... only instructions on how to install specific 32-bit apps on 64-bit ubuntu.

Thanks for the help in advance!

Yes, you can force applications. Just never, ever, ever force install libraries.

---

### Post by sammy_pal on 2007-07-28
Doesn't always help.... :(

---

### Post by Kilz on 2007-07-28
> **sammy_pal said:**
> Doesn't always help.... :(

When you force install an application, you may have to manulay install some 32bit libraries. Without the required files some applications will not start even if you force them in.

---

### Post by phoenix_fire2005 on 2007-07-28
> **Kilz said:**
> When you force install an application, you may have to manulay install some 32bit libraries. Without the required files some applications will not start even if you force them in.

How do you go about doing this? I made another thread (see below) when trying to install DOSBox 0.70 in a i386 deb failed due to some missing dependencies, which I assume are some 32-bit libraries...

[http://ubuntuforums.org/showthread.php?t=511968](http://ubuntuforums.org/showthread.php?t=511968)

---

### Post by Cappy on 2007-07-28
Try getlibs: [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)
install it and then
```
getlibs /usr/bin/dosbox
```

---

