---
title: "Compiling issues - anyway to &quot;install&quot; 32bit?"
date: 2009-02-02
forum: x86 64-bit Users
---

### Post by Warthaug on 2009-02-02
I have been experimenting with ubuntu 64bit (8.10).  While there have been some smashing successes (near-halving of the processing time used by matlab), I have had some serious issues getting some packages installed.

Long story short, I'm trying to install a range of bioinformatics and molecular modeling programs.  Most of these are unavailable pre-complied in 64-bit, so I'm having to compile my own 64-bit versions.  Generally this has worked well, but I've run into two exceptions.  In both cases I've contacted the provider and gotten replies along the lines of "we used libraries which don't have 64bit versions yet, so you cannot recompile at this time".

Is there some way to deal with this, without having a second 32-bit install?  I've tried installing the 32-bit instillations directly, but always get the "this is not the correct architecture" errors...

Bryan

---

### Post by jespdj on 2009-02-02
How are you trying to install the 32-bit versions? You can install 32-bit .deb packages like this:
```
sudo dpkg -i --force-architecture filename.deb
```
If you install software manually that checks if it's running on a 32-bit system, you can try "linux32":
```
linux32 /path/to/executable
```
You might need to install 32-bit libraries that the software uses to make it work. The [getlibs](http://ubuntuforums.org/showthread.php?t=474790) script can help you to do this automatically.

---

### Post by Warthaug on 2009-02-02
> **jespdj said:**
> How are you trying to install the 32-bit versions? 

Usually via dpkg, sometimes using the ./filname.sh method.  If I remeber correctly, the packages I'm having issues with are all .deb's.

> **jespdj said:**
> 
You can install 32-bit .deb packages like this:
```
sudo dpkg -i --force-architecture filename.deb
```
If you install software manually that checks if it's running on a 32-bit system, you can try "linux32":
```
linux32 /path/to/executable
```
You might need to install 32-bit libraries that the software uses to make it work. The [getlibs](http://ubuntuforums.org/showthread.php?t=474790) script can help you to do this automatically.

Perfect - that's exactly what I needed to know.

thanx again! :p

Bryan

---

