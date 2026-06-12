---
title: "64-bit Makehuman .deb?"
date: 2008-10-30
forum: x86 64-bit Users
---

### Post by Tindytim on 2008-10-30
I found a few .debs in this thread:
[http://ubuntuforums.org/showthread.php?t=333615](http://ubuntuforums.org/showthread.php?t=333615)

But I get this error:
```
XXX@XXX:~$ makehuman
makehuman: error while loading shared libraries: libmhgui.so.0: cannot open shared object
file: No such file or directory

```
I installed animorph, and mhgui (in that order).

I tried compiling it myself, but I couldn't even get animorph to compile, getting this error:
```
BodySettings.cpp: In member function 'void Animorph::BodySettings::fromStream(std::ifstream&)':
BodySettings.cpp:54: error: 'strlen' was not declared in this scope
make[2]: *** [BodySettings.lo] Error 1
make[2]: Leaving directory `/home/tim/Desktop/MakeHuman/animorph-0.3/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/tim/Desktop/MakeHuman/animorph-0.3'
make: *** [all] Error 2

```

---

### Post by Tindytim on 2008-10-31
I got it working in 8.10 x64! Yay!
[IMG]http://img356.imageshack.us/img356/2432/makehumanwk8.png[/IMG]
I used this site for the compile issues:
[http://gcc.gnu.org/gcc-4.3/porting_to.html](http://gcc.gnu.org/gcc-4.3/porting_to.html)

And then after I installed animorph, mhgui, and makehuman (in that order) I had to use these commands:
```
sudo ln -s /usr/local/lib/libmhgui.so.0 /usr/lib/libmhgui.so.0
sudo ln -s /usr/local/lib/libanimorph.so.0 /usr/lib/libanimorph.so.0
```

---

### Post by micosta on 2008-11-06
I have also tried to compile animorph but I got into the same error:  "'strlen' was not declared in this scope":( I'd like to know how did you get through it.
Thanks

---

### Post by Tindytim on 2008-11-12
> **micosta said:**
> I have also tried to compile animorph but I got into the same error:  "'strlen' was not declared in this scope":( I'd like to know how did you get through it.
Thanks
I'm sorry, were you the one that PM'd me?

---

### Post by moueza on 2008-11-20
Same error:
have you just added: 
#include <iostream>
using namespace std; 
as said in [http://gcc.gnu.org/gcc-4.3/porting_to.html](http://gcc.gnu.org/gcc-4.3/porting_to.html)   ?

---

### Post by FromtheHip on 2009-01-24
I found a blog that discusses these problems and a better solution than changing the code ([http://www.nexal.it/blog/?tag=ubuntu-810](http://www.nexal.it/blog/?tag=ubuntu-810)).  It is in Italian, but Google translated it for me.  He says that the Subversion (SVN) repository has code that is compatible with GCC 4.3.

I followed his instructions and built the package without any code changes.

FromtheHip

---

