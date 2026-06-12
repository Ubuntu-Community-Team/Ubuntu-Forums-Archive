---
title: "ia32-libs not installing all the files?"
date: 2008-12-23
forum: x86 64-bit Users
---

### Post by nschubach on 2008-12-23
I've googled this and found specific patches for specific programs, but none of them get to the root problem that ia32 seems to be missing a lot of files.

What keyed me to this was the missing libSDL_image-1.2.so.0 among others.  The link is there.  The target is not.

---

### Post by nevada1920 on 2008-12-23
it is wonkey abit in ubuntu 8.10 :lolflag::popcorn:

---

### Post by nschubach on 2008-12-23
Does anyone happen to know of a "good" repository with the proper build?  I'd hate to have to do each file individually.  Call me lazy.  Sorry.:(

---

### Post by Lobotomy on 2009-01-15
Hello all,

Here is an ugly hack I have found to work, in waiting for bug #277454 to be fixed (which seems unlikely, as it was marked as 'wishlist'...) I have had success under Hardy...

First, find a package that have the file:
[http://packages.debian.org/sid/i386/libsdl-image1.2/download](http://packages.debian.org/sid/i386/libsdl-image1.2/download)

This is the debian package, but note: we take arch 'i386' and neither 'amd64' not 'ia64'...

Create yourself a directory which will contains the temporary things, and go into it:
```
mkdir ugly_hack
cd ugly_hack
```

Now, extract there the package (don't install!)
```
dpkg -x some_path/libsdl-image1.2_1.2.6-3_i386.deb
```

...and now, just copy the file to the right place:
```
sudo cp ./usr/lib/libSDL_image-1.2.so* /usr/lib32
```

(sudo needed because target directory is system)

Et voila! you can now delete all your 'ugly_hack' directory!

That was so user-friendly, wasn't it? /o\

---

### Post by Kilz on 2009-01-15
> **Lobotomy said:**
> Hello all,

Here is an ugly hack I have found to work, in waiting for bug #277454 to be fixed (which seems unlikely, as it was marked as 'wishlist'...) I have had success under Hardy...

First, find a package that have the file:
[http://packages.debian.org/sid/i386/libsdl-image1.2/download](http://packages.debian.org/sid/i386/libsdl-image1.2/download)

This is the debian package, but note: we take arch 'i386' and neither 'amd64' not 'ia64'...

Create yourself a directory which will contains the temporary things, and go into it:
```
mkdir ugly_hack
cd ugly_hack
```

Now, extract there the package (don't install!)
```
dpkg -x some_path/libsdl-image1.2_1.2.6-3_i386.deb
```

...and now, just copy the file to the right place:
```
sudo cp ./usr/lib/libSDL_image-1.2.so* /usr/lib32
```

(sudo needed because target directory is system)

Et voila! you can now delete all your 'ugly_hack' directory!

That was so user-friendly, wasn't it? /o\

Only one word.....
[Getlibs]("http://ubuntuforums.org/showthread.php?t=474790&highlight=getlibs")

---

