---
title: "Bit of a longshot but any ideas? (BlitzMAX)"
date: 2008-03-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by dgrafix on 2008-03-07
/usr/bin/ld: skipping incompatible /usr/lib/libGL.so when searching for -lGL
/usr/bin/ld: skipping incompatible /usr/lib/gcc-lib/x86_64-linux-gnu/3.3.6/../../../../lib/libGL.so when searching for -lGL
/usr/bin/ld: skipping incompatible /usr/lib/gcc-lib/x86_64-linux-gnu/3.3.6/../../../libGL.so when searching for -lGL
/usr/bin/ld: skipping incompatible /usr/lib/../lib/libGL.so when searching for -lGL
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libGL.so when searching for -lGL
/usr/bin/ld: skipping incompatible /usr/lib/libGL.so when searching for -lGL

I use a less known language called blitzmax that uses the gcc3.3 compiler and recently installed 64bit. I am getting these errors at compile time and have not a clue why. Never got them on 32bit.

Does anyone have a hint

---

### Post by LoneWolfJack on 2008-03-07
Looks like you are linking 64 bit libs when you need 32 bit libs. Try creating symlinks for every incompatible library to the 32bit version.

---

### Post by dgrafix on 2008-03-08
Lol how do i do that? :D

---

### Post by Cappy on 2008-03-08
Do you have ia32-libs installed?
```
sudo apt-get install ia32-libs
```

Do you have your restricted video drivers installed (ATI/Nvidia drivers)?

Do you have the 32-bit libGL libraries?
```
ls /usr/lib32/libGL*
```
(post the output of that please)

---

### Post by LoneWolfJack on 2008-03-08
```

ln -s /path/to/lib32/somelib.so /path/to/your/application/lib32/somelib.so

```

You can find the 32 bit libs in /usr/lib32

Good luck.

---

### Post by dgrafix on 2008-03-08
~$ ls /usr/lib32/libGL*
/usr/lib32/libGLcore.so.1          /usr/lib32/libGL.so.100.14.19
/usr/lib32/libGLcore.so.100.14.19  /usr/lib32/libGLU.so.1
/usr/lib32/libGL.so.1              /usr/lib32/libGLU.so.1.3.070001
~$ 

Yes to nvidia drivers

yes to ia32libs


I did the sym links:

sudo ln -s -T /usr/include/gnu/stubs-64.h /usr/include/gnu/stubs-32.h
sudo mv /usr/lib/libGL.so libGL.so.old
sudo ln -s -T /usr/lib32/libGL.so /usr/lib/libGL.so

That got rid of the skipping incompatable messages but now im simply getting the error:

/usr/bin/ld: cannot find -lGL

Got a feeling im getting close but have no idea what it needs.

---

### Post by Cappy on 2008-03-09
You don't have a /usr/lib32/libGL.so so that makes no sense as a possiblity.

Try installing
```
sudo apt-get install libsdl1.2-dev
```

and try
```
sudo ln -s /usr/lib32/libGL.so.1 /usr/lib32/libGL.so
```

You should reverse those changes you made already too. Linking from /usr/lib to /usr/lib32 is unncessary. You should only link from /usr/lib32 to /usr/lib32

```

sudo rm /usr/lib/libGL.so

```
```

sudo mv libGL.so.old /usr/lib/libGL.so
```

I tried to download BlitzMAX to give a definite solution but there is no linux demo.

---

### Post by dgrafix on 2008-03-10
Thanks seems to be getting there slowly, i can compile now at least :)

---

### Post by agtownz on 2008-03-10
I tried running BlitzMax from Wine and it seems to run surprisingly well.

---

### Post by dgrafix on 2008-03-11
Yes it does, the compiled apps/games run well too, but to be able to create a native linux app it needs to be compiled on linux.

I think i might switch back to 32bit ubuntu for now as i think my fiddling has broken my libs somehow.

Thanks for all your helps though. I do reccomend playing around with Bmax its a powerful but simple to learn CP-language. All it needs is a decent replacement for that horrid IDE.

---

### Post by LoneWolfJack on 2008-03-11
Going back to x32 won't be worth it... you'll have other problems. Once you get the whole idea behind why some things don't work out of the box in x64, it will become less of a hassle to fix those issues.

And BlitzMax... well, it doesn't come with braces so that's the end of that. ;)

Besides, there's Qt and GTK that you can combine with a real programming language. ;)

---

### Post by dgrafix on 2008-03-11
I wont have problems, it worked out of the box on x32.

If by braces you mean {} then it has its equivalent like pascal does, it is structured in the same way. If by a proper programming language you mean C++ then although powerful, i find it overly complex, not easy to debug and it is too assuming for my liking.

Personally I wish pascal could get a 3d facelift, oop and make a major comeback, until then the closest thing i have found in power and similar structure is Bmax+irrlicht (without learning the complexities of C++).

I liked pascal :(

---

