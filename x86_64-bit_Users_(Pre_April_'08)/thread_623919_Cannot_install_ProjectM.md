---
title: "Cannot install ProjectM"
date: 2007-11-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by LordVeovis on 2007-11-26
I have looked at alot of other posts and found similar ones to this and even a few other people with the same problem, but nothing has fixed my problem.

When trying to install, I get all teh way to running the command make for libprojectM I have all the dependencies and everything installed but get the following

```
desktop:~/InstallProjectM/libprojectM-1.01$ make
Linking CXX shared library libprojectM.so
/usr/bin/ld: /usr/lib/gcc/x86_64-linux-gnu/4.1.3/../../../../lib/libftgl.a(FTFont.o): relocation R_X86_64_32S against `vtable for FTFont' can not be used when making a shared object; recompile with -fPIC
/usr/lib/gcc/x86_64-linux-gnu/4.1.3/../../../../lib/libftgl.a: could not read symbols: Bad value
collect2: ld returned 1 exit status
make[2]: *** [libprojectM.so] Error 1
make[1]: *** [CMakeFiles/projectM.dir/all] Error 2
make: *** [all] Error 2
```

Any suggestions as to how I can fix this would be much appriciated.

---

### Post by Ehtetur on 2007-11-28
From your error message, it looks like make is looking for ftgl-dev...

hrmm... I bet you already ftgl-dev installed...:evil:
It looks like Kilz and some other folks ran across the same thing and it's pointing to a bug in gcc:
[http://ubuntuforums.org/showpost.php?p=2565802&postcount=6](http://ubuntuforums.org/showpost.php?p=2565802&postcount=6)

---

### Post by LordVeovis on 2007-11-29
Thanks for replying.  I have previously seen that post and read it, and nearly everything else i could find.  It does have a similar problem on the subsequent link, but I do not know how that problem relates to this or how to fix it.  I am a little new to linux, so not sure how that info applies to me.

---

### Post by LordVeovis on 2007-12-11
Still not able to get ProjectM to install properly... are there and Debs of the current version and not .99 as that would require me to revert other things as well...

---

### Post by sheen on 2007-12-12
I have exactly the same issue on ubuntu 7.10 amd64.
I have ftgl-dev isntalled.

---

### Post by sheen on 2007-12-12
Solution found : [http://ubuntuforums.org/showthread.php?t=249818](http://ubuntuforums.org/showthread.php?t=249818)

Install those packages and it works (until my compiz crash in amarok but it's another problem ^^)

---

### Post by xtknight on 2008-02-29
Actual solution found: [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=403116](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=403116)

cmake .
Then

You have to edit these files.

libprojectM-1.01$ gedit CMakeFiles/projectM.dir/link.txt 
libprojectM-1.01$ gedit CMakeFiles/projectM.dir/relink.txt 

Replace -lftgl with -lftgl_pic

Continue "make".  Problem solved.  Final product untested though.

---

### Post by sofamensch on 2008-04-18
Cannot find these files in the newest SVN?

---

### Post by sofamensch on 2008-04-18
These files have moved. Here are there locations
/projectM-Trunk/src/projectM-engine/CMakeFiles/projectM.dir/relink.txt

I Can confirm it works fine with these bugfixes

---

