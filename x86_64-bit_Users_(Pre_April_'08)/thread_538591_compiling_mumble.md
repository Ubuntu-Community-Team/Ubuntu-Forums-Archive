---
title: "compiling mumble"
date: 2007-08-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by ozfinngeek on 2007-08-30
Hi,
I am a total noob at compliing and this is my first go at it. I am trying to compile mumble 1.0.0,on 7.04 amd64 and i have installed all the libs. It gives me the following errors when i run the make:

make[2]: g++: Command not found
make[2]: *** [debug/mumble.gch/c++] Error 127
make[2]: Leaving directory `/home/sysop/mumble.source/mumble-1.0.0/src/mumble'
make[1]: *** [debug] Error 2
make[1]: Leaving directory `/home/sysop/mumble.source/mumble-1.0.0/src/mumble'
make: *** [sub-src-mumble-make_default] Error 2

Any ideas what i am doing wrong?

Thanks

---

### Post by John.Michael.Kane on 2007-08-30
> **ozfinngeek said:**
> Hi,
I am a total noob at compliing and this is my first go at it. I am trying to compile mumble 1.0.0,on 7.04 amd64 and i have installed all the libs. It gives me the following errors when i run the make:

make[2]: g++: Command not found
make[2]: *** [debug/mumble.gch/c++] Error 127
make[2]: Leaving directory `/home/sysop/mumble.source/mumble-1.0.0/src/mumble'
make[1]: *** [debug] Error 2
make[1]: Leaving directory `/home/sysop/mumble.source/mumble-1.0.0/src/mumble'
make: *** [sub-src-mumble-make_default] Error 2

Any ideas what i am doing wrong?

Thanks

Your missing the GNU C++ compiler

Run the command below.
```
gksudo aptitude install g++
```

After which try recompiling the program.

---

### Post by tvrg on 2007-08-30
only installing gcc won't solve everything, you will most probably get another error message (make not installed or whatever)

its easier to just install build-essential 
```
sudo apt-get install build-essential 
```

---

### Post by ozfinngeek on 2007-08-30
thanks for the info, i will try installing the essentials pack when i get home from work. I do actually have 2 versions of g++ installed which is why i am so confused. I will post back after i do that.

---

### Post by ozfinngeek on 2007-09-01
sudo apt-get build essentials worked perfectly for me. It was complied first time and mumble worked straight away, well after config anyway.

Many thanks for all the help.

I will be compiling from source more often now.:)

Cookies for everyone (the good edible kind, not the track and report kind).

---

### Post by helliewm on 2007-09-01
The Mumble deb is on  [www.getdeb.net](www.getdeb.net). I am sure I saw it there last night.

Helen

---

### Post by John.Michael.Kane on 2007-09-01
> **helliewm said:**
> The Mumble deb is on  [www.getdeb.net](www.getdeb.net). I am sure I saw it there last night.

Helen

You are correct. There's a mumble deb for 64bit there,however. It never hurts when someone wants to compile their own.

Note: For those wanting mumble 64bit from get deb link is below.
[Mumble]("http://www.getdeb.net/search.php?keywords=Mumble")

---

### Post by gnusci on 2007-09-01
I had the same problem, just give a look to the thread:

[http://ubuntuforums.org/showthread.php?t=539374](http://ubuntuforums.org/showthread.php?t=539374)

There is also some information regarding X11 and OpenGL, they are very necessary for GUI applications and Games.

---

