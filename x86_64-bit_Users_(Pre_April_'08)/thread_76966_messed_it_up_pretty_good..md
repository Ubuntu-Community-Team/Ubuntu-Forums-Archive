---
title: "messed it up pretty good."
date: 2005-10-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by sas13 on 2005-10-16
can't run any part of openoffice2.

this is what happens when I try:

```
$ ooffice2

/usr/lib/openoffice2/program/javaldx: error while loading shared libraries: libstdc++.so.6: cannot open shared object file: No such file or directory
/usr/lib/openoffice2/program/pagein: error while loading shared libraries: libstdc++.so.6: cannot open shared object file: No such file or directory
/usr/lib/openoffice2/program/soffice: line 224: /usr/lib/openoffice2/program/soffice.bin: No such file or directory
```


I'm pretty sure I messed up however it is that you point ubuntu towards the 32-bit lib's - I was trying to get skype to work and was playing with that kind of thing. (but I don't really have a clue...)

problem is I'm a newb and I don't really know what I'm doing.

running breezy on an AMD64 Turion compaq laptop

system is up-to-date and most everything else works.

---

### Post by sas13 on 2005-10-16
oh, yeah - forgot to say I have tried a complete removal and reinstall of oo2 and all it's supporting libraries to try to fix it first (old windoze habits die hard...)

---

### Post by Rounan on 2005-10-16
It does look like you've just misplaced some libraries.
First, do:
sudo updatedb

That will rebuild the search database for files on your computer. Then, do:
locate <filename>

where filename is what the program can't find. On my system, for "locate libstdc++", this turns up files in /usr/lib and /usr/lib32:

```
~$ ls -l /usr/lib/libstdc++.so*
lrwxrwxrwx  1 root root      18 2005-10-15 15:14 /usr/lib/libstdc++.so.5 -> libstdc++.so.5.0.7
-rw-r--r--  1 root root  829864 2005-09-16 07:22 /usr/lib/libstdc++.so.5.0.7
lrwxrwxrwx  1 root root      18 2005-10-15 10:28 /usr/lib/libstdc++.so.6 -> libstdc++.so.6.0.5
-rw-r--r--  1 root root 1005216 2005-10-01 11:01 /usr/lib/libstdc++.so.6.0.5
$ ls -l /usr/lib32/libstdc++.so*
lrwxrwxrwx  1 root root     18 2005-10-15 14:35 /usr/lib32/libstdc++.so.5 -> libstdc++.so.5.0.7
-rw-r--r--  1 root root 737496 2005-08-15 20:06 /usr/lib32/libstdc++.so.5.0.7
lrwxrwxrwx  1 root root     18 2005-10-15 14:35 /usr/lib32/libstdc++.so.6 -> libstdc++.so.6.0.5
-rw-r--r--  1 root root 911348 2005-10-01 11:01 /usr/lib32/libstdc++.so.6.0.5
```

Probably what's happened to you is that the .6.0.5 and .5.0.7 files are still there, but the .6 and .5 symlinks are gone. Check out the link man page, with "man ln" to see how to replace them.

For soffice.bin, I can't find any symlinks on my machine, only 2 tiny scripts called soffice.bin, and a soffice.bin.real that probably contains the actual binary. If you removed the soffice.bin.real, you'll need to uninstall and reinstall openoffice (though you said you did this already... strange...). If it's just the script missing, create a text file called soffice.bin (NO .txt extension), put it in the /usr/lib/openoffice2/program directory, make it executable with "chmod a+x <filename>" and give it these contents:```


#! /bin/sh

GTK_PATH=/usr/lib32/gtk-2.0 LD_PRELOAD=/usr/lib32/libpangohack.so.0.0 exec "$0".real "$@"
```

That's about as much as I can think of.

--Rounan

---

### Post by sas13 on 2005-10-17
Thanks for the rpely, but I got impatient and tried a brute force solution (that seems to be working) before I read it.

this is the gist of my solution, but I may be forgetting something-

basically I removed (rm -r) all the lib32 directories (/lib32/ and /usr/lib32)

I then deleted /etc/ld.so.cache and rebuilt it with ldconfig

then I reinstalled the 32 bit libraries with synaptic.

openoffice2 is now working, but still no luck with skype.

---

