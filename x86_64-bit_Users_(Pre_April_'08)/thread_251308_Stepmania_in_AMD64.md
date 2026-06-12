---
title: "Stepmania in AMD64"
date: 2006-09-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by Tyrance on 2006-09-05
Hi.

I found a patch from this forum for compiling stepmania under 64-bit system.
It's .txt so how do i use it?

found here: [http://www.ubuntuforums.org/showthread.php?t=34700]("http://www.ubuntuforums.org/showthread.php?t=34700")

Cheers. 

-J

---

### Post by sciboy on 2007-02-14
Well if you just want to use the official Stepmania linux binary i put this together pretty quickly.
[http://www.sciboy.org/stepmania/StepMania-AMD64.tar.gz](http://www.sciboy.org/stepmania/StepMania-AMD64.tar.gz)

I couldn't get that patch working so i just chucked together the libraries it needed with some other dudes wrapper script.
It'll work with both the 3.9 and 4.0 binaries, just extract it into the StepMania directory and run the script.

---

### Post by micke090 on 2007-05-22
This does not work for me, i get this from the terminal

```
mco@Michael03:~$ '/home/mco/StepMania-CVS-20070325-linux/amd64-wrapper.sh' 
StepMania CVS 4.0 CVS
Log starting 2007-05-22 16:37:53
Couldn't load driver gtk: dlopen(): libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory
Error: Couldn't open any loading windows.
```

---

### Post by Cappy on 2007-07-21
Make sure you have universe enabled and

```
sudo apt-get install ia32-libs ia32-libs-gtk
```

---

### Post by FruitieX on 2008-06-21
I am getting this error when executing the amd64 wrapper script:

rasse@fruitiex-laptop:~/Games/StepMania-CVS-20080103-linux$ ./amd64-wrapper.sh 
./stepmania: error while loading shared libraries: libpng.so.3: cannot open shared object file: No such file or directory

I installed libpng via apt-get but still no luck. :(
Oh, and I am running the 64-bit version of Hardy.

---

### Post by Cappy on 2008-06-21
Install getlibs: [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)
and run
```
sudo getlibs ~/Games/StepMania-CVS-20080103-linux/stepmania
```

---

