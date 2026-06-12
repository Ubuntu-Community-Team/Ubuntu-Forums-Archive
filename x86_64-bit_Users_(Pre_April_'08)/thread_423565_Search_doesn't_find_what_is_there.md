---
title: "Search doesn't find what is there"
date: 2007-04-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by jsym on 2007-04-26
While suffering through messages like "libstdc++.so.5: cannot open shared object file: No such file or directory" due to changes in where files are put in Feisty I came across a strange error: there are certain files which Search will not find even though they are there.  libstdc++.so.5 is one.  libX11.so.6 is another.  On further inspection when I choose "File system" rather than home Search ignores my home directory and all its contents when it should be searching the *entire* file system.  Things didn't used to be this way.

I imagine that this is some sort of path issue, but what and how to fix it?


--------------------------------
btw - apparently the solution to the "cannot open shared object file" problem is to band-aid it with a symbolic link:
```
ln -s /usr/local/lib/libstdc++.so.5 /usr/lib/libstdc++.so.5
```
I haven't tried yet though.

---

### Post by jsym on 2007-04-26
Two things.

First, apparently the reason that **Search for files...** was not finding what it was supposed to was that it uses a program called **locate** to find things and this program relies on a database of all the files on a system to pull the search off.  I updated the database and everything was fine.

```
$ locate -u
```

Not sure why the database wasn't updating itself or at least not doing so as often as demanded.  Perhaps this will be an ongoing problem for me?


Second, creating a symbolic link didn't help with my "cannot open shared object file" problem since the file were already where they were supposed to be.  I think it might be a problem with a 32-bit program not being able to work with 64-bit LSB executables.  I'll look around some and if I can't find anything I'll post to the forum.

---

