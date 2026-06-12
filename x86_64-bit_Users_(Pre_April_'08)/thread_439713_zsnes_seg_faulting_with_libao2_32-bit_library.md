---
title: "zsnes seg faulting with libao2 32-bit library"
date: 2007-05-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by dfreer on 2007-05-10
Hey everyone,

    I am trying to create a 32-bit package of zsnes v1.51, which can be compiled with libao2 support for better sound (MUCH better sound, IMO). I compiled several different versions of zsnes on a x86 system, first vanilla, then with libao2 support, then a release version, and finally a release version with libao2 support. I also grabbed v1.52 from svn and did the same thing. They all run fine on my x86 system, and libao2 works and sounds great. Here's an example of what I am talking about:
[LIST]
[*]zsnes1.51.vanilla
[*]zsnes1.51.release
[*]zsnes1.51.libao2
[*]zsnes1.51.libao2.release
[*]zsnes1.52.vanilla
[*]zsnes1.52.release
[*]zsnes1.52.libao2
[*]zsnes1.52.libao2.release
[/LIST]

    I then tried executing the binary on my x86_64 system. The vanilla and release versions work well, other than having scratchy sound. 1.51 with libao2 will produce this error:
```
Segmentation fault (core dumped)
```
1.52 will execute with libao2, but will only use the Simple DirectMedia Layer output driver, leaving no option to use libao2. So it sounds extremely bad, but runs.

My question is when it seg faults and dumps it core, is there a file I can check to see why it did that? And does anyone know of a way to run v1.51 in amd64 that the sound doesn't sound scratchy, either with libao2 or with SDL?

---

### Post by RAOF on 2007-05-11
You can **try** running it under gdb in order to debug it.  Once it's segfaulted, you can get a backtrace.

However, unless you've got some development knowledge, this won't help you much :(

---

### Post by dfreer on 2007-05-13
sorry for the long response time.
I've been talking to some developers over at the zsnes board, and it appears that although I installed the 32-bit package of libao2, the actual library /usr/lib32/libao.so.2 looks for plugins in /usr/lib/ao/plugins-2/ (I had to run the command *strings /usr/lib32/libao.so.2 | grep /* and it showed me there. So it appears that it is trying to use my 64-bit libao plugins which is why it is segfaulting. Now to find a fix!

---

### Post by dfreer on 2007-05-13
got it! thanks to 2 devs at zsnes forums, here's the fix!
[http://board.zsnes.com/phpBB2/viewtopic.php?t=10096](http://board.zsnes.com/phpBB2/viewtopic.php?t=10096)
the .debs can be found in my sig

---

