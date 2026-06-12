---
title: "libqt-mt.so.3: cannot open shared object file: No such file or directory"
date: 2009-03-03
forum: x86 64-bit Users
---

### Post by natialos on 2009-03-03
I'm trying to run flash4linux, but every time I do I get this error: 

[B]f4l: error while loading shared libraries: libqt-mt.so.3: cannot open shared object file: No such file or directory
[/B]

I've googled around and it seems like there is some problem with my qt3 being 32 bit and my computer being 64 bit. So how do I fix it?

I'm really a linux newbie, so if you would clearly spell out any instructions that you have, it would be much appreciated. :)

---

### Post by ibuclaw on 2009-03-03
For 64bit systems, there is [getlibs]("http://ubuntuforums.org/showthread.php?t=474790"), which finds and installs all 32bit dependencies for an application.

ie:
```
getlibs $(which flash4linux)
```

Regards
Iain

---

### Post by natialos on 2009-03-03
> **tinivole said:**
> For 64bit systems, there is [getlibs]("http://ubuntuforums.org/showthread.php?t=474790"), which finds and installs all 32bit dependencies for an application.

ie:
```
getlibs $(which flash4linux)
```

Regards
Iain

I get this:

```
Usage: getlibs /path/to/binary
       getlibs -l i386librarytoinstall.so
       getlibs -p i386packagename
       getlibs -w www.website.com/i386package.deb
       getlibs -i /home/natasha/i386package.deb
       See 'man getlibs' for more commands

```

which I take to mean that the command wasn't written out correctly. 

"getlibs -p  flash4linux" returns

"W: Unable to locate package flash4linux
E: No packages found
flash4linux was not found in your repositories
Make sure you have all repositories enabled and updated
No packages to install"

:/

---

### Post by ibuclaw on 2009-03-03
Pardon my ignorance, but how do you run flash4linux?

I just assumed that you type in 'flash4linux' in the console.

[EDIT]
is it **f4l** ?
If so, then it should be
```
getlibs $(which f4l)
```
instead.

Regards
Iain

---

### Post by natialos on 2009-03-03
ah, yes. that worked.

although now I'm getting:

Conflict in /usr/lib/kde3/plugins/styles/highcontrast.so:
  Plugin uses incompatible Qt library!
  expected build key "i686 Linux g++-4.* full-config", got "x86_64 Linux g++-4.* full-config".
Conflict in /usr/lib/kde3/plugins/styles/plastik.so:
  Plugin uses incompatible Qt library!
  expected build key "i686 Linux g++-4.* full-config", got "x86_64 Linux g++-4.* full-config".
Conflict in /usr/lib/kde3/plugins/styles/kthemestyle.so:
  Plugin uses incompatible Qt library!
  expected build key "i686 Linux g++-4.* full-config", got "x86_64 Linux g++-4.* full-config".
Conflict in /usr/lib/kde3/plugins/styles/highcolor.so:
  Plugin uses incompatible Qt library!
  expected build key "i686 Linux g++-4.* full-config", got "x86_64 Linux g++-4.* full-config".
Conflict in /usr/lib/kde3/plugins/styles/keramik.so:
  Plugin uses incompatible Qt library!
  expected build key "i686 Linux g++-4.* full-config", got "x86_64 Linux g++-4.* full-config".
Conflict in /usr/lib/kde3/plugins/styles/light.so:
  Plugin uses incompatible Qt library!
  expected build key "i686 Linux g++-4.* full-config", got "x86_64 Linux g++-4.* full-config".
Segmentation fault


I guess that's because I'm using qt4 instead of qt3 :[

but I have other programs that require qt4. Is there any way to satisfy this?

---

