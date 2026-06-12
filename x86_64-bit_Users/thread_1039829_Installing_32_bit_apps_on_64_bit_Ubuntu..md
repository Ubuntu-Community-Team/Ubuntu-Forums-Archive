---
title: "Installing 32 bit apps on 64 bit Ubuntu."
date: 2009-01-14
forum: x86 64-bit Users
---

### Post by chris062689 on 2009-01-14
I'm running 8.10, and want to know how exactly I can install 32 bit applications in a 64 bit environment, I know it's possible.

Notably Aptana Studio and PCSX2.
Any help?  :confused:

---

### Post by jespdj on 2009-01-15
If you have a 32-bit only .deb package, you can force it to install like this:
```
sudo dpkg -i --force-architecture filename.deb
```
After that, you might need to install the ncessary 32-bit libraries for the program. The [getlibs](http://ubuntuforums.org/showthread.php?t=474790) script can detect and install 32-bit libraries automatically for you.

---

### Post by Yellow Pasque on 2009-01-15
You can run the 32-bit version(s), but running the native 64-bit version is generally preferable.

Directions from the Aptana page:
> 64-bit Linux users please install Aptana as a plugin into Eclipse

pcsx2:
[http://forums.pcsx2.net/thread-2375.html](http://forums.pcsx2.net/thread-2375.html) (Make sure you have the prerequisite packages listed further down the thread).

---

### Post by chris062689 on 2009-01-15
Well, there discontiuing support for PCSX2 64, and installing Aptana over Eclipse I hear doesn't give you the "full Aptana experience".
I'll keep that in mind though, how exactly do you use getlibs?

---

### Post by jespdj on 2009-01-15
> **chris062689 said:**
> I'll keep that in mind though, how exactly do you use getlibs?
Click the link in my post above, it explains how to use getlibs.

---

